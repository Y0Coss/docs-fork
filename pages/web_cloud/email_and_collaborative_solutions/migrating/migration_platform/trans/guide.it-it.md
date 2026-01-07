---
title: "Migrare le tue email da una piattaforma e-mail OVHcloud ad un'altra"
excerpt: "Scopri come migrare le tue email da una piattaforma Exchange o E-mail Pro ad un'altra piattaforma Exchange, E-mail Pro, MX Plan o Zimbra"
updated: 2025-12-22
---

## Obiettivo

Desideri migrare le tue email presenti su una piattaforma Exchange o E-mail Pro ad un'altra piattaforma Exchange, E-mail Pro o MX Plan. In questa guida troverai un processo di migrazione in due fasi:

1. **Configurare la piattaforma di destinazione**.
2. **Migrare i conti email** dalla piattaforma attuale verso la nuova.

![email-migration](images/migration_platform01.gif){.thumbnail}

> [!primary]
>
> Per migrare una soluzione MX Plan verso una piattaforma Exchange o E-mail Pro, ti invitiamo a seguire la nostra guida [Migrare un indirizzo email MX Plan verso un account E-mail Pro o Exchange](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel).
>

**Scopri come migrare le tue email da una piattaforma Exchange o E-mail Pro ad un'altra piattaforma Exchange o E-mail Pro.**

## Prerequisiti

- Disporre di una piattaforma **"sorgente"** con conti [Exchange](/links/web/emails-hosted-exchange) o [E-mail Pro](/links/web/email-pro) configurati o [Zimbra](/links/web/zimbra).
- Disporre di una piattaforma di **"destinazione"** con conti [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) o MX Plan (via l'offerta MX Plan o inclusa in un'offerta di [ospedalità web OVHcloud](/links/web/hosting)). Questa piattaforma deve disporre di conti non configurati o disponibili per accogliere le email che devono essere migrate.
- Essere connesso al tuo [spazio client OVHcloud](/links/manager).

## Procedura

### Configurare la piattaforma di destinazione

