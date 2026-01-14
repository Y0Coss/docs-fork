---
title: 'Configurare HTTP/2 su OVHcloud Load Balancer'
excerpt: 'Configurazione di HTTP/2 su OVHcloud Load Balancer'
updated: 2026-01-14
---

> [!primary]
> **Nota sul supporto nativo del protocollo HTTP/2**
>
> A partire da giugno 2025, i frontends HTTP e TLS dei servizi Load Balancer di OVHcloud supportano nativamente il protocollo HTTP/2.
>
> La guida seguente rimane comunque applicabile per i frontends TCP, che possono risultare utili per applicazioni che richiedono una bassa latenza e alte prestazioni.
>
> Per attivare il protocollo HTTP/2 su frontends HTTP e TLS esistenti, è necessario effettuare l'invio del comando di aggiornamento riportato di seguito tramite l'API, dove **serviceName** è il nome interno del vostro Load Balancer.

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>

## Obiettivo

Questa guida ha due obiettivi principali:

- Aiutarvi a comprendere le differenze tra i frontends TCP, HTTP e TLS su un Load Balancer OVHcloud, permettendovi così di determinare se un frontend TCP è la scelta più appropriata per le vostre esigenze applicative specifiche, in particolare quando si gestisce il traffico HTTP/2.
- Se si ritiene che un frontend TCP sia desiderabile, fornire quindi istruzioni passo passo su come configurarlo per bilanciare efficacemente il traffico HTTP/2 sui vostri server backend.

## Prerequisiti

Avrete bisogno di:

- Un servizio [Load Balancer OVHcloud](/links/network/load-balancer);
- Un frontend TCP sul vostro Load Balancer;
- Un cluster di server (fattoria) TCP con almeno un server aggiunto;
- Server backend configurati per supportare e rispondere con HTTP/2;
- Avere accesso all'[API OVHcloud](/links/api).

## Procedura

### Perché utilizzare HTTP/2?

HTTP/2 apporta numerosi vantaggi per migliorare le prestazioni e l'efficienza delle vostre applicazioni:

- *Tempi di caricamento più rapidi* grazie al multiplexing, che permette di inviare più richieste in parallelo sulla stessa connessione.
- *Latenza ridotta* limitando gli scambi tra client e server.
- *Prestazioni di rete ottimizzate* grazie alla compressione degli header.

### Differenze tra i frontends HTTP/2 e TCP

Un frontend TCP opera al livello 4 (livello di trasporto) del modello OSI. Quando si configura un frontend TCP, il Load Balancer stabilisce una connessione TCP tra il client e un server backend. Ciò significa che il Load Balancer non ispeziona né comprende i dati HTTP/2 all'interno del flusso TCP. Di conseguenza, i frontends TCP offrono alte prestazioni grazie a un minimo elaboramento dei dati.

Tuttavia, poiché non comprende il protocollo applicativo, non può effettuare ottimizzazioni avanzate specifiche per HTTP, come il routing basato sul contenuto o la manipolazione degli header HTTP.

I frontends HTTP e TLS, invece, operano al livello 7 (livello applicativo). Quando un client si connette a un frontend compatibile con HTTP/2, il Load Balancer decodifica completamente i frame HTTP/2 prima di stabilire una connessione con un server backend.

Interpretando il protocollo applicativo, un frontend compatibile con HTTP/2 può fornire molte funzionalità avanzate. Queste includono la terminazione SSL/TLS (scaricando la crittografia/decrittografia dai server backend), il routing basato sul contenuto (ad esempio, indirizzando le richieste verso diverse fattorie backend in base al percorso dell'URL o agli header), la modifica delle richieste/risposte e il multiplexing HTTP/2.

**Dovreste utilizzare un frontend TCP quando:**

- Dovete bilanciare il carico di altri servizi non HTTP (ad esempio, database, applicazioni TCP personalizzate, SSH);
- Richiedete prestazioni massime e una latenza minima;
- I vostri server backend gestiscono già la terminazione SSL/TLS;
- Non avete bisogno di funzionalità HTTP avanzate specifiche, come il routing basato sul contenuto, la manipolazione degli header HTTP o le ottimizzazioni a livello del protocollo HTTP/2.

**Dovreste utilizzare un frontend compatibile con HTTP/2 quando:**

- Gestite principalmente traffico web (HTTP/HTTPS);
- Volete sfruttare i vantaggi delle prestazioni di HTTP/2 tra client e Load Balancer;
- Volete delegare la terminazione SSL/TLS dei vostri server backend al vostro Load Balancer;
- Avete bisogno di una logica di routing avanzata basata sugli header HTTP, sulle URL o su altri attributi del livello applicativo;
- Volete ottimizzare l'esperienza lato client sfruttando le funzionalità HTTP/2.

*Se decidete di utilizzare un frontend TCP, seguite le seguenti fasi di questa guida per configurarlo per l'utilizzo HTTP/2*.

### Configurare un frontend TCP per HTTP/2

> [!warning]
>
> L'ordine in cui vengono creati gli elementi è importante: prima di poter essere associati a delle regole, i percorsi devono essere configurati.
> 

#### Step 1: aggiungi un percorso

Di seguito andiamo a mostrare come aggiungere un percorso al servizio.

##### Tramite l'API

> [!faq]
>
> Servizio:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/tcp/route
>> >
>>
>
> Impostazioni:
>
>> > **serviceName** *
>> >
>> >> `<identificativo del Load Balancer>`
>> >
>> > **action**
>> >
>> >> **type**
>> >> >
>> >> > `"farm"`
>> >>
>> >> **target**
>> >> >
>> >> > `<id della farm TCP che deve gestire l’HTTP/2>`
>> >
>> > **frontendId**
>> >
>> >> `<identificativo del tuo front-end TCP 443>`
>

#### Step 2: aggiungi una regola

Ora vediamo come aggiungere una regola al percorso appena creato.

##### Tramite l'API

> [!faq]
>
> Servizio:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/tcp/route/{routeId}/rule
>> >
>>
>
> Impostazioni:
>
>> > **serviceName** *
>> >
>> >> `<identificativo del Load Balancer>`
>> >
>> > **routeId**
>> >
>> >> `<identificativo del percorso precedentemente creato>`
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

#### Step 3: applica le modifiche

Le modifiche effettuate su OVHcloud Load Balancer devono essere *espressamente applicate* a tutte le zone configurate: solo così saranno visibili ai visitatori. Questo consente di modificare le impostazioni in modo complesso in una sola volta.

Se disponi di più zone, dovrai applicare la stessa configurazione a ogni zona.

##### Tramite l'API

Aggiornamento di una zona:

> [!faq]
>
> Servizio:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>> >
>>
>
> Impostazioni:
>
>> > **serviceName** *
>> >
>> >> `<identificativo del Load Balancer>`
>> >
>> > **zone**
>> >
>> >> `<zona in cui distribuire la configurazione>`
>

#### Step 4: verifica lo stato del servizio

Dopo tutti questi passaggi, Load Balancer dovrebbe essere operativo per i tuoi server HTTP/2. A questo punto verifica e conferma lo stato del servizio inviando una richiesta al tuo OVHcloud Load Balancer e verificandone la risposta:

```bash
curl -I --http2 https://www.ovh.com/
HTTP/2 200
```

## Per saperne di più

Contatta la nostra [Community di utenti](/links/community).