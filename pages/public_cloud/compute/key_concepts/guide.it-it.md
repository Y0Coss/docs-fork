---
title: 'Public Cloud Instances - Concetti chiave'
excerpt: 'Scopri i fondamenti del Public Cloud Compute: funzionamento delle istanze, famiglie e dimensioni disponibili, distribuzioni multi-AZ, gestione delle immagini, sicurezza SSH, meccanismi di backup, rete pubblica/privata, e vantaggi dei Savings Plans.'
updated: 2025-12-03
---

## Obiettivo

Questa guida ha l'obiettivo di fornirti una chiara comprensione dei concetti fondamentali necessari alla creazione, configurazione e gestione delle tue prime istanze di Public Cloud Compute di OVHcloud. Imparerai come funzionano le istanze, come scegliere il tipo corretto di istanza e come gli elementi chiave come le immagini, le zone di disponibilità, la rete, la sicurezza e i backup si integrano all'interno dell'ecosistema OVHcloud.

## Cos'è un'istanza (Macchina Virtuale)?

Un'istanza, o Macchina Virtuale (VM), è un server completamente isolato che si esegue sull'infrastruttura fisica condivisa di OVHcloud. Funziona come un server tradizionale, ma offre la flessibilità e l'elasticità del cloud. Puoi scegliere il sistema operativo, definire le risorse CPU, RAM e di archiviazione, e distribuire le tue applicazioni, siti web o ambienti di sviluppo.

Le istanze di Public Cloud Compute offrono:

- Creazione su richiesta e dimensionamento flessibile – Allocare risorse in base alle tue esigenze.
- Fatturazione a consumo – Fatturato all'ora o al mese in base all'utilizzo effettivo.
- Integrazione trasparente con i servizi OVHcloud – inclusi l'archiviazione oggetti (*Object Storage*), la rete, i backup e molto altro.

Le istanze possono essere gestite tramite lo Spazio Cliente OVHcloud, l'interfaccia Horizon, gli endpoint API, o tramite strumenti di automazione e orchestrazione come l'OVHcloud CLI e Terraform.

## Tipi di istanze

OVHcloud offre diverse famiglie di istanze progettate per rispondere a diversi tipi di carico di lavoro. Ogni famiglia presenta una gamma di dimensioni (*flavors*) per soddisfare esattamente le tue esigenze in termini di risorse.

| Tipi di istanze  | Descrizione                      | Caso d'uso tipico                                                                                                                                                        |
| ------------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Generale           | Equilibrio CPU e Memoria         | Adatta a server di sviluppo, applicazioni web e carichi di lavoro aziendali generali. Fornisce un rapporto bilanciato tra CPU e RAM.                                            |
| CPU ottimizzata      | Alta prestazione del processore     | Ideale per applicazioni intensiva di calcolo, attività di elaborazione parallela, pipeline CI/CD o microservizi che richiedono una frequenza CPU elevata.                                     |
| Memoria ottimizzata  | Capacità di memoria elevata          | Progettata per l'analisi dei dati, carichi di lavoro big data e cache di database. Presenta rapporti memoria/CPU elevati e IOPS accelerati. I core virtuali sono clockati a 2 GHz o più.       |
| Archiviazione ottimizzata | Alta prestazione IOPS           | Dotata di archiviazione NVMe per E/S su disco ultraveloci, ideale per database e applicazioni big data.                                                                     |
| GPU                | Grafica accelerata hardware      | Fornisce una prestazione di calcolo parallelo eccezionale, fino a 1000 volte più veloce della CPU per alcuni carichi di lavoro. Adatta all'IA, al machine learning e al rendering 3D.               |
| Scoperta         | Risorse condivise, economica | Istanze di base con risorse condivise, offrendo una prestazione stabile a un prezzo accessibile. Ideale per ambienti di test, addestramento o progetti di dimostrazione. | 