> [!warning]
>
> Prima di iniziare la tua migrazione, se hai appena ordinato la tua nuova offerta email, aggiungi prima il nome del dominio alla tua piattaforma email. Se stai migrando verso una piattaforma MX Plan, il nome del dominio associato essendo "fisso", puoi passare direttamente alla [prossima fase](#accountsmigration).
>
> Seleziona l'opzione `Domini associati`{.action} o `Dominio`{.action} sulla tua piattaforma, quindi clicca su `Aggiungi un dominio`{.action}. Una volta aggiunto il nome del dominio, assicurati che l'indicazione `OK` o `Attivo`{.action} sia presente nella colonna `Stato`.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Per ulteriori dettagli sull'aggiunta di un nome di dominio, segui la [guida E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), la [guida Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) o la [guida Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

### Migrare i conti email <a name="accountsmigration"></a>

La migrazione dei tuoi conti email si svolgerà in 3 grandi fasi, **Rinominare** il conto email originale, **creare** il nuovo conto email e **migrare** dalla piattaforma originale verso la nuova.

![email-migration](images/migration_platform03.gif){.thumbnail}

> [!warning]
>
> Caso particolare:
>
> - Se devi migrare **un conto Exchange o Zimbra PRO** verso un conto **E-mail Pro** o **Zimbra STARTER**, devi assicurarti che i tuoi conti email non superino i 10 Go (E-mail Pro) o 15 Go (Zimbra STARTER). Le funzioni collaborative, la sincronizzazione dei calendari e contatti non sono presenti su E-mail Pro o Zimbra STARTER e non possono essere migrate.
> - Se devi migrare **un conto Exchange, E-mail Pro o Zimbra** verso un conto **MX Plan**, devi assicurarti che il tuo conto email non superi i 5 Go. Le funzioni collaborative, la sincronizzazione dei calendari e contatti non sono presenti su MX Plan e non possono essere migrate.

#### Rinominare

Rinomina il conto email da migrare con un nome temporaneo (esempio: per migrare il conto email *john.smith@mydomain.ovh*, rinominalo in *john.smith01@mydomain.ovh*).

Nell'opzione `Comptes e-mail`{.action} della tua piattaforma email, clicca sul pulsante `...`{.action} quindi su `Modifica`{.action}.

![email-migration](images/migration_platform04.png){.thumbnail}

#### Creare

Crea la tua email sul nuovo conto della tua piattaforma E-mail Pro, Exchange o MX Plan (prendendo l'esempio precedente, creerai quindi *john.smith@mydomain.ovh* sulla tua nuova piattaforma)

Nell'opzione `Comptes e-mail`{.action} della tua piattaforma, clicca sul pulsante `...`{.action}, a destra del conto email di destinazione, quindi su `Modifica`{.action}.

![email-migration](images/migration_platform05.png){.thumbnail}

#### Migrare

> [!warning]
> 
> Solo i dati dei tuoi conti email saranno migrati (email, contatti, calendari, regole della casella di posta, ecc.). Le funzionalità legate alla tua piattaforma dovranno essere ricreate sulla nuova piattaforma :
>
> - [Alias](/pages/web_cloud/email_and_collaborative_solutions/common_email_features/feature_redirections) 
> - [Deleghe](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_delegation) 
> - [Gruppi](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_groups)
> - Contatti esterni
> - [Piede di pagina](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_footers)

Migra il conto email "sorgente" verso il conto della tua nuova piattaforma utilizzando il nostro strumento [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Per ulteriori informazioni su OMM, consulta la nostra guida [Migrare dei conti email via OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![email-migration](images/migration_platform06.png){.thumbnail}

Il tempo di migrazione dipende dalla quantità di dati da migrare verso il tuo nuovo conto. Questo può variare da pochi minuti a diverse ore.

Verifica, dopo la migrazione, che tu riesca a recuperare tutti i tuoi elementi collegandoti al webmail all'indirizzo [Webmail](/links/web/email).

Una volta completata la migrazione, puoi conservare o eliminare il conto originale con il nome temporaneo.

Se desideri eliminarlo, vai nell'opzione `Comptes e-mail`{.action} della tua piattaforma email originale, clicca sul pulsante `...`{.action} quindi su `Réinitialiser ce compte`{.action}.

### Verificare o modificare la configurazione del tuo dominio

A questo punto, le tue email dovrebbero già essere migrate e funzionanti. Per sicurezza, ti invitiamo a verificare che la configurazione del tuo dominio sia corretta consultando il tuo spazio client.

Per farlo, seleziona il servizio E-mail Pro, Exchange o Zimbra interessato, quindi vai nell'opzione `Domini associati`{.action} o `Dominio`{.action} sulla tua piattaforma. Verifica la sezione o la colonna `Diagnostico`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Se hai appena completato la migrazione o modificato un record DNS del tuo dominio, potrebbe essere necessario attendere alcune ore affinché l'aggiornamento venga visualizzato nell'[spazio client OVHcloud](/links/manager).
>

Per modificare la configurazione, clicca sulla pastiglia rossa e effettua la manipolazione richiesta. Questa richiede un tempo di propagazione di 4 a 24 ore massimo prima di essere pienamente attiva.

### Utilizzare le tue email migrate

Ti rimane solo da utilizzare le tue email migrate. Per farlo, OVHcloud mette a disposizione un'applicazione online (_web app_) accessibile all'indirizzo [Webmail](/links/web/email). Devi inserire gli identificativi relativi alla tua email.

Se hai configurato uno dei conti migrati su un client di posta (esempio: Outlook, Thunderbird), devi riconfigurarlo. Le informazioni di connessione al server OVHcloud sono cambiate a causa della migrazione.

> [!primary]
>
> Puoi anche migrare manualmente delle email verso OVHcloud utilizzando il nostro strumento [OVHcloud Mail Migrator (OMM)](/links/web/omm). Per farlo, devi disporre delle informazioni (utente, password, server) dell'email sorgente e dell'email di destinazione.
>

## Per saperne di più

[Gestire i contatti dei propri servizi](/pages/account_and_service_management/account_information/managing_contacts).

[Primi passi con l'offerta E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Primi passi con l'offerta Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Primi passi con l'offerta Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Contatta la nostra [Community di utenti](/links/community).