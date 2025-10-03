---
title: "FAQ sobre os nomes de domínio & DNS"
excerpt: "Encontre as principais questões colocadas sobre os nomes de domínio, os servidores DNS e as zonas DNS"
updated: 2025-10-02
---

<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>

**Clique na perguntas abaixo para exibir as explicações.**

## Subscrição de um nome de domínio

/// details | Como posso subscrever um nome de domínio na OVHcloud ?

Siga estas etapas :

1. Acesse nosso site [OVHcloud](/links/website).
2. Na página exibida e no campo apropriado, digite o nome de domínio que deseja reservar (por exemplo: `dominio.tld`), em seguida, clique no botão `Pesquisar`{.action}.
3. Na nova página exibida, nossa interface informará se o nome de domínio escolhido está disponível para compra ou não. Se já estiver reservado com a sintaxe que você digitou, modifique-o e inicie uma nova verificação de disponibilidade.
4. Uma vez que você tenha encontrado um nome de domínio disponível, clique no botão `Adquirir`{.action}, depois no botão `Continuar a encomendar`{.action} na coluna à direita.
5. Selecione as opções ou serviços adicionais aos quais deseja subscrever-se juntamente com seu nome de domínio, depois clique em `Continuar`{.action} até que o processo de compra solicite que você faça login ou crie uma conta cliente OVHcloud.
6. Assim que você estiver autenticado com sua conta cliente OVHcloud, poderá personalizar as informações dos contatos (proprietário/titular, administrador, técnico) para seu nome de domínio. Em seguida, clique no botão `Continuar`{.action} para acessar o resumo de sua compra.
7. Na página `Resumo da sua compra` e, se necessário, poderá modificar a configuração DNS que será aplicada ao seu nome de domínio clicando no link intitulado `Modificar a configuração`{.action}. Assim que suas modificações forem concluídas, clique no botão `Pagar`{.action} para acessar a última etapa de sua compra.

Pague sua compra para iniciar a reserva de seu nome de domínio, bem como a instalação dos serviços e opções adicionais aos quais você se inscreveu.

Alguns instantes depois, você receberá um e-mail de confirmação para sua compra.
Você poderá, em seguida, administrar seu nome de domínio fazendo login no seu [Área de Cliente OVHcloud](/links/manager).

