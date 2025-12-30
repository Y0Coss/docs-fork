---
title: "Zimbra Pro - Configurar a conta de correio eletrónico através do ActiveSync no Outlook clássico para Windows"
excerpt: "Descubra como configurar o seu endereço de correio eletrónico Zimbra Pro no Outlook para Windows através do protocolo ActiveSync"
updated: 2025-12-17
---

<style>
details>summary {
    color:rgb(255,165,0) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
.w-600 {
  max-width:600px !important;
}
.h-500 {
  max-width:500px !important;
}
</style>

## Objetivo

As contas Zimbra Pro podem ser configuradas no Windows utilizando o protocolo ActiveSync, permitindo configurar todas as funcionalidades colaborativas do seu endereço de correio eletrónico de uma só vez. A aplicação Outlook para Windows permite aceder ao seu endereço de correio eletrónico Zimbra Pro através do protocolo ActiveSync.

**Descubra como configurar o seu endereço de correio eletrónico Zimbra Pro no Outlook para Windows através do protocolo ActiveSync.**

## Requisitos

- Dispor de um endereço de correio eletrónico [Zimbra Pro](/links/web/emails-zimbra).
- Dispor da aplicação [Outlook clássico](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) no Windows.
- Dispor das credenciais relativas ao endereço de correio eletrónico que pretende configurar.

/// details | Informações relativas à gestão e configuração dos serviços OVHcloud

OVHcloud coloca à sua disposição serviços cuja configuração, gestão e responsabilidade lhe são atribuídas. Caber-lhe-á, por isso, assegurar o seu bom funcionamento.

Colocamos à sua disposição este guia para o ajudar no melhor possível em tarefas comuns. No entanto, recomendamos que contacte um [parceiro especializado](/links/transversal/marketplace-support-collaboration) e/ou o editor do serviço se encontrar dificuldades. De facto, não estaremos em posição de lhe prestar assistência. Mais informações na secção « [Quer saber mais?](go-further) » deste guia.

///

## Instruções

> [!warning]
>
> Antes de iniciar a sua configuração, é importante notar que a aplicação Outlook incluída gratuitamente com o Windows 11 é incompatível com o protocolo ActiveSync, necessário para a configuração de uma conta Zimbra Pro. Terá de utilizar a versão **Outlook clássico** para beneficiar do suporte ao protocolo ActiveSync.
>
> Para instalar o Outlook clássico no seu computador Windows, descarregue-o a partir da página Microsoft « [Instalar ou reinstalar o Outlook clássico num computador Windows](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) », e instale-o.
>
> Após a instalação, para distinguir as duas versões quando estiverem instaladas, escreva « Outlook » na barra de pesquisa do Windows. Poderá então constatar a diferença como abaixo.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}

### Adicionar a conta <a name="add-account"></a>

Para adicionar uma conta Zimbra Pro no Outlook clássico, siga os passos abaixo, clicando sucessivamente nos separadores abaixo:

> [!tabs]
> **Passo 1**
>>
>> 1. Aceda ao **painel de controlo** do Windows.
>> 2. Clique em `Contas de utilizador`{.action}.
>> 3. Clique em `Correio`{.action}.
>> 4. Clique em `Contas de correio...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Passo 2**
>>
>> - A partir da janela **Definições da conta**, no separador `Correio`, clique em `Novo...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Passo 3**
>>
>> - A partir da janela **Adicionar conta**, selecione `Configuração manual ou tipos de servidores adicionais`{.action}.
>> - Clique em `Seguinte`{.action} para continuar.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Passo 4**
>>
>> - Selecione `Exchange ActiveSync`{.action}.
>> - Clique em `Seguinte`{.action} para continuar.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Passo 5**
>>
>> Introduza as informações de ligação à sua conta:
>>
>> - **O seu nome** : Defina um nome de exibição.
>> - **Endereço de correio eletrónico** : Introduza o seu endereço de correio eletrónico completo.
>> - **Servidor de correio** : Introduza « zimbra1.mail.ovh.net ».
>> - **Nome de utilizador** : Introduza o seu endereço de correio eletrónico completo.
>> - **Palavra-passe** : Introduza a palavra-passe associada ao seu endereço de correio eletrónico.
>>
>> Clique em `Seguinte`{.action} para finalizar a adição da conta.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Passo 6**
>>
>> O seu endereço de correio eletrónico está agora configurado para o Outlook. Para beneficiar de uma sincronização completa das funcionalidades da sua conta Zimbra Pro, **descarregue e instale** o módulo « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) ».
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Passo 7**
>>
>> Após a instalação do módulo « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) », inicie o Outlook clássico.
>> A primeira vez, aparece a janela de configuração **Zimbra Server configuration Settings**. Introduza as seguintes informações:
>>
>> - **Nome do servidor** : Introduza « zimbra1.mail.ovh.net ».
>> - **Endereço de correio eletrónico** : Introduza o seu endereço de correio eletrónico completo.
>> - **Palavra-passe** : Introduza a palavra-passe associada ao seu endereço de correio eletrónico.
>>
>> Não é necessário alterar os restantes parâmetros. Clique em `Aplicar`{.action} para validar os parâmetros e certifique-se de que estão corretos. Clique finalmente em `OK`{.action} para aceder ao Outlook e começar a utilizar o seu endereço de correio eletrónico.
>>
>> ![outlook Windows](images/outlook-windows-add-step-07.png){.thumbnail .h-500}

> [!warning]
>
> Se encontrar um problema de envio ou receção após seguir as etapas de configuração acima, consulte a secção « [Modificar as definições existentes](#modify-settings) » deste guia.

### Utilizar o endereço de correio eletrónico

Uma vez o endereço de correio eletrónico configurado, pode começar a utilizá-lo! Pode enviar e receber mensagens, bem como gerir os seus calendários e tarefas.

OVHcloud também oferece uma aplicação web que permite aceder ao seu endereço de correio eletrónico a partir de um navegador Internet. Pode ligar-se ao [webmail OVHcloud](/links/web/email) com as credenciais do seu endereço de correio eletrónico. Para qualquer questão relativa à sua utilização, consulte o nosso guia « [Utilizar o webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra) ».

### Como modificar as definições existentes? <a name="modify-settings"></a>

Para modificar as definições de uma conta de correio eletrónico já configurada, siga as instruções abaixo:

1. Aceda ao **painel de controlo** do Windows.
1. Clique em `Contas de utilizador`{.action}.
1. Clique em `Correio`{.action}.
1. Clique em `Contas de correio...`{.action}.
1. Selecione a conta de correio eletrónico pretendida na lista e clique em `Modificar...`{.action}.

![outlook ios](images/outlook-windows-modify-01.png){.thumbnail .h-500}

Consulte as definições no **passo 7** do capítulo « [Adicionar a conta](#add-account) ».

### Como eliminar uma conta de correio eletrónico? <a name="delete-account"></a>

Para eliminar a sua conta de correio eletrónico, siga as instruções abaixo:

1. Aceda ao **painel de controlo** do Windows.
1. Clique em `Contas de utilizador`{.action}.
1. Clique em `Correio`{.action}.
1. Clique em `Contas de correio...`{.action}.
1. Selecione a conta de correio eletrónico pretendida na lista e clique em `Eliminar`{.action}.

![outlook ios](images/outlook-windows-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> Para poder eliminar a sua conta de correio eletrónico, é necessário que esta não seja a conta de correio eletrónico predefinida.

## Quer saber mais? <a name="go-further"></a>

> [!primary]
>
> Para mais informações sobre a configuração de um endereço de correio eletrónico a partir da aplicação Outlook no Windows, consulte o [centro de ajuda da Microsoft](https://support.microsoft.com/fr-fr/office/ajouter-un-compte-de-messagerie-%C3%A0-outlook-pour-windows-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794).

Para serviços especializados (indexação, desenvolvimento, etc.), contacte os [parceiros OVHcloud](/links/partner).

Se desejar beneficiar de uma assistência na utilização e configuração das suas soluções OVHcloud, propomos-lhe consultar as nossas diferentes [ofertas de apoio](/links/support).

Fale com a nossa [comunidade de utilizadores](/links/community).