Ogni famiglia di istanze include diverse dimensioni (flavors) per aiutarti a adattare l'istanza alle esigenze specifiche delle tue applicazioni.

## Localizzazione e zone di disponibilità

Le istanze di Public Cloud di OVHcloud sono distribuite su [più centri dati in tutto il mondo](&#x2F;links&#x2F;infrareg), garantendo alta disponibilità e vicinanza ai tuoi utenti. Esempi di regioni:

- GRA – Gravelines, Francia
- BHS – Beauharnois, Canada
- DE – Francoforte, Germania

**Tipi di zone di disponibilità :**

| Tipi di zona                   | Descrizione                                                                    | Utilizzo consigliato                                                                                        |
| ------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| 1-AZ (Single Availability Zone) | Le istanze sono distribuite in una singola zona.                                   | Ambienti semplici, sviluppo, test o carichi di lavoro non critici.                                  |
| 3-AZ (Triple Availability Zone) | Le istanze sono distribuite su tre zone ridondanti all'interno della stessa regione. | Carichi di lavoro di produzione che richiedono alta disponibilità e tolleranza ai guasti.                                  |
| Local Zones                     | Posizioni periferiche più vicine agli utenti finali per ridurre il ritardo. | Applicazioni sensibili al ritardo come l'elaborazione dati in tempo reale, i giochi online o i servizi web interattivi. | 

&gt; [!primary]
&gt; 
&gt; **Buona pratica :** Per carichi di lavoro critici, preferisci un [deploy multi-AZ](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_cross_functional&#x2F;3az_ref_architecture) per garantire resilienza e continuità del servizio.
&gt;

## Immagini di sistema disponibili

Alla creazione di un'istanza, selezioni un'immagine che include il sistema operativo e, eventualmente, applicazioni preinstallate. OVHcloud offre una varietà di immagini per soddisfare esigenze diverse :

- **Distribuzioni Linux :** Ubuntu, Debian, CentOS, AlmaLinux, Rocky Linux e altre. Queste immagini sono pronte all'uso per server web, ambienti di sviluppo e carichi di lavoro generali.
- **Windows Server :** Versioni con licenze integrate, permettendo un immediato deployment per applicazioni Microsoft e carichi di lavoro aziendali.
- **Applicazioni preconfigurate :** Immagini che includono software come cPanel, Plesk, Docker o NVIDIA GPU Cloud (NGC). Semplificano il deployment e accelerano il passaggio alla produzione.
- **[Immagini personalizzate](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;upload_own_image) :** Puoi importare le tue immagini nei formati QCOW2 o RAW, offrendo un controllo completo sul tuo ambiente e permettendo migrazioni, modelli standardizzati o configurazioni specializzate.

**Ciclo di vita e supporto :** OVHcloud aggiorna regolarmente il catalogo delle immagini. Consulta sempre le notizie sul ciclo di vita e la fine del supporto per assicurarti che le tue immagini siano sicure e supportate. Vedi [qui](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;image-life-cycle).

## Chiavi SSH

Le chiavi SSH offrono un modo sicuro per accedere alle tue istanze senza utilizzare password. Sono composte da due elementi :

- **Chiave pubblica :** Installata sull'istanza per permettere l'accesso.
- **Chiave privata :** Conservata in modo sicuro sulla tua macchina locale e utilizzata per autenticare la connessione.

L'autenticazione SSH garantisce un accesso crittografato e affidabile ai tuoi server.

Buone pratiche :

- Non condividere mai la tua chiave privata.
- Utilizza una chiave unica per ogni utente.
- Conserva le tue chiavi in un gestore o in un cassetto sicuro.

Per istruzioni dettagliate sulla creazione e sull'utilizzo delle chiavi SSH, consulta la guida [OVHcloud su SSH](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;creating-ssh-keys-pci).

## Backup

I backup proteggono i tuoi dati e le configurazioni da perdite accidentali o errori. OVHcloud offre diversi meccanismi di backup per garantire la sicurezza delle tue istanze e dei tuoi dati :

- **Tipi di backup :**
    - Backup manuale : Crea uno snapshot del tuo disco in qualsiasi momento.
    - Backup automatici : Backup pianificati creati a intervalli regolari.
    - Creazione e ripristino dell'istanza : Distribuisci una nuova istanza direttamente da un backup esistente.
- **Posizioni di backup :**
    - Backup locale : Archiviato nella stessa regione della tua istanza.
    - Backup remoto : Crea automaticamente una copia del backup locale in una regione a tua scelta.

&gt; [!primary]
&gt;
&gt; **Buona pratica :** I backup non sostituiscono un'architettura resiliente. Per ambienti critici, combina i backup con la replicazione multi-AZ per garantire una protezione massima dei dati e una disponibilità ottimale del servizio.
&gt;

## Reti pubbliche e private

Le istanze di Public Cloud di OVHcloud possono essere collegate a diversi tipi di rete in base alle tue esigenze applicative.

| Tipi di rete        | Descrizione                                                                                   | Caso d'uso                                                                            |
| -----------------------| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Rete pubblica          | Le istanze sono collegate a Internet tramite un indirizzo IP pubblico.                         | Hosting di siti web, API o fornire accesso remoto ai tuoi server.                  |
| Rete privata (vRack)   | Una connessione privata tra le tue risorse OVHcloud, isolata da Internet.                   | Connessione di database, servizi backend o comunicazione interna tra istanze. | 

Il vRack ti permette di creare una rete sicura e isolata, anche attraverso diverse regioni o progetti.

**Esempio :** Ospita il tuo database su una rete privata mentre esponi solo il tuo server web sulla rete pubblica.

Per ulteriori dettagli sulla configurazione delle reti Public Cloud, consulta la guida ufficiale [OVHcloud sulle reti](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_network_services&#x2F;concepts-01-public-cloud-networking-concepts).

## Savings Plans

I Savings Plans ti permettono di ridurre i costi del Public Cloud Compute in cambio di un impegno di utilizzo costante su un periodo definito, che va da 1 mese a 3 anni.

**Vantaggi principali :**

- **Costi ridotti :** Più economico rispetto alla fatturazione *pay-as-you-go*.
- **Applicazione automatica :** Le economie si applicano automaticamente a tutte le istanze compatibili.
- **Flessibile :** Puoi cambiare i tipi o le dimensioni delle istanze mantenendo comunque i vantaggi del tuo piano.

**Casi d'uso ideali :**

- Carichi di lavoro stabili e prevedibili, come applicazioni di produzione o server aziendali.
- Servizi con esigenze di risorse costanti che beneficiano di un'ottimizzazione dei costi.

I Savings Plans ti aiutano a ottimizzare il tuo budget mantenendo le prestazioni e l'affidabilità del tuo ambiente cloud. Per ulteriori informazioni, consulta la guida ufficiale [OVHcloud sui Savings Plans](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_cross_functional&#x2F;savings_plans).

## Per saperne di più

Una volta che hai padroneggiato i concetti fondamentali del Public Cloud Compute di OVHcloud, puoi esplorare operazioni e attività di gestione più avanzate.

- [Come creare un'istanza Public Cloud e accedervi](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;public-cloud-first-steps)
- [Gestisci le tue istanze Public Cloud](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;first_steps_with_public_cloud_instance)
- [Avvia un'istanza su un volume avviabile](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;start_instance_on_attached_volume)
- [Metti in pausa o sospendi un'istanza](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;suspend_or_pause_an_instance)
- [Primi passi con applicazioni preinstallate](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;apps_first_steps)
- [Aggiungi crediti cloud](&#x2F;pages&#x2F;account_and_service_management&#x2F;managing_billing_payments_and_services&#x2F;add_cloud_credit_to_project)

Contatta la nostra [Community di utenti](&#x2F;links&#x2F;community).