Não hesite em criar um ticket de suporte a partir do [centro de ajuda](https://help.ovhcloud.com/csm?id=csm_get_help) se necessário.

///

/// details | Como posso comprar um nome de domínio no mercado secundário ?

A compra de um nome de domínio no mercado secundário é feita da mesma forma que a subscrição de um nome de domínio.

Siga estas etapas :

1. Acesse nosso site [OVHcloud](/links/website).
2. Na página exibida e no campo apropriado, digite o nome de domínio que deseja reservar (por exemplo: `dominio.tld`), em seguida, clique no botão `Pesquisar`{.action}.
3. Na nova página exibida, nossa interface informará se o nome de domínio escolhido está disponível para compra ou não. Se já estiver reservado com a sintaxe que você digitou, modifique-o e inicie uma nova verificação de disponibilidade.
4. Uma vez que você tenha encontrado um nome de domínio disponível, clique no botão `Comprar`{.action}, depois no botão `Continuar a compra`{.action} na coluna à direita.
5. Selecione as opções ou serviços adicionais aos quais deseja subscrever-se juntamente com seu nome de domínio, depois clique em `Avançar`{.action} até que o processo de compra solicite que você faça login ou crie uma conta cliente OVHcloud.
6. Assim que você estiver autenticado com sua conta cliente OVHcloud, poderá personalizar as informações dos contatos (proprietário/titular, administrador, técnico) para seu nome de domínio. Em seguida, clique no botão `Continuar`{.action} para acessar o resumo de sua compra.
7. Na página `Resumo da sua compra` e, se necessário, poderá modificar a configuração DNS que será aplicada ao seu nome de domínio clicando no link intitulado `Modificar a configuração`{.action}. Assim que suas modificações forem concluídas, clique no botão `Pagar`{.action} para acessar a última etapa de sua compra.

Pague sua compra para iniciar a reserva de seu nome de domínio, bem como a instalação dos serviços e opções adicionais aos quais você se inscreveu.

Alguns instantes depois, você receberá um e-mail de confirmação para sua compra.
Você poderá, em seguida, administrar seu nome de domínio fazendo login no seu [Área de Cliente OVHcloud](/links/manager).

Não hesite em criar um ticket de suporte a partir do [centro de ajuda](https://help.ovhcloud.com/csm?id=csm_get_help) se necessário.

///

## Administração de um nome de domínio

/// details | Como saber se meu nome de domínio está registrado na OVHcloud ?

Para isso, você pode realizar uma consulta [WHOIS](/links/web/domains-whois) para saber onde seu nome de domínio está registrado e verificar se você está declarado como titular do nome de domínio.

Cada escritório de registro (como a OVHcloud) tem a possibilidade de escolher como exibir as informações relativas a um nome de domínio no WHOIS.

Após realizar a consulta WHOIS, procure no resultado pelo menos uma das seguintes linhas :

- Domain Name: ovhcloud.com
- Registrar WHOIS Server: whois.ovh.com
- Registrar URL: https://ovh.com
- Registrar: OVH sas

Se você observar pelo menos uma dessas linhas no resultado, seu nome de domínio está realmente registrado na OVHcloud.

Caso contrário, seu nome de domínio está registrado em outro escritório de registro. Procure então as linhas relativas ao `Registrar` para identificar o escritório de registro onde seu nome de domínio está registrado.

///

/// details | Como saber a data de expiração de um nome de domínio ?

A solução mais rápida é realizar uma consulta [WHOIS](/links/web/domains-whois) no nome de domínio. Após realizar a consulta, procure no resultado a linha correspondente à data de expiração (por exemplo: `Expiry Date: 2025-09-22T08:00:00Z`, `Registry Expiry Date: 2025-09-22T08:00:00Z`, etc.).

Se seu nome de domínio estiver registrado na OVHcloud, você também poderá seguir estas etapas :

1. Aceda à [Área de Cliente OVHcloud](/links/manager)}.
2. Clique no seu nome no canto superior direito e escolha `As minhas ofertas e serviços`{.action}.
3. No quadro que aparece, procure a linha correspondente ao seu nome de domínio e localize a data presente na coluna `Data de entrada em vigor`. Esta data corresponde à data de expiração do seu nome de domínio.

///

/// details | Como alterar a data anual de expiração de um nome de domínio ?

A data anual de expiração de um nome de domínio (por exemplo: 24 de setembro) é pré-determinada com base na data de registro (criação) do nome de domínio.

Geralmente, a data anual de expiração de um nome de domínio é a mesma da data em que você o registrou.

Portanto, não é possível alterar a data anual de expiração de um nome de domínio.

///

<br>

/// details | Como corrigir um erro de digitação no meu nome de domínio ?

Assim que um nome de domínio é adquirido, ele é registrado com base nos caracteres que você definiu ao fazer a compra. O registro é feito junto ao registro da extensão do seu nome de domínio (por exemplo: o registro dos *.com*) e são aplicadas taxas de reserva do lado do registrador (como a OVHcloud).

Um nome de domínio é um endereço único na Internet, por exemplo: `ovhcloud.com`.
Qualquer alteração nesse nome, seja um caractere ou uma extensão (.com, .fr, .net, etc.), torna-o um nome de domínio completamente diferente.

Portanto, se você cometeu um erro de digitação ao fazer a compra, ele não poderá ser modificado ou corrigido. Você deverá adquirir um novo nome de domínio independentemente do anterior (desde que a nova ortografia desejada não esteja já reservada por outra pessoa).

Os nomes de domínio são considerados produtos personalizados, pois são registrados especificamente para um titular e bloqueados para outros desde a compra. Por isso, uma vez registrados, eles não podem ser reembolsados.

///

/// details | Como modificar um nome de domínio já adquirido ?

Assim que um nome de domínio é adquirido, ele é registrado com base nos caracteres que você definiu ao fazer a compra. O registro é feito junto ao registro da extensão do seu nome de domínio (por exemplo: o registro dos *.com*) e são aplicadas taxas de reserva do lado do registrador (como a OVHcloud).

Um nome de domínio é um endereço único na Internet, por exemplo: `ovhcloud.com`.
Qualquer alteração nesse nome, seja um caractere ou uma extensão (.com, .fr, .net, etc.), torna-o um nome de domínio completamente diferente.

Portanto, se você cometeu um erro de digitação ao fazer a compra, ele não poderá ser modificado ou corrigido. Você deverá adquirir um novo nome de domínio independentemente do anterior (desde que a nova ortografia desejada não esteja já reservada por outra pessoa).

Os nomes de domínio são considerados produtos personalizados, pois são registrados especificamente para um titular e bloqueados para outros desde a compra. Por isso, uma vez registrados, eles não podem ser reembolsados.

///

/// details | Como excluir um nome de domínio ?

Siga estas etapas :

1. Aceda à [Área de Cliente OVHcloud](/links/manager)}.
2. Clique no seu nome no canto superior direito e escolha `As minhas ofertas e serviços`{.action}.
3. No quadro que aparece, procure a linha correspondente ao seu nome de domínio, clique no botão `...`{.action} à direita, depois em `Rescindir o meu serviço`{.action}.
4. Na página exibida, preencha o questionário e clique em `Validar`{.action} no final.

