---
title: "Zimbra Pro - Configurare l'account e-mail tramite ActiveSync su Outlook classico per Windows"
excerpt: "Scopri come configurare il tuo indirizzo e-mail Zimbra Pro su Outlook per Windows tramite il protocollo ActiveSync"
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

## Obiettivo

Gli account Zimbra Pro possono essere configurati su Windows utilizzando il protocollo ActiveSync, permettendoti di configurare in un'unica volta tutte le funzionalità collaborative del tuo indirizzo e-mail. L'applicazione Outlook per Windows consente di consultare il tuo account e-mail Zimbra Pro tramite il protocollo ActiveSync.

**Scopri come configurare il tuo indirizzo e-mail Zimbra Pro su Outlook per Windows tramite il protocollo ActiveSync.**

## Prerequisiti

- Disporre di un indirizzo e-mail [Zimbra Pro](/links/web/emails-zimbra).
- Disporre dell'applicazione [Outlook classico](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) su Windows.
- Disporre delle credenziali relative all'indirizzo e-mail che si desidera configurare.

/// details | Informazioni relative alla gestione e alla configurazione dei servizi OVHcloud

OVHcloud mette a disposizione servizi la cui configurazione, gestione e responsabilità spettano a voi. È quindi a voi il compito di assicurarne il corretto funzionamento.

Vi mettiamo a disposizione questa guida per accompagnarvi al meglio in attività comuni. Tuttavia, vi consigliamo di fare riferimento a un [partner specializzato](/links/transversal/marketplace-support-collaboration) e/o di contattare l'editore del servizio in caso di difficoltà. Infatti, non saremo in grado di fornirvi un supporto. Per ulteriori informazioni, consultare la sezione « [Aller plus loin](go-further) » di questa guida.

///

## Procedura

> [!warning]
>
> Prima di iniziare la configurazione, è importante notare che l'applicazione Outlook inclusa gratuitamente con Windows 11 non è compatibile con il protocollo ActiveSync, necessario per la configurazione di un account Zimbra Pro. Dovrai utilizzare la versione **Outlook classico** per beneficiare del supporto del protocollo ActiveSync.
>
> Per installare Outlook classico sul tuo computer Windows, scaricalo dalla pagina Microsoft « [Installer ou réinstaller Outlook classique sur un PC Windows](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) » e installalo.
>
> Una volta completata l'installazione, per distinguere le due versioni quando sono installate, digita « Outlook » nella barra di ricerca di Windows. Potrai quindi constatare la differenza come mostrato di seguito.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}

### Aggiungere l'account <a name="add-account"></a>

Per aggiungere un account Zimbra Pro su Outlook classico, segui le seguenti fasi cliccando successivamente sui tab sottostanti :

> [!tabs]
> **Fase 1**
>>
>> 1. Vai al **Pannello di controllo** di Windows.
>> 2. Clicca su `Account utente`{.action}.
>> 3. Clicca su `Posta`{.action}.
>> 4. Clicca su `Account di posta elettronica...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Fase 2**
>>
>> - Dalla finestra **Impostazioni account**, nell'etichetta `Posta`, clicca su `Nuovo...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Fase 3**
>>
>> - Dalla finestra **Aggiungi account**, seleziona `Configurazione manuale o tipi di server aggiuntivi`{.action}.
>> - Clicca su `Avanti`{.action} per proseguire.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Fase 4**
>>
>> - Seleziona `Exchange ActiveSync`{.action}.
>> - Clicca su `Avanti`{.action} per proseguire.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Fase 5**
>>
>> Inserisci le informazioni di accesso al tuo account :
>>
>> - **Il tuo nome** : Definisci un nome visualizzato.
>> - **Indirizzo e-mail** : Inserisci il tuo indirizzo e-mail completo.
>> - **Server di posta** : Inserisci « zimbra1.mail.ovh.net ».
>> - **Nome utente** : Inserisci il tuo indirizzo e-mail completo.
>> - **Password** : Inserisci la password associata al tuo indirizzo e-mail.
>>
>> Clicca su `Avanti`{.action} per completare l'aggiunta dell'account.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Fase 6**
>>
>> Il tuo indirizzo e-mail è ora configurato per Outlook. Per beneficiare di una piena sincronizzazione delle funzionalità del tuo account Zimbra Pro, **scarica e installa** il modulo « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) ».
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Fase 7**
>>
>> Una volta installato il modulo « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) », avvia Outlook classico.
>> La prima volta, verrà visualizzata la finestra di configurazione **Zimbra Server configuration Settings**. Compila le seguenti informazioni :
>>
>> - **Nome del server** : Inserisci « zimbra1.mail.ovh.net ».
>> - **Indirizzo e-mail** : Inserisci il tuo indirizzo e-mail completo.
>> - **Password** : Inserisci la password associata al tuo indirizzo e-mail.
>>
>> Non è necessario modificare gli altri parametri. Clicca su `Applica`{.action} per confermare i parametri e assicurati che siano corretti. Clicca infine su `OK`{.action} per accedere a Outlook e iniziare a utilizzare il tuo indirizzo e-mail.
>>
>> ![outlook Windows](images/outlook-windows-add-step-07.png){.thumbnail .h-500}

