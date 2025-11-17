60 - Avere sottoscritto una delle seguenti offerte e-mail :
    - MX Plan OVHcloud (disponibile tramite un'[offerta di hosting Web Cloud](/links/web/hosting)), un [hosting gratuito 100M](/links/web/domains-free-hosting) o un'offerta MX Plan ordinata separatamente.
    - [Exchange](/links/web/emails-hosted-exchange) o [Private Exchange](/links/web/emails-hosted-exchange).
    - [E-mail Pro](/links/web/email-pro).
    - [Zimbra](/links/web/zimbra).
    - Un'offerta e-mail esterna ad OVHcloud con DKIM abilitato.

85 - [Configurare automaticamente il DKIM per un'offerta e-mail OVHcloud](#auto-dkim)
- [Configurare il DKIM tramite API per un'offerta e-mail OVHcloud](#internal-dkim)
    - [API - Configurazione completa del DKIM](#firststep)
        - [Per MX Plan e Zimbra](#confemail)
        - [Per Exchange](#confex)
        - [Per E-mail Pro](#confemp)
    - [API - Gli stati diversi del DKIM](#dkim-status)
    - [API - Abilitare o cambiare un selettore DKIM](#enable-switch)
    - [API - Disabilitare e rimuovere il DKIM](#disable-delete)

106 Per comprendere bene perché il DKIM permette di rendere sicuri i vostri scambi di e-mail, è necessario comprendere come funziona. Il DKIM utilizza il «**hashing**» e la «**crittografia asimmetrica**» per creare una firma sicura. La **piattaforma e-mail** e la **zona DNS** del vostro nome a dominio vi aiuteranno a trasmettere le informazioni del DKIM ai vostri destinatari.

108 /// details | L'hashing <a name="hash"></a>

118 ///

120 /// details | La crittografia asimmetrica <a name="encrypt"></a>

136 ///

138 /// details | Come vengono utilizzati l'hashing e la crittografia asimmetrica per il DKIM ? <a name="encrypt-and-hash"></a>

144 ///

146 /// details | Perché è necessario configurare i server DNS ? <a name="dns-and-dkim"></a>

150 ///

152 /// details | Cos'è un selettore DKIM ? <a name="selector"></a>

165 ///

167 /// details | Esempio di un'e-mail inviata utilizzando il DKIM <a name="example"></a>

177 ///

179 ### Configurare automaticamente il DKIM per un'offerta e-mail OVHcloud <a name="auto-dkim"></a>

La configurazione automatica del DKIM è disponibile per tutte le nostre offerte e-mail :

- MX Plan inclusa con un [hosting Web Cloud](/links/web/hosting), un [hosting gratuito 100M](/links/web/domains-free-hosting) o ordinata separatamente.
- [Exchange](/links/web/emails).
- [E-mail Pro](/links/web/email-pro).
- [Zimbra](/links/web/zimbra).

Quando configurate il vostro nome a dominio su una soluzione e-mail OVHcloud, la configurazione automatica del DKIM è proposta e realizzata per default se non la disattivate.

Se il DKIM non è stato attivato quando avete aggiunto un nome a dominio alla vostra piattaforma e-mail, dovrete avviare il processo di configurazione automatica tramite lo spazio client.

Cliccate sull'onghetto qui sotto corrispondente alla vostra offerta.

> [!tabs]
> **MX Plan**
>>
>> 1. Accedete al vostro [Spazio Cliente OVHcloud](/links/manager).
>> 1. Recatevi nella sezione `Web Cloud`{.action}.
>> 1. Cliccate su `MX Plan`{.action}.
>> 1. Selezionate il dominio interessato.
>> 1. Infine, andate sull'onghetto `Informazioni generali`{.action}.
>>
>> Nel riquadro **Informazioni generali**, potete osservare che il tasto `DKIM` è rosso sotto la dicitura **Diagnostica**.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Per attivare il DKIM, basta cliccare sul tasto `DKIM` rosso e poi su `Conferma`{.action} dalla finestra di attivazione che appare.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> Nel caso in cui il vostro nome a dominio non sia gestito nello stesso spazio client OVHcloud della vostra piattaforma e-mail o registrato fuori da OVHcloud, otterrete la finestra qui sotto :
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> Questa vi invita a inserire due valori CNAME nella zona DNS del nome a dominio, il che permette di collegare questo nome a dominio ai selettori DKIM del vostro servizio e-mail. È necessario inserire questi valori e assicurarvi che siano propagati prima di cliccare su `Attiva`{.action}.
>>
> **Exchange**
>>
>> 1. Accedete al vostro [Spazio Cliente OVHcloud](/links/manager).
>> 1. Recatevi nella sezione `Web Cloud`{.action}.
>> 1. Nella sezione `MICROSOFT`, cliccate su `Exchange`{.action}.
>> 1. Selezionate la piattaforma interessata.
>> 1. Infine, andate sull'onghetto `Domini associati`{.action}.
>>
>> A destra del nome a dominio interessato, potete osservare che il tasto `DKIM` è rosso.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Per attivare il DKIM, basta cliccare sul tasto `DKIM` rosso e poi su `Conferma`{.action} dalla finestra di attivazione che appare.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Accedete al vostro [Spazio Cliente OVHcloud](/links/manager).
>> 1. Recatevi nella sezione `Web Cloud`{.action}.
>> 1. Cliccate su `Email Pro`{.action}.
>> 1. Selezionate la piattaforma interessata.
>> 1. Infine, andate sull'onghetto `Domini associati`{.action}.
>>
>> A destra del nome a dominio interessato, potete osservare che il tasto `DKIM` è rosso.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Per attivare il DKIM, basta cliccare sul tasto `DKIM` rosso e poi su `Conferma`{.action} dalla finestra di attivazione che appare.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **Zimbra**
>>
>> 1. Accedete al vostro [Spazio Cliente OVHcloud](/links/manager).
>> 1. Recatevi nella sezione `Web Cloud`{.action}.
>> 1. Cliccate su `Zimbra Mail`{.action}.
>> 1. Infine, andate sull'onghetto `Dominio`{.action}.
>> 1. A destra del dominio interessato, cliccate su `⁝`{.action}, quindi su `Diagnostica`{.action}.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/access.png){.thumbnail .w-400 .h-600}
>>
>> A destra della dicitura `DKIM` sull'onghetto corrispondente, dovreste osservare un avviso che indica che il DKIM non è conforme. Cliccate sull'onghetto `DKIM`{.action} per accedere allo stato della configurazione DKIM. Per correggere l'errore, dovrete aggiungere o modificare due voci DNS di tipo CNAME nella zona DNS del nome a dominio associato, in base alle informazioni visibili da questo onggetto.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/dkim-cname-conf.png){.thumbnail .w-400 .h-600}
>>
>> > [!primary]
>> > **Suggerimento per creare un record CNAME**
>> >
>> > Dal [Spazio Cliente OVHcloud](/links/manager) dove è ospitato il nome a dominio del vostro servizio e-mail, nella sezione `Web Cloud`{.action}, cliccate su `Nomi di dominio`{.action} nella colonna di sinistra e selezionate il nome a dominio interessato.<br>
>> > Selezionate l'onghetto `Zona DNS`{.action} e cliccate su `Aggiungi un'entrata`{.action} nella finestra che appare. Scegliete `CNAME` e completate in base ai valori che avete notati.

Per attivare il DKIM, basta cliccare sul tasto `DKIM` rosso e poi su `Conferma`{.action} dalla finestra di attivazione che appare.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}

L'attivazione automatica del DKIM dura tra 30 minuti e 24 ore al massimo. Per verificare che il vostro DKIM funzioni, basta tornare nella sezione di gestione del dominio menzionata negli onggetti sopra e verificare che il tasto `DKIM` sia verde o, per un'offerta Zimbra, che l'onghetto `DKIM` non presenti più l'icona di avviso.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto03.png){.thumbnail .w-400 .h-600}

Oltre le 24 ore, se il vostro tasto `DKIM` è rosso, consultate la sezione [« Perché il DKIM non funziona e appare in rosso nello spazio client ? »](#reddkim) di questa guida.

### Configurare il DKIM tramite API per un'e-mail OVHcloud <a name="internal-dkim"></a>

Per una piattaforma Exchange o E-mail Pro, dovrete prima recuperare il riferimento della vostra piattaforma per configurare il vostro DKIM.

Cliccate sull'onghetto qui sotto corrispondente alla vostra offerta.

> [!tabs]
> **Exchange**
>>
>> 1. Accedete al vostro [Spazio Cliente OVHcloud](/links/manager).
>> 1. Recatevi nella sezione `Web Cloud`{.action}.
>> 1. Nella sezione `MICROSOFT`, cliccate su `Exchange`{.action}.
>> 1. Selezionate la piattaforma interessata.
>>
>> Per default, il nome della vostra piattaforma corrisponde al suo riferimento o sarà visibile sotto il nome che gli avete attribuito (vedere l'immagine qui sotto).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/general-information/dns-dkim-platform-exchange.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Accedete al vostro [Spazio Cliente OVHcloud](/links/manager).
>> 1. Recatevi nella sezione `Web Cloud`{.action}.
>> 1. Cliccate su `Email Pro`{.action}.
>> 1. Selezionate la piattaforma interessata.
>>
>> Per default, il nome della vostra piattaforma corrisponde al suo riferimento o sarà visibile sotto il nome che gli avete attribuito (vedere l'immagine qui sotto).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/email-pro/general-information/dns-dkim-platform-emailpro.png){.thumbnail .w-400 .h-600}

Assicuratevi anche che il nome a dominio che desiderate utilizzare per le vostre e-mail sia attivo nella sezione `Domini associati`{.action}.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dns-dkim-domain.png){.thumbnail .w-400 .h-600}

#### API - Configurazione completa del DKIM <a name="firststep"></a>

Per configurare il DKIM, recatevi sulla [pagina delle API OVHcloud](/links/console) e accedete :

1. Cliccate su `Authentication`{.action} in alto a sinistra.
1. Cliccate quindi su `Login with OVHcloud SSO`{.action}.
1. Inserite i vostri identificativi OVHcloud.
1. Cliccate sul pulsante `Authorize`{.action} per autorizzare le chiamate alle API da questo sito.

> [!primary]
>
> Riferitevi alla nostra guida « [Primi passi con le API OVHcloud](/pages/manage_and_operate/api/first-steps) » se non avete mai utilizzato le API.

Recatevi nella sezione `/email/domain/` (offerte MX Plan e Zimbra), `/email/exchange` (offerta Exchange) o `/email/pro` (offerta E-mail Pro) delle API e digitate « dkim » nel campo `Filter` per far apparire solo le funzioni API relative al DKIM.

Cliccate sull'onghetto corrispondente alla vostra offerta :

> [!tabs]
> **MX Plan e Zimbra**
>>
>> ![email](/pages/assets/screens/api/get-email-domain-domain-dkim.png){.thumbnail .w-400 .h-600}
>>
> **Exchange**
>>
>> ![email](/pages/assets/screens/api/get-email-exchange-organizationname-service-exchangeservice-domain-domainname-dkim.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> ![email](/pages/assets/screens/api/get-email-pro-service-domain-domainname-dkim.png){.thumbnail .w-400 .h-600}
>>

##### **Per MX Plan e Zimbra** <a name="confemail"></a>

Seguite le **5 fasi** cliccando successivamente su ciascuno dei 5 onggetti qui sotto :
```

> [!tabs]
> **1. Abilitare DKIM sul tuo dominio**
>> Per abilitare DKIM sul tuo dominio, utilizza l'API seguente:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : inserisci il nome del dominio associato al tuo servizio Email su cui desideri abilitare DKIM.
>>
>> Clicca su `EXECUTE`{.action} per avviare l'abilitazione.<br>
>>
>> *Esempio di risultato:*
>>
>> ```console
>> {
>>  "domain": "mydomain.ovh",
>>  "id": 123455789,
>>  "function": "domain/enableDKIM",
>>  "status": "todo"
>> }
>> ```
>>
>> Dovresti ottenere lo stesso risultato dell'esempio sopra con l'indicazione `"status": "todo"` che indica che il DKIM verrà installato.
>>
> **2. Verificare lo stato dell'operazione DKIM**
>> Dopo aver avviato il processo di abilitazione del DKIM, segui lo stato dell'installazione per verificare che l'installazione venga completata o per recuperare i record DNS se la tua zona DNS è gestita al di fuori del tuo Spazio Cliente OVHcloud.<br>
>>.
>> <br>
>> Per farlo, utilizza l'API seguente:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : inserisci il nome del dominio associato al tuo servizio Email.<br>
>> <br>
>> Clicca su `EXECUTE`{.action} per visualizzare il risultato.<br>
>>
>> *Esempio di risultato :*
>>
>> ```console
>> {
>>  "activeSelector": null,
>>  "autoconfig": true,
>>  "selectors": [
>>    {
>>      "selectorName": "ovhmo3456789-selector2",
>>      "status": "set",
>>      "cname": "ovhmo3456789-selector2._domainkey.mydomain.ovh CNAME ovhmo3456789-selector2._domainkey.123402.aj.dkim.mail.ovh.net."
>>    },
>>    {
>>      "selectorName": "ovhmo3456789-selector1",
>>      "cname": "ovhmo3456789-selector1._domainkey.mydomain.ovh CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.",
>>      "status": "set"
>>    }
>>  ],
>>  "status": "modifying"
>> }
>> ```
>> <br>
>> Nell'esempio sopra, l'ultima riga di stato `"status": "modifying"` significa che la configurazione è in corso. Aspetta circa **10 minuti** e rilancia l'API.
>>
>> - se il valore è `"status": "enabled"`, la tua configurazione è terminata e funzionale.
>> - se il valore è `"status": "disabled"`, la tua configurazione deve essere completata manualmente, vai al passo successivo.
>>
> **3. Recuperare il record DNS**
>> Devi configurare manualmente la zona DNS del tuo dominio **nei seguenti casi** :
>>
>> - il tuo servizio Email è collegato a un dominio gestito in un altro account cliente OVHcloud;
>> - il tuo servizio Email è collegato a un dominio gestito in un altro registro.
>>
>> Per configurare la tua zona DNS, devi recuperare i valori del record DNS **dei due selettori**. Per farlo, utilizza il risultato dell'API del passo precedente :
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : inserisci il nome del dominio associato al tuo servizio Email.
>>
>> Clicca su `EXECUTE`{.action} per visualizzare il risultato.
>>
>> *Esempio di risultato :*
>>
>> ```console
>> {
>>  "activeSelector": null,
>>  "status": "disabled",
>>  "autoconfig": false,
>>  "selectors": [
>>    {
>>      "cname": "ovhmo3456789-selector1._domainkey.mydomain.ovh CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.",
>>      "status": "toSet",
>>      "selectorName": "ovhmo4287928-selector1"
>>    },
>>    {
>>      "selectorName": "ovhmo4287928-selector2",
>>      "cname": "ovhmo3456789-selector2._domainkey.mydomain.ovh CNAME ovhmo3456789-selector2._domainkey.123402.aj.dkim.mail.ovh.net.",
>>      "status": "toSet"
>>    }
>>  ]
>> }
>> ```
>>
>> I valori `"status": "toSet"` e `"status": "disabled"` significano che i record CNAME devono essere configurati. Recupera i 2 valori `cname` in un file di testo e vai al passo successivo.
>>
> **4. Configurare il record DNS**
>> Dal [Spazio Cliente OVHcloud](/links/manager) dove è ospitato il dominio del tuo servizio e-mail, nell'onghetta `Web Cloud`{.action}, clicca su `Nomi di dominio`{.action} nella colonna di sinistra e seleziona il dominio interessato.<br>
>> Vai all'onghetta `Zona DNS`{.action} e clicca su `Aggiungi un'entrata`{.action} nella finestra che appare. Scegli `CNAME` e completa in base ai valori che hai registrato.
>>
>> Se si decompone il valore dell'esempio al passo "**3. Recuperare il record DNS**" :
>>
>> - `ovhmo3456789-selector1._domainkey.mydomain.ovh` corrisponde al sottodominio del record CNAME. Si mantiene solo `ovhmo3456789-selector1._domainkey` perché il `.mydomain.ovh` è già precompilato. <br>
>> - `ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net."` corrisponde alla destinazione del record. È bene mantenere il punto alla fine per delimitare il valore.<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api022.png){.thumbnail .w-400 .h-600}
>>
>> Una volta inseriti i valori, clicca su `Avanti`{.action} e poi su `Conferma`{.action}.
>>
>> > [!primary]
>> >
>> > **Ripeti questa operazione per il secondo selettore.**
>>
>> Se configuri la tua zona DNS in un'interfaccia esterna a OVHcloud, il tuo record CNAME deve avere la seguente forma :
>>
>> ```console
>> ovhmo3456789-selector1._domainkey IN CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Non dimenticare che una modifica in una zona DNS è soggetta a un ritardo di propagazione. È generalmente breve ma può arrivare fino a 24 ore.
>>
> **5. Abilitazione del DKIM**
>>
>> Dopo la propagazione della tua configurazione DNS, utilizza nuovamente l'API seguente per abilitare il DKIM :<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : inserisci il nome del dominio associato al tuo servizio e-mail su cui desideri abilitare DKIM.
>>
>> Clicca su `EXECUTE`{.action} per avviare l'abilitazione.<br>
>>
>> *Esempio di risultato :*
>>
>> ```console
>> {
>>  "selectors": [
>>    {
>>      "selectorName": "ovhmo3465680-selector2",
>>      "cname": "ovhmo3456789-selector2._domainkey.mydomain.ovh CNAME ovhmo3456789-selector2._domainkey.123402.aj.dkim.mail.ovh.net.",
>>      "status": "set"
>>    },
>>    {
>>      "status": "set",
>>      "cname": "ovhmo3456789-selector1._domainkey.mydomain.ovh CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.",
>>      "selectorName": "ovhmo3465680-selector1"
>>    }
>>  ],
>>  "activeSelector": "ovhmo3465680-selector1",
>>  "autoconfig": true,
>>  "status": "enabled"
>> }
>> ```
>>
>> - Se noti bene i valori `"status": "set"` sui 2 selettori, significa che sono correttamente configurati.
>> - Se noti i valori `"status": "toSet"` sui 2 selettori, significa che le tue modifiche DNS non sono visibili. Riprendi dall'onghetta « **4. Configurare il record DNS** ».
>> - Se noti bene i valori `"status": "toFix"` sui 2 selettori, significa che i record CNAME sono stati correttamente rilevati nella zona DNS del tuo dominio ma i valori sono errati. Riprendi dall'onghetta « **4. Configurare il record DNS** ».
>>
>> > [!success]
>> >
>> > Hai ora completato tutte le operazioni per abilitare il DKIM. Per verificare che sia correttamente abilitato, controlla il suo stato tornando all'onghetta del passo « **2. Verificare lo stato dell'operazione DKIM** » per verificare che il valore `status:` sia in `enabled`. Se è così, il tuo DKIM è ora attivo.
>>

##### **Per Exchange** <a name="confex"></a>

Segui le **5 fasi** seguenti cliccando su ciascuna delle schede.

> [!tabs]
> **1. Elenco dei selettori**
>> Prima di creare uno dei selettori per il tuo nome di dominio, devi recuperare il nome che ti è assegnato automaticamente dalla piattaforma Exchange.<br>
>> <br>
>> Per farlo, utilizza il seguente chiamata API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkimSelector
>> >
>> <br>
>>
>> - `domainName` : inserisci il nome del dominio collegato alla tua piattaforma Exchange su cui desideri abilitare DKIM. <br>
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1". <br>
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1". <br>
>>
>> *Esempio di risultato :*
>>
>> ```console
>> "ovhex123456-selector1"
>> "ovhex123456-selector2"
>> ```
>>
> **2. Creare un selettore**
>> Ora creerai un selettore, genererai la sua coppia di chiavi e il registro DNS associato al nome del dominio.<br>
>> <br>
>> Per farlo, utilizza il seguente chiamata API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : inserisci il nome del dominio collegato alla tua piattaforma Exchange su cui desideri abilitare il DKIM.
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1".
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1".
>> - `"selectorName"` : nell'onghetta **ESEMPIO** della sezione **REQUEST BODY**, inserisci il nome di un selettore che hai registrato nel passo precedente (esempio: "ovhex123456-selector1").
>>
>> *Esempio di input :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhex123456-selector1"
>> }
>> ```
>>
>> Clicca su `ESI ESECUZIONE`{.action} per avviare la creazione del selettore.<br>
>>
>> > [!primary]
>> >
>> > Ti consigliamo di effettuare questa operazione due volte per ciascuno dei selettori precedentemente elencati. Il secondo selettore ti permetterà di effettuare un cambio di coppia di chiavi quando necessario. Ti invitiamo a consultare il nostro caso d'uso [« Come cambiare la tua coppia di chiavi DKIM »](#2selectors) quando vorrai passare al secondo selettore.
>> <br>
>>
>> *Esempio di risultato :*
>>
>> ```console
>> status: "todo",
>> function: "addExchangeDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Recuperare il registro DNS**
>> Devi configurare manualmente la zona DNS del tuo nome di dominio **nei seguenti casi** :
>>
>> - la tua piattaforma Exchange è collegata a un nome di dominio che è gestito in un altro account cliente OVHcloud ;<br>
>> - la tua piattaforma Exchange è collegata a un nome di dominio che è gestito in un altro ufficio di registrazione ;<br>
>>
>> Per configurare la tua zona DNS, devi recuperare i valori del registro DNS **per ogni selettore se ne hai creati due**. Per farlo, utilizza il seguente chiamata API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : inserisci il nome del dominio collegato alla tua piattaforma Exchange su cui desideri configurare il DKIM.
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1".
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1".
>> - `selectorName` : inserisci il nome del selettore che hai creato nel passo precedente.
>>
>> *Esempio di risultato :*
>>
>> ```console
>> targetRecord: "ovhex123456-selector1._domainkey.1675.ac.dkim.mail.ovh.net"
>> recordType: "CNAME"
>> header: "from;to;subject;date"
>> taskPendingId: 108712689
>> status: "waitingRecord"
>> cnameIsValid: false
>> lastUpdate: "1970-01-01T00:00:00+01:00"
>> customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"
>> selectorName: "ovhex1234565-selector1"
>> ```
>>
>> Recupera i valori `customerRecord` e `targetRecord` in un file di testo. Passa al passo successivo.
>>
>> > [!primary]
>> >
>> > È possibile che il `status:` sia in `todo`, ciò non ha alcun impatto sulla configurazione della tua zona DNS.
>>
> **4. Configurare il registro DNS**
>> Dal [Spazio Cliente OVHcloud](/links/manager) dove è ospitato il nome del dominio della tua piattaforma Exchange, nell'onghetta `Web Cloud`{.action}, clicca su `Nomi di dominio`{.action} nella colonna di sinistra e seleziona il nome del dominio interessato.<br>
>> Vai all'onghetta `Zona DNS`{.action} e clicca su `Aggiungi un'entrata`{.action} nella finestra che appare. Scegli `CNAME` e completa in base ai valori che hai registrato.<br>
>>
>> Se prendiamo i valori dell'esempio al passo "**3.Recuperare il registro DNS**":
>>
>> - `customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"` corrisponde al sottodominio del registro CNAME. Manteniamo solo `ovhex123456-selector1._domainkey` poiché il `.mydomain.ovh` è già precompilato. <br>
>> - `targetRecord: "ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` corrisponde alla destinazione del registro. Aggiungi un punto alla fine per delimitare il valore. Questo dà `ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Una volta inseriti i valori, clicca su `Avanti`{.action} e poi su `Conferma`{.action}.<br>
>>
>> **Ripeti questa operazione per il secondo selettore se l'hai creato.**<br>
>>
>> Se configuri la tua zona DNS in un'interfaccia esterna a OVHcloud, il tuo registro CNAME deve avere la seguente forma :
>>
>> ```console
>> ovhex123456-selector1._domainkey IN CNAME ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Non dimenticare che una modifica in una zona DNS è soggetta a un ritardo di propagazione. È generalmente breve ma può arrivare fino a 24 ore.
>>
> **5. Abilitazione del DKIM**
>> > [!warning]
>> >
>> > Dalla sezione « [API - Gli stati diversi del DKIM](#dkim-status) » di questa guida, verifica che il valore `status:` sia effettivamente in `ready` prima di poter abilitare il DKIM.
>>
>> Per abilitare il DKIM, utilizza il seguente chiamata API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : inserisci il nome del dominio collegato alla tua piattaforma Exchange su cui desideri abilitare il DKIM.
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1".
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che appare nella forma "hosted-zz111111-1" o "private-zz111111-1".
>> - `selectorName` : inserisci il nome del selettore che hai creato.
>>
>> *Esempio di risultato :*
>>
>> ```console
>> id: 108716876
>> todoDate: "2023-05-05T11:30:11+02:00"
>> finishDate: null
>> status: "todo"
>> function: "enableExchangeDKIM"
>> ```
>>
>> > [!success]
>> >
>> > Hai ora completato tutte le operazioni necessarie per abilitare il DKIM. Per verificare che sia effettivamente abilitato, consulta la sezione « [API - Gli stati diversi del DKIM](#dkim-status) » di questa guida per verificare che il valore `status:` sia effettivamente in `inProduction`. Se è così, il tuo DKIM è ora attivo.<br><br> **Se hai creato due selettori**, il secondo selettore dovrebbe essere in `status: "ready"`.
>>

##### **Per Email Pro** <a name="confemp"></a>

Segui le **5 fasi** di seguito cliccando su ciascuna delle schede.

> [!tabs]
> **1. Elenco dei selettori**
>> Prima di creare uno dei selettori per il tuo dominio, devi recuperare il nome che ti viene assegnato automaticamente dalla piattaforma Email Pro.<br>
>> <br>
>> Per farlo, utilizza il seguente chiamata API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim
>> <br>
>>
>> - `service` : inserisci il nome della tua piattaforma Email Pro che ha la forma "emailpro-zz111111-1". <br>
>> - `domainName` : inserisci il nome del dominio associato alla tua piattaforma Email Pro su cui desideri attivare DKIM. <br>
>>
>> *Esempio di risultato :*
>>
>> ```console
>> "ovhemp123456-selector1"
>> "ovhemp123456-selector2"
>> ```
>>
> **2. Creare un selettore**
>> Ora creerai un selettore, genererai la sua coppia di chiavi e l'entry DNS associata al nome del dominio.<br>
>>
>> > [!primary]
>> >
>> > Ti consigliamo di eseguire questa operazione due volte per ciascun selettore precedentemente elencato. Il secondo selettore ti permetterà di effettuare un cambio della coppia di chiavi quando necessario. Ti invitiamo a consultare il nostro caso d'uso [« Come cambiare la tua coppia di chiavi DKIM »](#2selectors).
>> <br>
>> Per farlo, utilizza il seguente chiamata API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : inserisci il nome del dominio associato alla tua piattaforma Email Pro su cui desideri attivare DKIM.
>> - `service` : inserisci il nome della tua piattaforma Email Pro che ha la forma "emailpro-zz111111-1". <br>
>> - `"selectorName"` : Nella sezione **ESEMPIO** di **REQUEST BODY**, inserisci il nome di un selettore che hai individuato al passo precedente. (esempio: "ovhemp123456-selector1").
>>
>> *Esempio di input :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhemp123456-selector1"
>> }
>> ```
>>
>> Clicca su `EXECUTE`{.action} per avviare la creazione del selettore.<br>
>>
>> > [!primary]
>> >
>> > Ti consigliamo di eseguire questa operazione due volte per ciascun selettore precedentemente elencato. Il secondo selettore ti permetterà di effettuare un cambio della coppia di chiavi quando necessario. Ti invitiamo a consultare il nostro caso d'uso [« Come cambiare la tua coppia di chiavi DKIM »](#2selectors) quando vorrai passare al secondo selettore.
>>
>> *Esempio di risultato :*
>>
>> ```console
>> status: "todo",
>> function: "addDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Recuperare l'entry DNS**
>> Devi configurare manualmente la zona DNS del tuo dominio **nei seguenti casi** :
>>
>> - la tua piattaforma Email Pro è collegata a un dominio gestito in un altro account OVHcloud ;<br>
>> - la tua piattaforma Email Pro è collegata a un dominio gestito in un altro registro ;<br>
>>
>> Per configurare la tua zona DNS, devi recuperare i valori dell'entry DNS **per ogni selettore se ne hai creati due**. Per farlo, utilizza il seguente chiamata API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : inserisci il nome della tua piattaforma Email Pro che ha la forma "emailpro-zz111111-1" .
>> - `domainName` : inserisci il nome del dominio associato alla tua piattaforma Email Pro su cui desideri configurare il DKIM.
>> - `selectorName` : inserisci il nome del selettore che hai creato al passo precedente.
>>
>> *Esempio di risultato :*
>>
>> ```console
>> targetRecord: "ovhemp123456-selector1._domainkey.1675.ac.dkim.mail.ovh.net"
>> recordType: "CNAME"
>> header: "from;to;subject;date"
>> taskPendingId: 108712689
>> status: "waitingRecord"
>> cnameIsValid: false
>> lastUpdate: "1970-01-01T00:00:00+01:00"
>> customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"
>> selectorName: "ovhemp1234565-selector1"
>> ```
>>
>> Recupera i valori `customerRecord` e `targetRecord` in un file di testo. Passa al passo successivo.
>>
>> > [!primary]
>> >
>> > È possibile che il `status:` sia in `todo`, ciò non ha alcun impatto sulla configurazione della tua zona DNS.
>>
> **4. Configurare l'entry DNS**
>> Dal [Spazio Cliente OVHcloud](/links/manager) dove è ospitato il dominio della tua piattaforma Email Pro, clicca su `Web Cloud`{.action} nell'angolo in alto a destra, clicca su `Nomi di dominio`{.action} nella colonna di sinistra e seleziona il dominio interessato.<br>
>> Vai all'onglet `Zona DNS`{.action} e clicca su `Aggiungi un'entry`{.action} nella finestra che appare. Scegli `CNAME` e completa in base ai valori che hai recuperato.<br>
>>
>> Se prendiamo i valori dell'esempio al passo "**3.Recuperare l'entry DNS**":
>>
>> - `customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"` corrisponde al sottodominio dell'entry CNAME. Manteniamo solo `ovhemp123456-selector1._domainkey` poiché il `.mydomain.ovh` è già precompilato. <br>
>> - `targetRecord: "ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` corrisponde alla destinazione dell'entry. Aggiungi un punto alla fine per completare il valore. Questo darà `ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Una volta inseriti i valori, clicca su `Avanti`{.action} e poi su `Conferma`{.action}.<br>
>>
>> **Ripeti questa operazione per il secondo selettore se l'hai creato.**<br>
>>
>> Se configuri la tua zona DNS in un'interfaccia esterna a OVHcloud, la tua entry CNAME dovrà avere la seguente forma :
>>
>> ```console
>> ovhemp123456-selector1._domainkey IN CNAME ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Non dimenticare che una modifica in una zona DNS è soggetta a un periodo di propagazione. È generalmente breve ma può arrivare fino a 24 ore.
>>
> **5. Attivazione del DKIM**
>> > [!warning]
>> >
>> > Dalla sezione « [API - Gli stati del DKIM](#dkim-status) » di questa guida, verifica che il valore `status:` sia bene in `ready` prima di poter attivare il DKIM.
>>
>> Per attivare il DKIM, utilizza il seguente chiamata API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : inserisci il nome della tua piattaforma Email Pro che ha la forma "emailpro-zz111111-1" .
>> - `domainName` : inserisci il nome del dominio associato alla tua piattaforma Email Pro su cui desideri attivare il DKIM.
>> - `selectorName` : inserisci il nome del selettore che hai creato.
>>
>> *Esempio di risultato :*
>>
>> ```console
>> id: 108716876
>> todoDate: "2023-05-05T11:30:11+02:00"
>> finishDate: null
>> status: "todo"
>> function: "enableDKIM"
>> ```
>>
>> > [!success]
>> >
>> > Hai ora completato tutte le operazioni per attivare il DKIM. Per verificare che sia attivo, consulta la sezione « [API - Gli stati del DKIM](#dkim-status) » di questa guida per verificare che il valore `status:` sia bene in `inProduction`. Se è il caso, il tuo DKIM è ora attivo.<br><br> **Se hai creato due selettori**, il secondo selettore dovrebbe essere in `status: "ready"`.
>>

#### API - Gli stati del DKIM <a name="dkim-status"></a>

Seleziona l'offerta email interessata nei seguenti tabs :

> [!tabs]
> **MX Plan e Zimbra**
>> Durante le tue operazioni sul DKIM della tua piattaforma Email, utilizza la seguente chiamata API per verificare lo stato corrente del DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>>
>> - `domain` : inserisci il nome del dominio associato al tuo servizio Email su cui deve essere presente il DKIM.
>>
>> Osserva quindi il valore `status:` generale nel risultato :
>>
>> - `disabled` : il DKIM è disattivato, non è ancora stato configurato o è stato disattivato tramite API. <br>
>> - `modifying` : la configurazione del DKIM è in corso, è necessario attendere la fine del processo.<br>
>> - `toConfigure` : la configurazione del DKIM è in attesa dei parametri DNS del dominio. Devi configurare manualmente le entries DNS nella zona del dominio. Per farlo, consulta [il passo 4 di « la configurazione completa del DKIM » per MX Plan e Zimbra](#confemail).<br>
>> - `enabled` : il DKIM è configurato e funzionale.<br>
>> - `error` : Il processo di installazione ha incontrato un errore. Ti invitiamo a aprire un [ticket con il supporto](https://help.ovhcloud.com/csm?id=csm_get_help) specificando il nome del dominio interessato.<br>
>>
>> A livello dei selettori hai anche 3 possibili stati:
>>
>> - `set` : il selettore è correttamente configurato e attivo.
>> - `toSet` : il selettore non è configurato nella zona DNS del dominio. Consulta [il passo 4 di « la configurazione completa del DKIM » per MX Plan e Zimbra](#confemail).
>> - `toFix` : il selettore è correttamente configurato nella zona DNS del dominio ma i valori sono errati. Consulta [il passo 4 di « la configurazione completa del DKIM » per MX Plan e Zimbra](#confemail).
>>
> **Exchange**
>> Durante le tue operazioni sul DKIM della tua piattaforma Exchange, utilizza la seguente chiamata API per verificare lo stato corrente del DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : inserisci il nome del dominio associato alla tua piattaforma Exchange su cui deve essere presente il DKIM. <br>
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che ha la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che ha la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `selectorName` : inserisci il nome del selettore che hai creato. <br>
>>
>> Osserva quindi il valore `status:` nel risultato :
>>
>> - `todo` : il compito è stato inizializzato, sta per iniziare. <br>
>> - `WaitingRecord` : le entries DNS sono in attesa di configurazione o in corso di validazione nella zona DNS del dominio. Viene effettuata una verifica automatica regolare per verificare se l'entry DNS è presente e correttamente configurata.
>> - `ready` : le entries DNS sono presenti nella zona. Il DKIM può ora essere attivato. <br>
>> - `inProduction` : il DKIM è correttamente configurato e attivo, quindi pienamente operativo. <br>
>> - `disabling` : il DKIM è in corso di disattivazione. <br>
>> - `deleting` : il DKIM è in corso di cancellazione. <br>
>>
>> Se incontri l'errore seguente quando lanci la chiamata API, ciò significa che il selettore non esiste o è stato cancellato. Dovrai crearlo.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>
> **Email Pro**
>> Durante le tue operazioni sul DKIM della tua piattaforma Email Pro, utilizza la seguente chiamata API per verificare lo stato corrente del DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : inserisci il nome della tua piattaforma Email Pro che ha la forma « emailpro-zz111111-1 » . <br>
>> - `domainName` : inserisci il nome del dominio associato alla tua piattaforma Email Pro su cui deve essere presente il DKIM. <br>
>> - `selectorName` : inserisci il nome del selettore che hai creato . <br>
>>
>> Osserva quindi il valore `status:` nel risultato :
>>
>> - `todo` : il compito è stato inizializzato, sta per iniziare. <br>
>> - `WaitingRecord` : le entries DNS sono in attesa di configurazione o in corso di validazione nella zona DNS del dominio. Viene effettuata una verifica automatica regolare per verificare se l'entry DNS è presente e correttamente configurata. <br>
>> - `ready` : le entries DNS sono presenti nella zona. Il DKIM può ora essere attivato. <br>
>> - `inProduction` : il DKIM è correttamente configurato e attivo, quindi pienamente operativo. <br>
>> - `disabling` : il DKIM è in corso di disattivazione. <br>
>> - `deleting` : il DKIM è in corso di cancellazione. <br>
>>
>> Se incontri l'errore seguente quando lanci la chiamata API, ciò significa che il selettore non esiste o è stato cancellato. Dovrai crearlo.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>

#### API - Attivare o cambiare un selettore DKIM <a name="enable-switch"></a>

> [!warning]
>

> [!primary]
>
> Durante una rotazione del selettore DKIM, puoi attivare direttamente il secondo selettore che hai creato per passarci, mantenendo comunque il primo selettore che rimarrà attivo finché tutti gli e-mail consegnati con questo non saranno analizzati correttamente dal destinatario.

#### API - Disattivare e eliminare il DKIM <a name="enable-switch"></a>

> [!warning]
>
> **Per le offerte Exchange e E-mail Pro** <br>
>
> Il selettore DKIM deve essere in stato `inProduction` o `ready` prima di poter essere disattivato.

Seleziona l'offerta e-mail interessata tra le schede seguenti:

> [!tabs]
> **MX Plan e Zimbra**
>> Se desideri disattivare il DKIM senza eliminare i selettori e la loro coppia di chiavi, utilizza la seguente chiamata API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/disable
>> <br>
>>
>> - `domain` : inserisci il nome di dominio collegato al tuo servizio E-mail su cui deve essere presente il DKIM. <br>
>>
>> *Esempio di risultato :*
>>
>> ```console
>> {
>>  "domain": "guidesteam.ovh",
>>  "id": 174219594,
>>  "function": "domain/disableDKIM",
>>  "status": "todo"
>> }
>> ```
>>
> **Exchange**
>> Se desideri disattivare il DKIM senza eliminare il selettore e la sua coppia di chiavi, utilizza la seguente chiamata API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : inserisci il nome di dominio collegato alla tua piattaforma Exchange. <br>
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che appare nella forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che appare nella forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `selectorName` : inserisci il nome del selettore che desideri disattivare. <br>
>>
>> Se desideri eliminare il selettore DKIM e la sua coppia di chiavi, utilizza la seguente chiamata API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange DELETE /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : inserisci il nome di dominio collegato alla tua piattaforma Exchange. <br>
>> - `exchangeService` : inserisci il nome della tua piattaforma Exchange che appare nella forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : inserisci il nome della tua piattaforma Exchange che appare nella forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `selectorName` : inserisci il nome del selettore che desideri eliminare. <br>
>>
> **E-mail Pro**
>> Se desideri disattivare il DKIM senza eliminare il selettore e la sua coppia di chiavi, utilizza la seguente chiamata API:
>> 
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : inserisci il nome di dominio collegato alla tua piattaforma E-mail Pro. <br>
>> - `selectorName` : inserisci il nome del selettore che desideri disattivare. <br>
>> - `service` : inserisci il nome della tua piattaforma E-mail Pro che appare nella forma « emailpro-zz111111-1 ». <br>
>>
>> Se desideri eliminare il selettore DKIM e la sua coppia di chiavi, utilizza la seguente chiamata API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro DELETE /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : inserisci il nome di dominio collegato alla tua piattaforma E-mail Pro. <br>
>> - `selectorName` : inserisci il nome del selettore che desideri eliminare. <br>
>> - `service` : inserisci il nome della tua piattaforma E-mail Pro che appare nella forma « emailpro-zz111111-1 ». <br>
>>

### Configurare il DKIM per un'offerta e-mail al di fuori del tuo account OVHcloud <a name="external-dkim"></a>

Se desideri configurare la tua zona DNS per aggiungervi un record DKIM per la tua offerta, segui le istruzioni seguenti.

Dall'[Spazio Cliente OVHcloud](/links/manager), clicca sull'onghetta `Web Cloud`{.action} e poi su `Nomi di dominio`{.action} nella colonna di sinistra e seleziona il nome di dominio interessato.

Clicca sull'onghetta `Zona DNS`{.action} e poi su `Aggiungi un'entrata`{.action}. Esistono 3 modi per aggiungere un record per configurare il DKIM nella tua zona DNS:

- [un record DKIM](#dkim-record) : configurazione che permette di visualizzare tutti i parametri di un record DKIM.
- [un record TXT](#txt-record) : record da utilizzare quando ti sono stati forniti tutti i parametri DKIM.
- [un record CNAME](#cname-record) : record utilizzato per un'offerta e-mail OVHcloud o un server e-mail Microsoft.

#### Record DKIM <a name="dkim-record"></a>

Questo record è chiamato DKIM sull'interfaccia ma in realtà si tratta di un record TXT in uscita. Il record DKIM ha l'obiettivo di facilitare la lettura degli elementi diversi di configurazione del DKIM presentandoli sotto forma di caselle indipendenti.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-add.png){.thumbnail .w-400 .h-600}

- **Sottodominio** : inserisci il nome del selettore DKIM e aggiungi `._domainkey` come suffisso, il tuo nome di dominio verrà aggiunto automaticamente alla fine.

*esempio:*

```console
  selector-name._domainkey.mydomain.ovh.
```

- **Versione (v=)** : serve a indicare la versione del DKIM. È consigliato utilizzarla e il valore predefinito è `DKIM1`.<br>
Se specificato, questo tag deve essere posto in prima posizione nel record e deve essere uguale a "DKIM1" (senza virgolette). I record che iniziano con un tag "v=" con un'altra valore devono essere ignorati.

- **Granularità (g=)** : permette di specificare la parte « local-part » di un indirizzo e-mail, ovvero la parte che precede il « @ ».<br>
Consente di specificare l'indirizzo e-mail o gli indirizzi e-mail che sono autorizzati a firmare un messaggio elettronico con la chiave DKIM del selettore.<br>
Il valore predefinito di "g=" è "\*", il che significa che tutti gli indirizzi e-mail sono autorizzati a utilizzare la chiave di firma DKIM.<br>
Indicando un valore specifico per "g=", si può limitare l'utilizzo della chiave a una parte locale specifica di un indirizzo e-mail o a un intervallo di indirizzi e-mail specifici utilizzando caratteri generici (ad esempio: "\*-group").

- **Algoritmo (hash) (h=)** : permette di specificare gli algoritmi di hash utilizzati per firmare gli header delle e-mail. Questo tag permette di definire una lista di algoritmi di hash che verranno utilizzati per generare una firma DKIM per un messaggio specifico.

- **Tipo di chiave (k=)** : specifica l'algoritmo di firma utilizzato per firmare i messaggi elettronici in uscita. Permette ai destinatari di sapere come è stato firmato il messaggio e quale è il metodo utilizzato per verificare la sua autenticità.<br>
I valori possibili per il tag "k=" includono "rsa" per l'algoritmo di firma RSA e "ed25519" per l'algoritmo di firma Ed25519. La scelta dell'algoritmo dipende dalla politica di sicurezza dell'invio e dal supporto del destinatario.

- **Note (n=)** : serve a includere note di interesse per gli amministratori che gestiscono il sistema delle chiavi DKIM.<br>
Queste note possono essere utili per motivi di documentazione o per aiutare gli amministratori a comprendere o gestire il funzionamento del DKIM. Le note incluse in n= non vengono interpretate dai programmi e non influenzano il funzionamento del DKIM.

- **Chiave pubblica (base64) (p=)** : utilizzata per inserire i dati della chiave pubblica DKIM, che sono codificati in base64.<br>
Questo tag è obbligatorio nella firma DKIM e permette ai destinatari della firma di recuperare la chiave pubblica necessaria per verificare l'autenticità del messaggio firmato.

- **Revoca della chiave pubblica** : se una chiave pubblica DKIM è stata revocata (ad esempio in caso di compromissione della chiave privata), deve essere utilizzato un valore vuoto per il tag "p=", indicando che questa chiave pubblica non è più valida. I destinatari devono quindi restituire un errore per ogni firma DKIM che si riferisce a una chiave revocata.

- **Tipo di servizio (s=)**: Il tag "s=" (Tipo di Servizio) è opzionale e non è presente per default. Permette di specificare il o i tipi di servizio a cui si applica questo record DKIM.<br>
I tipi di servizio sono definiti utilizzando un elenco di parole chiave separate da due punti ":".<br>
Il destinatario deve ignorare questo record se il tipo di servizio appropriato non è elencato.<br>
Il tag "s=" è destinato a limitare l'utilizzo delle chiavi ad altre finalità, nel caso in cui l'utilizzo del DKIM fosse definito per altri servizi in futuro.<br>
I tipi di servizio attualmente definiti sono "\*" (tutti i tipi di servizio), "email" (posta elettronica).

- **Modalità test (t=y)** : permette ai proprietari del nome di dominio di testare l'implementazione del DKIM senza rischiare che i messaggi vengano rifiutati o contrassegnati come SPAM se la verifica della firma DKIM fallisce.<br>
Quando si utilizza il flag "t=y", il destinatario non deve trattare diversamente i messaggi firmati in modalità test rispetto ai messaggi non firmati. Tuttavia, il destinatario può tracciare il risultato della modalità test per aiutare i firmatari.

- **Sottodomini (t=s)** : permette di limitare l'utilizzo della firma DKIM al nome di dominio solo (ad esempio : @mydomain.ovh) o di permettere l'invio dal nome di dominio e dai suoi sottodomini (ad esempio : @mydomain.ovh, @test.mydomain.ovh, @other.mydomain.ovh, ecc.).

#### Record TXT <a name="txt-record"></a>

Si tratta del tipo di record nativo utilizzato per configurare il DKIM nella zona DNS del tuo nome di dominio. È necessario conoscere bene la sua sintassi per completarlo.

Questo tipo di configurazione DKIM è consigliato quando le informazioni da inserire ti sono state fornite dal fornitore del servizio e-mail.

Per comprendere bene la composizione del record DKIM, consulta la parte precedente di questa guida intitolata « [Record DKIM](#dkim-record) ».

**Esempio di un record DKIM**

- sottodominio :

```console
selector-name._domainkey.mydomain.ovh.
```

- destinazione :

```console
v=DKIM1;t=s;p= MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA77VDAIfyhjtoF0DIE5V7 rev1EKk4L0nxdBpD5O/jPrM4KP0kukeuB6IMpVplkkq52MSDeRcjoO50h0DmwZOr RUkyGjQwOnAh0VhY3fqkuwBYftEX7vWo8C2E1ylzimABkwPpSL62jZ1DheoXcil9 1M35wWBKtlYdXVedKjCQKOEnwTo+0hdNe38rU9NMgq6nbTIMjDntvxoVI+yF3kcx q/VpAY8BIYbcAXkVFvUyfUBABnnKpf0SfblsfcLW0Koy/FRxPDFOvnjNxXeOxMFR UI6K6PaW2WvtbJG2v+gHLY5M4tB0+/FNJU9emZfkPOk3DmRhZ8ENi7+oZa2ivUDj OQIDAQAB
```

#### Record CNAME <a name="cname-record"></a>

Il record CNAME è un alias. Questo significa che il valore destinazione punta verso un URL che fornirà direttamente il record DKIM al server che interrogherà il record CNAME. Questo tipo di record CNAME per configurare il DKIM è comune nel caso dell'utilizzo di un server e-mail Microsoft.

Si tratta precisamente del tipo di record utilizzato per attivare il DKIM su un nome di dominio dichiarato per un'offerta Exchange OVHcloud. Questo processo permette al tuo fornitore di soluzione e-mail di gestire per te la sicurezza e l'aggiornamento del DKIM.

### Testa il tuo DKIM <a name="test-dkim"></a>

Ti consigliamo di inviare un'e-mail da un account della tua piattaforma Exchange a un indirizzo e-mail che verifica la firma DKIM al momento della ricezione.

Ecco ciò che potrai trovare nell'intestazione dell'e-mail ricevuta :

<pre class="bgwhite"><code>ARC-Authentication-Results: i=1; mx.example.com;
       dkim=pass header.i=@mydomain.ovh header.s=ovhex123456-selector1 header.b=KUdGjiMs;
       spf=pass (example.com: domain of test-dkim@mydomain.ovh designates 54.36.141.6 as permitted sender) smtp.mailfrom=test-dkim@mydomain.ovh
Return-Path: &lt;test-dkim@mydomain.ovh&gt;
</code></pre>

Per recuperare l'intestazione di un'e-mail, consulta la nostra guida « [Recuperare l'intestazione di un'e-mail](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/diagnostic_headers) ».

### Casi d'uso <a name="usecases"></a>

#### Come e perché cambiare la coppia di chiavi DKIM sulla mia offerta ? <a name="2selectors"></a>

> [!warning]
>
> Questa domanda riguarda esclusivamente le offerte Exchange e E-mail Pro.

Quando attivi per la prima volta il DKIM sul tuo servizio e-mail, è possibile creare 2 selettori che contengono ciascuno una coppia di chiavi. Il secondo selettore funge da successore a quello che è in corso d'uso.

Per evitare tentativi di decrittazione della chiave DKIM, è consigliabile cambiare regolarmente la coppia di chiavi. A tal fine, assicurati di aver configurato correttamente i tuoi 2 selettori verificando che il primo sia in stato `inProduction` e il secondo in stato `ready`. Puoi verificare questo stato facendo riferimento alla sezione « [API - Gli stati diversi del DKIM

Hai notato che le tue email non sono firmate con DKIM, nonostante l'attivazione o la configurazione. In primo luogo, accedi al tuo Spazio Cliente per verificare lo stato del DKIM.

Clicca sul tab sottostante corrispondente alla tua offerta, per verificare lo stato del DKIM sulla tua piattaforma email.

> [!tabs]
> **Exchange**
>>
>> 1. Accedi al tuo [Spazio Cliente OVHcloud](/links/manager).
>> 1. Vai alla sezione `Web Cloud`{.action}.
>> 1. Nella sezione `MICROSOFT`, clicca su `Exchange`{.action}.
>> 1. Seleziona la piattaforma interessata.
>>
>> Nella sezione `Domaines associés`{.action}, verifica il colore dell'icona `DKIM` a destra del nome di dominio interessato (vedi l'immagine sottostante).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>
> **Email Pro**
>>
>> 1. Accedi al tuo [Spazio Cliente OVHcloud](/links/manager).
>> 1. Vai alla sezione `Web Cloud`{.action}.
>> 1. Clicca su `Email Pro`{.action}.
>> 1. Seleziona la piattaforma interessata.
>> 1. Infine, vai al tab `Domaines associés`{.action}.
>>
>> Nella sezione `Domaines associés`{.action}, verifica il colore dell'icona `DKIM` a destra del nome di dominio interessato (vedi l'immagine sottostante).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>

Ecco i 4 stati che causano l'icona DKIM in rosso nel tuo Spazio Cliente. Clicca sul tab corrispondente al tuo codice errore:

> [!tabs]
> **501**
>>
>> "Only one dkim selector has been initialized"<br><br>
>> Solo un selettore DKIM è presente nella tua configurazione. Per permetterci di effettuare il passaggio a una nuova chiave quando necessario, ti chiediamo di configurare entrambi i selettori forniti dal servizio.<br><br>
>> Per correggere questo errore:
>>
>> - Verifica lo stato dei selettori DKIM per identificare quello da configurare. A tale scopo, consulta la sezione « [API - Gli stati del DKIM](#dkim-status) » di questa guida.
>> - Una volta che hai identificato il selettore da configurare, segui le fasi della sezione « [API - Configurazione completa del DKIM](#firststep) » in questa guida, in base alla tua offerta (Exchange o Email Pro), applicandola esclusivamente al selettore interessato.
>> Aspetta al massimo 24 ore dopo la configurazione del selettore.
>>
> **502**
>>
>> "One DKIM configuration task is in error"<br><br>
>> Si è verificato un errore durante la configurazione del DKIM. Dopo 24 ore, se la tua configurazione è ancora in questo stato, ti invitiamo a aprire un [ticket con il supporto](https://help.ovhcloud.com/csm?id=csm_get_help).
>>
> **503**
>>
>> "CNAME record is wrong"<br><br>
>> Il valore del record CNAME necessario per la configurazione del DKIM non è stato inserito correttamente. Devi configurare correttamente la zona DNS del nome di dominio associato.
>> Per configurare la tua zona DNS, recupera i valori del record CNAME che vengono visualizzati:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Prendendo ad esempio l'immagine sopra, il nome di dominio è "mydomain.ovh" e ti è richiesto di configurare il selettore "2". In questo caso, devi aggiungere un record CNAME con sottodominio "ovhex1234567-selector2.domainkey.mydomain.ovh" e come destinazione "ovhex1234567-selector2.domainkey.7890.dkim.mail.ovh.net".<br><br>
>> Una volta che la tua zona DNS è configurata, aspetta il tempo di propagazione DNS (massimo 24 ore)
>>
> **504**
>>
>> "One CNAME record is missing"<br><br>
>> Il valore del record CNAME necessario per la configurazione del DKIM è mancante. Devi configurare la zona DNS del nome di dominio associato.
>> Per configurare la tua zona DNS, recupera i valori del record CNAME che vengono visualizzati:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Prendendo ad esempio l'immagine sopra, il nome di dominio è "mydomain.ovh" e ti è richiesto di configurare il selettore "2". In questo caso, devi aggiungere un record CNAME con sottodominio "ovhex1234567-selector2.domainkey.mydomain.ovh" e come destinazione "ovhex1234567-selector2.domainkey.890123.dkim.mail.ovh.net".<br><br>
>> Una volta che la tua zona DNS è configurata, aspetta il tempo di propagazione DNS (massimo 24 ore)
>>

#### Dall'interfaccia API OVHcloud, come capire lo stato del DKIM che non funziona? <a name="api-error"></a>

Se utilizzi le API OVHcloud per configurare il tuo DKIM e non funziona, consulta la sezione « [API - Gli stati del DKIM](#dkim-status) » di questa guida per identificare lo stato dei tuoi selettori.

Di seguito trovi gli stati che possono bloccare il funzionamento del tuo DKIM e la soluzione appropriata per ogni situazione.

> [!tabs]
> **Exchange e Email Pro**
>> - `WaitingRecord` : I record DNS sono in attesa di configurazione o in fase di validazione nella zona DNS del nome di dominio. Viene effettuata regolarmente una verifica automatica per verificare se il record DNS è presente e correttamente configurato. In base alla tua offerta, segui **l'etapa 5** nella sezione « [API - Configurazione completa del DKIM](#firststep) » per configurare correttamente la zona DNS del nome di dominio interessato.
>> - `ready` : I record DNS sono presenti nella zona. Il DKIM può ora essere attivato. Dovrai semplicemente attivare il selettore seguendo la sezione « [API - Attivare o cambiare un selettore DKIM](#enable-switch) ».
>> - `deleting` : Il DKIM è in corso di eliminazione. Dopo l'eliminazione, dovrai seguire la sezione « [API - Configurazione completa del DKIM](#firststep) ».
>> - `disabling` : Il DKIM è in corso di disattivazione. Dopo questa operazione, potrai attivare il selettore seguendo la sezione « [API - Attivare o cambiare un selettore DKIM](#enable-switch) ».
>> - `todo` : L'attività è stata inizializzata, deve essere avviata. Dopo 24 ore, se il tuo selettore è ancora in questo stato, ti invitiamo ad aprire un [ticket con il supporto](https://help.ovhcloud.com/csm?id=csm_get_help) specificando il numero del selettore interessato.
> **MX Plan e Zimbra**
>> - `disabled` : Il DKIM è disattivato, non è ancora stato configurato o è stato disattivato tramite API. <br>
>> - `modifying` : La configurazione del DKIM è in corso, è necessario attendere fino alla fine del processo.<br>
>> - `toConfigure` : La configurazione del DKIM è in attesa dei parametri DNS del nome di dominio. Devi configurare manualmente i record DNS nella zona del nome di dominio. A tale scopo, consulta l'etapa « [Configurazione completa del DKIM](#confemail) » di questa guida. <br>
>> - `error` : Il processo di installazione ha riscontrato un errore. Ti invitiamo ad aprire un [ticket con il supporto](https://help.ovhcloud.com/csm?id=csm_get_help) specificando il nome di dominio interessato.
>>
>> A livello dei selettori hai anche 2 stati relativi a un errore:
>>
>> - `toSet` : Il selettore non è configurato nella zona DNS del nome di dominio. Consulta [l'etapa 4 di « la configurazione completa del DKIM » per MX Plan e Zimbra](#confemail).
>> - `toFix` : Il selettore è stato correttamente configurato nella zona DNS del nome di dominio ma i valori sono errati. Consulta [l'etapa 4 di « la configurazione completa del DKIM » per MX Plan e Zimbra](#confemail).

## Per saperne di più
Contatta la nostra [Community di utenti](/links/community).

Nel contesto dell'implementazione di un record DNS dinamico (DynHost), l'utilizzo di un wildcard (carattere `*`) nella casella `sous-domaine`{.action} del modulo di un record DNS non è disponibile.