Seu nome de domínio será então suspenso na data de expiração, e, a partir dessa data, será excluído **permanentemente** em um prazo máximo de 60 dias. Esse prazo é definido pela **I**nternet **C**orporation for **A**ssigned **N**ames and **N**umbers (**ICANN**) para que um nome de domínio seja totalmente excluído e novamente disponível para registro por outro titular.

> [!primary]
>
> Uma vez solicitada a rescisão, você pode acelerar a exclusão criando um ticket de suporte a partir do [centro de ajuda](https://help.ovhcloud.com/csm?id=csm_get_help). Documentos comprobatórios deverão ser fornecidos para acelerar essa exclusão.

> [!success]
>
> Encontre todos os detalhes no nosso guia « [Como cancelar os meus serviços OVHcloud](/pages/account_and_service_management/managing_billing_payments_and_services/how_to_cancel_services) ».

///

/// details | Recebi um e-mail sobre a validação das informações do titular associadas ao meu nome de domínio, o que fazer ?

Primeiramente, se você tiver dúvidas sobre a legitimidade do e-mail recebido, consulte nosso guia « [Atenção às tentativas de fraude: como reconhecer os emails fraudulentos e de phishing](/pages/account_and_service_management/account_information/phishing_care) ».

Conforme uma diretiva da **I**nternet **C**orporation for **A**ssigned **N**ames and **N**umbers (**ICANN**) de 01/09/2014, os registradores (por exemplo: OVHcloud) são obrigados a verificar a validade dos dados dos titulares/proprietários de nomes de domínio. A OVHcloud envia então um e-mail aos titulares/proprietários do nome de domínio registrado para o endereço de e-mail de contato declarado na OVHcloud.

Você receberá esse e-mail quando realizar uma das seguintes ações :

- Registro de um novo nome de domínio.
- Transferência de um nome de domínio.
- Alteração das informações associadas ao seu nome de domínio.

Esse e-mail contém um link que permite verificar rapidamente suas informações como proprietário/titular legal do nome de domínio.

Atenção: Essa verificação deve ser feita em um prazo de 15 dias. Após esse prazo, o nome de domínio será suspenso tecnicamente. Ele permanecerá sob seu nome contratuamente, mas não será mais acessível na Internet. Uma mensagem de erro será exibida para os visitantes do seu site.

Você pode receber os seguintes e-mails nos primeiros 15 dias :

- **Dia 0** : Imediatamente após adquirir o nome de domínio ou alterar suas informações, você (ou a pessoa registrada como proprietário/titular do nome de domínio) receberá o primeiro e-mail com um link de verificação.
- **Dias 4, 9 e 13 (e-mails de lembrete)** : Se você ainda não verificou o nome de domínio, você receberá o e-mail novamente.
- **Dia 14** : Se você ainda não verificou o nome de domínio, o e-mail é enviado novamente. Além disso, um e-mail também é enviado para o endereço de e-mail do administrador/titular do nome de domínio para informá-lo de que as informações dele não foram confirmadas.
- **Dia 15** : Se o proprietário/titular do nome de domínio ainda não respondeu, enviamos um e-mail para o administrador do nome de domínio para informá-lo da situação e da desativação do nome de domínio.

Após esses 15 dias, o sistema envia e-mails adicionais (até 9 e-mails) antes de excluir seu nome de domínio. Essa exclusão será realizada após 60 dias a partir do dia 0.

> [!warning]
>
> Dependendo da extensão do nome de domínio (por exemplo: *.com*, *.net*, etc.), alguns dos prazos mencionados acima podem variar. Recomendamos fortemente que você verifique, junto ao registro da extensão do seu nome de domínio, o processo de verificação do controle dos contatos.

///

/// details | Não recebi o e-mail de validação das informações do titular associado ao meu nome de domínio e ele está suspenso, o que fazer ?

Se você não recebeu o e-mail de validação do proprietário do seu nome de domínio, verifique os seguintes pontos :

1. O endereço de e-mail declarado para o titular do nome de domínio é válido e funcional.
2. O e-mail de validação não está na pasta de spam.

Após verificar e confirmar os dois pontos acima, se você ainda não conseguir recuperar o e-mail de validação do titular, convidamos você a abrir um ticket de suporte a partir do [centro de ajuda](https://help.ovhcloud.com/csm?id=csm_get_help) para solicitar o reenvio desse e-mail.

///

/// details | O que é um nome de domínio no formato IDN ?

Originalmente, os nomes de domínio podiam conter apenas caracteres **ASCII** específicos (incluindo as 26 letras do alfabeto latino). Um **I**nternationalized **D**omain **N**ame (**IDN**) permite, entre outras coisas, o uso de caracteres especiais ou acentuados, ou até mesmo outros alfabetos (como o *cirílico*).

Na OVHcloud, é perfeitamente possível comprar IDNs e utilizá-los como nomes de domínio completos com os nossos outros serviços (como hospedagem web, zona DNS, etc.<sup>1</sup>).

Uma vez adquiridos, os IDNs aparecem no seu [Área de Cliente OVHcloud](/links/manager) no formato **xn--**.

Mesmo que seu domínio apareça em [notação internacionalizada (IDN)](https://en.wikipedia.org/wiki/Internationalized_domain_name) no seu [Área de Cliente OVHcloud](/links/manager), ele funcionará e aparecerá de forma totalmente normal em outros lugares. O endereço do seu site será exibido como você solicitou. Seus endereços de e-mail também serão exibidos como você deseja para seus correspondentes.

> [!alert]
>
> <sup>1</sup> : Não é recomendado utilizar um endereço de e-mail com um nome de domínio IDN a partir de um cliente de e-mail (Outlook, Mail do macOS, etc.). De fato, alguns clientes de e-mail ainda não interpretam nomes de domínio com caracteres acentuados, o que bloqueia a transmissão dos e-mails. Quando um remetente lhe envia um e-mail, ele recebe então uma mensagem automática indicando que seu endereço de e-mail não existe.
>
> **Recomenda-se reservar, em complemento ao seu nome de domínio com caracteres acentuados, o mesmo nome de domínio sem esses acentos, para evitar qualquer incompatibilidade nos intercâmbios de e-mails.**

///

/// details | Como corrigir um nome de domínio no formato IDN ?

Assim como os nomes de domínio "clássicos", assim que um nome de domínio ou um IDN é adquirido, ele é registrado com base nos caracteres que você definiu ao fazer a compra.

Portanto, se você cometeu um erro de digitação ao fazer a compra, ele não poderá ser corrigido. Você deverá adquirir um novo nome de domínio independentemente do anterior (desde que a nova ortografia desejada não esteja já reservada por outra pessoa).

///

/// details | Como renovar apenas um nome de domínio presente em um pack Alldom ?

Para isso, você deve estar, no mínimo, declarado como [contato "faturação"](/pages/account_and_service_management/account_information/managing_contacts) do nome de domínio em questão. Você deverá, em seguida, modificar o modo de renovação do nome de domínio para **renovação automática**.

Para isso, siga estas etapas :

1. Aceda à [Área de Cliente OVHcloud](/links/manager)}.
2. Clique no seu nome no canto superior direito e escolha `As minhas ofertas e serviços`{.action}.
3. No quadro que aparece e à direita do nome de domínio em questão, clique no botão `...`{.action} na coluna `Ações`, depois em `Configurar a renovação`{.action}. Você poderá, em seguida, configurar a renovação desse nome de domínio em **renovação automática**.

> [!primary]
>
> Se você possui uma oferta antiga de hospedagem web que inclui um nome de domínio gratuito e se você modificar essa oferta de hospedagem, isso pode, em alguns casos, cancelar a gratuidade do nome de domínio.
>
> Em caso de dúvida, convidamos você a abrir um ticket de suporte a partir do [centro de ajuda](https://help.ovhcloud.com/csm?id=csm_get_help) especificando o nome de domínio e a hospedagem web em questão.

> [!success]
>
> Encontre todos os detalhes no nosso guia « [Como renovar os meus serviços OVHcloud](/pages/account_and_service_management/managing_billing_payments_and_services/how_to_use_automatic_renewal) ».

///

## Transferência de um nome de domínio

/// details | Meu nome de domínio é transferível após uma mudança de proprietário ?

A **I**nternet **C**orporation for **A**ssigned **N**ames and **N**umbers (**ICANN**) implementou medidas de segurança para prevenir transferências ou mudanças de proprietários não autorizadas ou abusivas de nomes de domínio.

A ICANN definiu, entre outras coisas, um prazo incompressível de **60** dias entre cada operação que pode ocorrer em um nome de domínio (criação, mudança de proprietário, transferência).

As regras definidas pela ICANN devem obrigatoriamente ser respeitadas pelos registradores (como a OVHcloud).

Você não terá outra escolha senão esperar até o final do prazo de 60 dias para poder transferir seu nome de domínio após ter mudado seu proprietário.

///

/// details | Meu nome de domínio está bloqueado contra a transferência por 60 dias, o que fazer ?

A **I**nternet **C**orporation for **A**ssigned **N**ames and **N**umbers (**ICANN**) implementou medidas de segurança para prevenir transferências ou mudanças de proprietários não autorizadas ou abusivas de nomes de domínio.

A ICANN definiu, entre outras coisas, um prazo incompressível de **60** dias entre cada operação que pode ocorrer em um nome de domínio (criação, mudança de proprietário, transferência).

As regras definidas pela ICANN devem obrigatoriamente ser respeitadas pelos registradores (como a OVHcloud).

Você não terá outra escolha senão esperar até o final do prazo de 60 dias para realizar uma nova operação (mudança de proprietário ou transferência) em seu nome de domínio.

///

/// details | Não consigo encontrar meu nome de domínio no meu espaço cliente, o que fazer ?

Primeiramente, realize uma consulta [WHOIS](/links/web/domains-whois) para saber onde seu nome de domínio está registrado e verificar se você está declarado como titular do nome de domínio.

Caso n°1.A - Seu nome de domínio está registrado na OVHcloud e você está declarado como titular do nome de domínio :

Realize uma [procedimento de recuperação de contatos](/links/transversal/procedure-change-contact) para que seu nome de domínio seja totalmente gerenciado no seu [Área de Cliente OVHcloud](/links/manager). Assim, você não precisará mais contatar a pessoa que gerenciava anteriormente seu nome de domínio.

Caso n°1.B - Seu nome de domínio está registrado na OVHcloud e você não está declarado como titular do nome de domínio :

Conforme a **G**eneral **D**ata **P**rotection **R**egulation (**GDPR**), a OVHcloud não poderá fornecer informações relativas à pessoa ou à organização que gerencia o nome de domínio na OVHcloud.

No entanto, você pode tentar contatar a pessoa ou organização que o gerencia seguindo as instruções de [este formulário](/links/web/contact-domain-owner).

Caso n°2 - Seu nome de domínio não está registrado na OVHcloud :

Entre em contato diretamente com o registrador (indicado nas linhas que começam com o termo `Registrar`) do seu nome de domínio para continuar suas pesquisas. De fato, se o nome de domínio não estiver registrado na OVHcloud, não seremos capazes de acompanhá-lo nesse assunto.

///

/// details | Não consigo contatar a pessoa que gerencia meu nome de domínio, o que fazer ?

Primeiramente, realize uma consulta [WHOIS](/links/web/domains-whois) para verificar se você está declarado como titular do nome de domínio.

Caso n°1 - Você está declarado como titular do nome de domínio :

Realize uma [procedimento de recuperação de contatos](/links/transversal/procedure-change-contact) para que seu nome de domínio seja totalmente gerenciado no seu [Área de Cliente OVHcloud](/links/manager). Assim, você não precisará mais contatar a pessoa que gerenciava anteriormente seu nome de domínio.

Caso n°2 - Você não está declarado como titular do nome de domínio :

Conforme a **G**eneral **D**ata **P**rotection **R**egulation (**GDPR**), a OVHcloud não poderá fornecer informações relativas à pessoa ou à organização que gerencia o nome de domínio na OVHcloud.

No entanto, você pode tentar contatar a pessoa ou organização que o gerencia seguindo as instruções de [este formulário](/links/web/contact-domain-owner).

///

/// details | Posso vender meu nome de domínio ?

Atualmente, a OVHcloud não oferece suporte diretamente ao processo de venda de nomes de domínio já registrados. Não oferecemos esse tipo de serviço.

No entanto, se você deseja colocar seu nome de domínio à venda em um mercado secundário, entre em contato com um dos nossos parceiros a seguir :

- [Afternic](https://www.afternic.com).
- [Sedo](https://sedo.com).

Se você deseja vender seu nome de domínio, pode adicioná-lo a essas plataformas. Uma vez adicionado, os fornecedores autorizados oferecerão seu nome de domínio ao preço que você definir em uma das plataformas acima.

///

## Zona DNS

> [!primary]
>
> A modificação de uma zona DNS é uma operação delicada e pode causar interrupções nos serviços associados ao seu nome de domínio (hospedagem web, e-mail, etc.). Em caso de dúvida, não hesite em contatar um [provedor especializado](/links/partner)

/// details | O que é uma zona DNS ?

A zona DNS de um nome de domínio contém uma configuração aplicável a este último. Ela é composta por informações técnicas, chamadas *registros DNS*. A zona DNS funciona como um centro de encaminhamento, direcionando o tráfego para os serviços corretos associados ao domínio.

Você pode, por exemplo, especificar :

- O endereço IP (registros DNS do tipo *A* e *AAAA*) da sua hospedagem web para exibir seu site com seu nome de domínio.
- Os servidores de e-mail (registros DNS do tipo *MX*) para os quais seu nome de domínio deve redirecionar os e-mails que recebe.
- Informações relacionadas à segurança / autenticação dos seus serviços (hospedagem web, servidor web, servidor de e-mail, etc.) associados ao seu nome de domínio (registros DNS do tipo *SPF*, *DKIM*, *DMARC*, etc.).

Uma zona DNS é hospedada / registrada em **servidores DNS**. Esses **servidores DNS** devem ser declarados junto ao registrador do nome de domínio para utilizar a zona DNS que eles hospedam.

> [!success]
>
> Encontre todos os detalhes no nosso guia « [Saber tudo sobre a zona DNS](/pages/web_cloud/domains/dns_zone_general_information) ».

///