> [!warning]
>
> Se riscontri problemi di invio o ricezione dopo aver seguito le fasi di configurazione sopra indicate, consulta la sezione « [Modificare le impostazioni esistenti](#modify-settings) » di questa guida.

### Utilizzare l'indirizzo e-mail

Una volta configurato l'indirizzo e-mail, puoi iniziare a utilizzarlo! Puoi già inviare e ricevere messaggi, ma anche gestire i tuoi calendari e le tue attività.

OVHcloud propone anche un'applicazione web che permette di accedere al tuo indirizzo e-mail da un browser Internet. Puoi accedere al [webmail OVHcloud](/links/web/email) con le credenziali del tuo indirizzo e-mail. Per qualsiasi domanda relativa al suo utilizzo, consulta la nostra guida « [Utiliser le webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra) ».

### Come modificare le impostazioni esistenti ? <a name="modify-settings"></a>

Per modificare le impostazioni di un account e-mail già configurato, segui le istruzioni seguenti :

1. Vai al **Pannello di controllo** di Windows.
1. Clicca su `Account utente`{.action}.
1. Clicca su `Posta`{.action}.
1. Clicca su `Account di posta elettronica...`{.action}.
1. Seleziona l'account e-mail desiderato nell'elenco e clicca su `Modifica...`{.action}.

![outlook ios](images/outlook-windows-modify-01.png){.thumbnail .h-500}

Trova le impostazioni alla **fase 7** del capitolo « [Aggiungere l'account](#add-account) ».

### Come eliminare un account e-mail ? <a name="delete-account"></a>

Per eliminare il tuo account e-mail, segui le istruzioni seguenti:

1. Vai al **Pannello di controllo** di Windows.
1. Clicca su `Account utente`{.action}.
1. Clicca su `Posta`{.action}.
1. Clicca su `Account di posta elettronica...`{.action}.
1. Seleziona l'account e-mail desiderato nell'elenco e clicca su `Elimina`{.action}.

![outlook ios](images/outlook-windows-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> Per poter eliminare il tuo account e-mail, è necessario che non sia l'account e-mail predefinito.

## Per saperne di più <a name="go-further"></a>

> [!primary]
>
> Per ulteriori informazioni sulla configurazione di un indirizzo e-mail dall'applicazione Outlook su Windows, consulta il [centro assistenza Microsoft](https://support.microsoft.com/fr-fr/office/ajouter-un-compte-de-messagerie-%C3%A0-outlook-pour-windows-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794).

Per prestazioni specializzate (posizionamento, sviluppo, ecc.), contatta i [partner OVHcloud](/links/partner).

Se desideri beneficiare di un supporto sull'utilizzo e la configurazione delle tue soluzioni OVHcloud, ti proponiamo di consultare le nostre diverse [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).