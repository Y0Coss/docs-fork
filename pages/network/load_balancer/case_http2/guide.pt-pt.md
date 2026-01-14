---
title: 'Como configurar o protocolo HTTP/2 no Load Balancer OVHcloud'
excerpt: 'Configuração do protocolo HTTP/2 no Load Balancer OVHcloud'
updated: 2026-01-14
---

> [!primary]
> **Nota sobre o suporte nativo ao protocolo HTTP/2**
>
> A partir de junho de 2025, os frontends HTTP e TLS dos serviços Load Balancer da OVHcloud suportam nativamente o protocolo HTTP/2.
>
> Este guia continua, no entanto, aplicável aos frontends TCP, que podem ser úteis para aplicações que necessitam de baixa latência e altas performances.
>
> Para ativar o protocolo HTTP/2 nos frontends HTTP e TLS existentes, terá de efetuar o seguinte chamada de atualização através da API, onde **serviceName** é o nome interno do seu Load Balancer.

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>

## Objetivo

Este guia tem dois objetivos principais:

- Ajudá-lo a compreender as diferenças entre os frontends TCP, HTTP e TLS num Load Balancer da OVHcloud, permitindo-lhe assim determinar se um frontend TCP é a escolha mais adequada para as suas necessidades específicas de aplicações, especialmente na gestão do tráfego HTTP/2.
- Se for considerado desejável utilizar um frontend TCP, fornecer depois instruções passo a passo sobre como o configurar para equilibrar eficazmente o tráfego HTTP/2 nos seus servidores backend.

## Pré-requisitos

Terá necessidade de:

- Um serviço [Load Balancer OVHcloud](/links/network/load-balancer);
- Um frontend TCP no seu Load Balancer;
- Um cluster de servidores (ferme) TCP com pelo menos um servidor adicionado;
- Servidores backend configurados para suportar e responder com HTTP/2;
- Acesso à [API OVHcloud](/links/api).

## Instruções

### Porquê utilizar HTTP/2?

O HTTP/2 traz muitas vantagens para melhorar o desempenho e a eficiência das suas aplicações:

- *Tempos de carregamento mais rápidos* graças ao multiplexagem, que permite enviar várias requisições em paralelo na mesma ligação.
- *Latência reduzida* ao limitar as trocas entre o cliente e o servidor.
- *Desempenho de rede otimizado* graças à compressão dos cabeçalhos.

### Diferenças entre os frontends HTTP/2 e TCP

Um frontend TCP opera na Camada 4 (a camada de transporte) do modelo OSI. Quando configura um frontend TCP, o Load Balancer estabelece uma ligação TCP entre o cliente e um servidor backend. Isto significa que o Load Balancer não inspeciona nem compreende os dados HTTP/2 dentro do fluxo TCP. Por isso, os frontends TCP oferecem altas performances graças ao processamento mínimo dos dados.

No entanto, como não compreende o protocolo de aplicação, não pode realizar otimizações avançadas específicas ao HTTP, tais como o encaminhamento baseado no conteúdo ou a manipulação dos cabeçalhos HTTP.

Os frontends HTTP e TLS, por sua vez, operam na Camada 7 (a camada de aplicação). Quando um cliente se liga a um frontend compatível com HTTP/2, o Load Balancer decodifica completamente as tramas HTTP/2 antes de estabelecer uma ligação com um servidor backend.

Ao interpretar o protocolo de aplicação, um frontend compatível com HTTP/2 pode fornecer muitas funcionalidades avançadas. Estas incluem a terminação SSL/TLS (desencarregando a encriptação/desencriptação dos servidores backend), o encaminhamento baseado no conteúdo (por exemplo, encaminhar requisições para diferentes ferros de backend com base no caminho da URL ou nos cabeçalhos), a modificação das requisições/respostas e o multiplexagem HTTP/2.

**Deverá utilizar um frontend TCP quando:**

- Precisar equilibrar a carga de outros serviços não-HTTP (por exemplo, bases de dados, aplicações TCP personalizadas, SSH);
- Exigir desempenho máximo e latência mínima;
- Os seus servidores backend já gerem a terminação SSL/TLS;
- Não necessitar de funcionalidades HTTP avançadas específicas, tais como encaminhamento baseado no conteúdo, manipulação dos cabeçalhos HTTP ou otimizações ao nível do protocolo HTTP/2.

**Deverá utilizar um frontend compatível com HTTP/2 quando:**

- Tratar principalmente de tráfego web (HTTP/HTTPS);
- Quiser tirar partido das vantagens de desempenho do HTTP/2 entre o cliente e o Load Balancer;
- Quiser delegar a terminação SSL/TLS dos seus servidores backend ao seu Load Balancer;
- Precisar de uma lógica de encaminhamento avançada baseada nos cabeçalhos HTTP, URLs ou outros atributos da camada de aplicação;
- Quiser otimizar a experiência do lado do cliente tirando partido das funcionalidades HTTP/2.

*Se optar por utilizar um frontend TCP, siga os passos seguintes deste guia para o configurar para utilização HTTP/2*.

### Configurar um frontend TCP para HTTP/2

> [!warning]
>
> A ordem de criação dos elementos é importante. Os encaminhamentos devem ser configurados antes de lhes serem atribuídas regras.
> 

#### Adicionar um encaminhamento

Vamos adicionar um encaminhamento ao serviço.

##### Através da API

> [!faq]
>
> Serviço:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/tcp/route
>> >
>>
>
> Parâmetros:
>
>> > **serviceName** *
>> >
>> >> `<ID do Load Balancer>`
>> >
>> > **action**
>> >
>> >> **type**
>> >> >
>> >> > `"farm"`
>> >>
>> >> **target**
>> >> >
>> >> > `<ID da Farm TCP que deve poder gerir o HTTP/2>`
>> >
>> > **frontendId**
>> >
>> >> `<ID do Frontend TCP 443>`
>

#### Adicionar uma regra

Agora vamos adicionar uma regra à nossa route.

##### Através da API

> [!faq]
>
> Serviço:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/tcp/route/{routeId}/rule
>> >
>>
>
> Parâmetros:
>
>> > **serviceName** \
>> >
>> >> `<ID do Load Balancer>`
>> >
>> > **routeId**
>> >
>> >> `<ID da route criada acima>`
>> >
>> > **field**
>> >
>> >> `"protocol"`
>> >
>> > **match**
>> >
>> >> `"is"`
>> >
>> > **pattern**
>> >
>> >> `"http/2.0"`
>

#### Aplicar as modificações

As modificações feitas ao Load Balancer OVHcloud devem ser  *aplicadas explicitamente* em cada uma das zonas configuradas para o serviço. Caso contrário, elas não serão visíveis para os seus visitantes. Isto permite efetuar alterações de configuração complexas de uma só vez.

Se tem várias zonas, deve aplicar a mesma configuração a cada uma delas.

##### Através da API

Atualizar uma zona:

> [!faq]
>
> Serviço:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>> >
>>
>
> Parâmetros:
>
>> > **serviceName** *
>> >
>> >> `<ID do Load Balancer>`
>> >
>> > **zona**
>> >
>> >> `<zona na qual aplicar a configuração>`
>

#### Validar

Depois destas etapas, já dispõe de um serviço de repartição de carga funcional para os seus servidores HTTP/2. Agora pode validar o estado do serviço solicitando-o ao Load Balancer OVHcloud e verificando a versão da resposta:

```bash
curl -I --http2 https://www.ovh.com/
HTTP/2 200
```

## Quer saber mais?

Fale com a nossa [comunidade de utilizadores](/links/community).