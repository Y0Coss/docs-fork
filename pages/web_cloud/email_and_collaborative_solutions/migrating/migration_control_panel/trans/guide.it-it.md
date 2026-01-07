---
title: 'Migrare un indirizzo e-mail MX Plan verso un account E-mail Pro, Exchange o Zimbra'
excerpt: 'Scopri come migrare un indirizzo e-mail MX Plan verso un account E-mail Pro, Exchange o Zimbra'
updated: 2025-12-22
---

## Obiettivo

OVHcloud offre diverse soluzioni di posta elettronica: MX Plan (venduto singolarmente o incluso in un piano di hosting web), E-mail Pro, Exchange e Zimbra. Queste soluzioni offrono funzionalità specifiche e possono adattarsi a diversi usi. I tuoi bisogni sono cambiati? OVHcloud mette a tua disposizione uno strumento di migrazione che ti permette di passare da una soluzione all'altra.

**Scopri come migrare un indirizzo e-mail MX Plan verso un account E-mail Pro o Exchange.**

<iframe class="video" width="560" height="315" src="https://www.youtube-nocookie.com/embed/0JLLoBBvsCc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> [!warning]
>
> [OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm) permette di migrare i tuoi messaggi da un server di posta a un altro.<br>
> Se le tue e-mail sono conservate localmente (configurazione POP o archivio locale), puoi effettuare un [esportazione dal tuo software di posta](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), quindi [importare il tuo file PST tramite OMM](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm#realiser-une-migration-par-fichier) o [importare direttamente dal tuo software di posta](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

## Prerequisiti

- Disporre di un indirizzo e-mail MX Plan (tramite l'offerta MX Plan o incluso in un piano di [hosting web OVHcloud](/links/web/hosting)).
- Disporre di un servizio [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) con almeno un account non configurato (che apparirà nella forma « @configureme.me ») o [Zimbra](/links/web/zimbra).
- **Non aver configurato alcuna inoltrare sull'indirizzo e-mail MX Plan che desideri migrare**.
- Essere connessi al vostro [spazio client OVHcloud](/links/manager).

## Procedura

### Passo 1: delimitare il progetto

Le soluzioni E-mail Pro e Exchange dispongono di una base di funzionalità comuni. Tuttavia, esistono differenze a seconda degli utilizzi. Scegliendo un indirizzo Exchange, si dispone dell'intera gamma di funzioni collaborative, come la sincronizzazione del calendario e dei contatti. La soluzione E-mail Pro, invece, ne propone alcune, ma esse sono limitate all'utilizzo tramite webmail.

Prima di procedere, è quindi importante sapere verso quale offerta si desidera migrare i propri indirizzi e-mail MX Plan. Per aiutarvi in questa scelta, consultate la pagina delle [soluzioni e-mail professionali di OVHcloud](/links/web/emails) che propone un confronto dettagliato delle offerte. È possibile cumulare le soluzioni e quindi utilizzare, per lo stesso nome di dominio, uno o più account E-mail Pro e Exchange. Inoltre, se dovete migrare diversi account, vi consigliamo di mettere in atto un piano di migrazione.

### Passo 2: ordinare i vostri account E-mail Pro o Exchange

Questo passo è facoltativo se già disponete di un servizio Exchange o E-mail Pro verso cui effettuare questa migrazione.

In caso contrario, accedete al vostro [spazio client OVHcloud](/links/manager), quindi ordinate il servizio E-mail Pro o Exchange desiderato. Seguite le diverse fasi, quindi attendete l'installazione del servizio. Vi verrà inviata un'e-mail alla fine di questa operazione.

> [!primary]
>
> Dopo aver ordinato l'account, lasciatelo inizialmente nella forma « @configureme.me ». Infatti, verrà rinominato durante la migrazione.
>

### Passo 3: effettuare la migrazione

Prima di iniziare la migrazione, dovrete identificare la versione del MX Plan da cui state migrando.

> [!primary]
>
> La tecnologia e-mail della vostra offerta MX Plan può variare in base alla data di attivazione della vostra offerta o se una migrazione è avvenuta di recente. Questa tecnologia si distingue in particolare per l'interfaccia del suo webmail. Per identificarla dal vostro spazio client, seguite questi passaggi :
>
> 1. Accedete al vostro [spazio client OVHcloud](/links/manager).
> 1. Recatevi nella sezione `Web Cloud`{.action}.
> 1. Cliccate su `MX Plan`{.action}.
> 1. Selezionate il dominio interessato.
> 1. L'onghetto `Informazioni Generali`{.action} è selezionato per default.
> 1. Individuate la tecnologia utilizzata sotto la dicitura **Webmail** nell'area `Abbonamento`.
>
> ![MX plan](/pages/assets/schemas/emails/technology-email.png){.thumbnail .w-640}
>

#### 3.1 Migrazione manuale di un'offerta MX Plan verso Exchange, E-mail Pro o Zimbra  <a name="all-mxplan"></a>

> [!warning]
>
> Questa parte riguarda tutti i servizi MX Plan che utilizzano la tecnologia webmail Rouncube, Zimbra o OWA.
>
> Tuttavia, se desiderate migrare un servizio MX Plan che utilizza il webmail Roundcube verso una piattaforma Email Pro o Exchange OVHcloud, seguite la parte « [Migrazione automatica di un'offerta MX Plan Roundcube verso Exchange o Email Pro](#roundcube-mxplan) » di questa guida.

> [!warning]
>
> Se avete appena ordinato la vostra nuova offerta e-mail, aggiungete prima il nome di dominio alla vostra piattaforma e-mail, prima di iniziare la migrazione. <br> - *Ad esempio, per migrare l'account « myemail@mydomain.ovh », dovrete aggiungere il nome di dominio « mydomain.ovh » alla vostra piattaforma.*
>
> Selezionate l'onghetto `Domini associati`{.action} o `Dominio`{.action} sulla vostra piattaforma, quindi cliccate su `Aggiungi un dominio`{.action}. Una volta aggiunto il nome di dominio, assicuratevi che l'indicazione `OK` o `Attivo`{.action} sia presente nella colonna `Stato`.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Per ulteriori dettagli sull'aggiunta di un nome di dominio, seguite [la guida E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [la guida Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) o [la guida Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

La migrazione del vostro MX Plan si svolgerà in 3 grandi fasi, **Rinomina**, **Crea** e **Migra**.

![exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Rinominate** l'account MX Plan da migrare con un nome temporaneo (esempio: per migrare l'account MX plan *john.smith@mydomain.ovh*, rinominate quest'ultimo in *john.smith01@mydomain.ovh*).

Nell'onghetto `Account e-mail`{.action} della vostra piattaforma MX Plan, cliccate sul pulsante `...`{.action} quindi su `Modifica`{.action}.

![exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> La modifica dell'account non è immediata, attendete la fine dell'operazione prima di passare al passo successivo.

2\. **Create** il vostro indirizzo e-mail sul nuovo account della vostra piattaforma E-mail Pro o Exchange (prendendo l'esempio precedente, andrete quindi a creare *john.smith@mydomain.ovh* sulla vostra nuova piattaforma).

Nell'onghetto `Account e-mail`{.action} della vostra piattaforma E-mail Pro o Exchange, cliccate sul pulsante `...`{.action} quindi su `Modifica`{.action}.

![exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Migra** l'account MX Plan verso l'account della vostra nuova piattaforma utilizzando il nostro strumento [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Per ulteriori informazioni su OMM, consultate la nostra guida [Migrare account e-mail tramite OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

Il tempo di migrazione dipende dalla quantità di contenuti da migrare verso il vostro nuovo account. Questo può variare da pochi minuti a diverse ore.

Verificate, dopo la migrazione, che i vostri elementi siano presenti accedendo al webmail all'indirizzo [Webmail](/links/web/email)

Potete conservare o eliminare l'account originale con il nome temporaneo dopo questa migrazione.

Se desiderate eliminarlo, recatevi nell'onghetto `Account e-mail`{.action} del vostro MX Plan, cliccate sul pulsante `...`{.action} quindi su `Reimposta questo account`{.action}.

#### 3.2 Migrazione automatica di un'offerta MX Plan Roundcube verso Exchange o Email Pro <a name="roundcube-mxplan"></a>

> [!warning]
>
> Questa parte riguarda esclusivamente i servizi MX Plan che utilizzano la tecnologia webmail Rouncube.

> [!primary]
>
> Il vostro account OVHcloud deve essere preventivamente contatto amministratore **e** contatto tecnico del servizio MX plan da migrare, **nonché** del servizio E-mail Pro o Exchange verso cui state migrando.
>
> Per ulteriori informazioni sui cambiamenti di contatti, consultate la nostra guida per [gestire i contatti dei propri servizi](/pages/account_and_service_management/account_information/managing_contacts).
>

La migrazione può essere effettuata da due interfacce :<br>

- **quella dell'assistente di configurazione Hosted Exchange**, esclusivamente se avete appena ordinato un servizio Hosted Exchange e non avete ancora configurato nulla su quest'ultimo ;
- **quella del MX Plan**, non appena disponete di un servizio E-mail Pro o Exchange (già configurato o meno) e di un indirizzo MX Plan che desiderate migrare.

> A titolo di ricordo, prima di iniziare la migrazione, assicuratevi che non siano state configurate **redirezioni** o **risponditori automatici** sul vostro MX Plan.
>
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Una volta che siete pronti, proseguite nella lettura di questa documentazione in base all'interfaccia selezionata. Vi ricordiamo che il tempo di migrazione dipende dalla quantità di contenuti da migrare verso il vostro nuovo account. Questo può variare da pochi minuti a diverse ore.

> [!warning]
>
> Una volta confermata la migrazione, non potrete più accedere al vostro vecchio indirizzo e-mail MX Plan né annullare il processo di migrazione. Vi consigliamo vivamente di effettuare questa operazione in un orario opportuno.
>
> Anche se non potrete più accedere al vostro indirizzo e-mail attuale, i messaggi già ricevuti nonché quelli ricevuti non andranno persi. Tutti saranno immediatamente accessibili dal vostro nuovo account.
>

##### **Migrazione dall'assistente di configurazione Exchange**

Per accedervi, selezionate nel [spazio client OVHcloud](/links/manager) il servizio interessato. L'assistente dovrebbe apparire per aiutarvi a configurare il vostro nuovo servizio Exchange. Durante questo processo, potrete selezionare gli account e-mail MX Plan da migrare.

Se l'assistente di configurazione non appare, appariranno invece le informazioni generali del servizio Exchange. In questo caso, dovrete effettuare la migrazione dei vostri account tramite l'interfaccia MX Plan.

##### **Migrazione dall'interfaccia MX Plan**

Per effettuare la migrazione da questa interfaccia, recatevi nella sezione `E-mail`{.action} del vostro spazio client OVHcloud. Scegliete quindi il servizio con il nome del dominio delle vostre e-mail. Cliccate sull'icona a forma di ingranaggio sulla riga dell'account e-mail interessato (chiamato anche account sorgente) e poi su `Migra l'account`{.action}.

![exchange](images/access_the_migration_tool.png){.thumbnail}

Nella finestra che appare, selezionate il servizio di destinazione (quello verso cui desiderate migrare l'indirizzo) e cliccate su `Avanti`{.action}. Se possiede almeno un account "libero" (cioè ancora non configurato), la migrazione avverrà verso uno di questi account. Da qui, prendete visione delle informazioni che appaiono, validatele, quindi cliccate su `Avanti`{.action} per proseguire l'operazione.

Se non possedete un account "libero", apparirà un pulsante `Ordina account`{.action}. Seguite le fasi, quindi attendete che gli account siano installati per effettuare nuovamente l'operazione.

Confermate infine la password dell'indirizzo e-mail sorgente (quello che desiderate migrare), quindi cliccate su `Migra`{.action}. Questa operazione dovrà essere ripetuta tante volte quante necessarie per la migrazione di altri account.

![exchange](images/account_migration_steps.png){.thumbnail}

### Passo 4 : verificare o modificare la configurazione del vostro dominio

A questo punto, le vostre e-mail dovrebbero già essere migrate e funzionanti. Per sicurezza, vi invitiamo a verificare che la configurazione del vostro dominio sia corretta consultando il vostro spazio client.

Per farlo, selezionate il servizio E-mail Pro, Exchange o Zimbra interessato, quindi recatevi sull'onghetto `Domini associati`{.action} o `Dominio`{.action} sulla vostra piattaforma. Verificate la sezione o la colonna `Diagnostica`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Se avete appena effettuato la migrazione o modificato un record DNS del vostro dominio, potrebbe essere necessario attendere alcune ore affinché l'indicazione nell'[spazio client OVHcloud](/links/manager) venga aggiornata.
>

Per modificare la configurazione, cliccate sul tasto rosso e effettuate l'operazione richiesta. Quest'ultima richiede un tempo di propagazione di 4 a 24 ore al massimo prima di essere pienamente efficace.

### Passo 5 : utilizzare le vostre e-mail migrate

Non vi rimane che utilizzare le vostre e-mail migrate. Per farlo, OVHcloud mette a disposizione un'applicazione online (_web app_) accessibile all'indirizzo [Webmail](/links/web/email). Dovrete inserire i vostri identificativi relativi all'indirizzo e-mail.

Se avete configurato uno dei conti migrati su un client di posta (come Outlook), dovrete reimpostarlo. Le informazioni di accesso al server OVHcloud sono cambiate a causa della migrazione. Per aiutarvi, consultate la nostra documentazione dalle sezioni dedicate alla [E-mail Pro](/products/web-cloud-email-collaborative-solutions-email-pro) e [Hosted Exchange](/products/web-cloud-email-collaborative-solutions-mx-plan). Se non siete in grado di reimpostare l'account immediatamente, l'accesso tramite l'applicazione online è comunque possibile.

### Organizzazione del contenuto delle vostre e-mail dopo la migrazione <a name="content-after-migration"></a>

Quando vi connettete per la prima volta al vostro nuovo account e-mail, il contenuto migrato può essere parzialmente nascosto. Per visualizzare tutti gli elementi, dal webmail, cliccate sul triangolo accanto alla `Casella di ricezione` per rivelare le sottocartelle. Il contenuto migrato del vostro vecchio account e-mail dovrebbe apparire.

![exchange](images/owa_migrate_content.png){.thumbnail}

Le cartelle predefinite, come « elementi inviati » o « cestino » appaiono in inglese (« Sent items » e « Trash »), ad eccezione delle cartelle che avete creato voi.

Dopo una migrazione, non esitate a esplorare tutte le cartelle e sottocartelle del vostro account per verificare che tutti gli elementi siano presenti.

### Migrazione Manuale

Potete inoltre migrare manualmente le vostre e-mail verso la vostra nuova offerta e-mail OVHcloud utilizzando esclusivamente il vostro software di posta. Riferitevi alla nostra guida [Migrare manualmente la vostra e-mail](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration). Vi consigliamo comunque di utilizzare questo metodo solo quando i metodi principali non sono possibili.

## Per saperne di più

[Gestire i contatti dei propri servizi](/pages/account_and_service_management/account_information/managing_contacts).

[Primi passi con l'offerta E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Primi passi con l'offerta Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Primi passi con l'offerta Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Contatta la nostra [Community di utenti](/links/community).