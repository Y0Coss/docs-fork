60 - Eine der folgenden E-Mail-Angebote abonniert haben:
    - MX Plan OVHcloud (über ein [Cloud-Web-Hosting-Angebot](/links/web/hosting) verfügbar), ein [kostenloses Hosting 100M](/links/web/domains-free-hosting) oder ein separat bestelltes MX Plan-Angebot.
    - [Exchange](/links/web/emails-hosted-exchange) oder [Private Exchange](/links/web/emails-hosted-exchange).
    - [E-mail Pro](/links/web/email-pro).
    - [Zimbra](/links/web/zimbra).
    - Ein E-Mail-Angebot außerhalb von OVHcloud mit DKIM.




85 - [DKIM automatisch für ein E-Mail-Angebot von OVHcloud konfigurieren](#auto-dkim)
- [DKIM per API für ein E-Mail-Angebot von OVHcloud konfigurieren](#internal-dkim)
    - [API - DKIM vollständig konfigurieren](#firststep)
        - [Für MX Plan und Zimbra](#confemail)
        - [Für Exchange](#confex)
        - [Für E-mail Pro](#confemp)
    - [API - Die verschiedenen DKIM-Zustände](#dkim-status)
    - [API - Aktivieren oder Wechseln eines DKIM-Selektors](#enable-switch)
    - [API - Deaktivieren und Löschen des DKIM](#disable-delete)



106 Um zu verstehen, warum DKIM Ihre E-Mail-Austauschvorgänge sichert, ist es wichtig zu verstehen, wie es funktioniert. DKIM verwendet „**Hashing**“ und „**asymmetrisches Verschlüsselung**“, um eine sichere Signatur zu erstellen. Die **E-Mail-Plattform** und die **DNS-Zone** Ihres Domainnamens helfen dabei, die DKIM-Informationen an Ihre Empfänger weiterzugeben.

108 /// details | Das Hashing <a name="hash"></a>


118 ///

120/// details | Asymmetrische Verschlüsselung <a name="encrypt"></a>

136 ///

138 /// details | Wie werden Hashing und asymmetrische Verschlüsselung für DKIM verwendet? <a name="encrypt-and-hash"></a>

144 ///

146 /// details | Warum ist es notwendig, die DNS-Server zu konfigurieren? <a name="dns-and-dkim"></a>

150 ///

152 /// details | Was ist ein DKIM-Selektor? <a name="selector"></a>

165 ///

167 /// details | Beispiel für eine per DKIM gesendete E-Mail <a name="example"></a>

177 ///

179 ### DKIM automatisch für ein E-Mail-Angebot von OVHcloud konfigurieren <a name="auto-dkim"></a>

Die automatische DKIM-Konfiguration ist für alle unsere E-Mail-Angebote verfügbar:

- MX Plan inklusive [Cloud-Web-Hosting](/links/web/hosting), ein [kostenloses Hosting 100M](/links/web/domains-free-hosting) oder separat bestellt.
- [Exchange](/links/web/emails).
- [E-mail Pro](/links/web/email-pro).
- [Zimbra](/links/web/zimbra).

Wenn Sie Ihren Domainnamen auf einer E-Mail-Lösung von OVHcloud konfigurieren, wird die automatische DKIM-Konfiguration standardmäßig angeboten und durchgeführt, sofern Sie sie nicht deaktivieren.

Wenn DKIM nicht aktiviert wurde, als Sie einen Domainnamen zu Ihrer E-Mail-Plattform hinzugefügt haben, müssen Sie den automatischen Konfigurationsprozess über das Kundencenter starten.

Klicken Sie auf das unten stehende Registerblatt, das zu Ihrem Angebot passt.

> [!tabs]
> **MX Plan**
>>
>> 1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie auf `MX Plan`{.action}.
>> 1. Wählen Sie den betreffenden Domainnamen aus.
>> 1. Gehen Sie schließlich zum Registerblatt `Allgemeine Informationen`{.action}.
>>
>> Im Bereich **Allgemeine Informationen** können Sie beobachten, dass die Schaltfläche `DKIM` rot unter der Bezeichnung **Diagnose** ist.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Um DKIM zu aktivieren, klicken Sie einfach auf die rote Schaltfläche `DKIM` und dann auf `Bestätigen`{.action} im Aktivierungsdialog, der angezeigt wird.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> Falls Ihr Domainname nicht im gleichen OVHcloud Kundencenter wie Ihre E-Mail-Plattform verwaltet wird oder außerhalb von OVHcloud registriert ist, erhalten Sie das folgende Fenster:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> Dieses Fenster fordert Sie dazu auf, zwei CNAME-Werte in der DNS-Zone des Domainnamens einzugeben, wodurch dieser Domainname mit den DKIM-Selektoren Ihres E-Mail-Dienstes verknüpft wird. Sie müssen diese Werte eingeben und sicherstellen, dass sie verbreitet wurden, bevor Sie auf `Aktivieren`{.action} klicken.
>>
> **Exchange**
>>
>> 1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie im Bereich `MICROSOFT` auf `Exchange`{.action}.
>> 1. Wählen Sie die betreffende Plattform aus.
>> 1. Gehen Sie schließlich zum Registerblatt `Zugeordnete Domains`{.action}.
>>
>> Rechts neben dem betreffenden Domainnamen können Sie beobachten, dass die Schaltfläche `DKIM` rot ist.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Um DKIM zu aktivieren, klicken Sie einfach auf die rote Schaltfläche `DKIM` und dann auf `Bestätigen`{.action} im Aktivierungsdialog, der angezeigt wird.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie auf `Email Pro`{.action}.
>> 1. Wählen Sie die betreffende Plattform aus.
>> 1. Gehen Sie schließlich zum Registerblatt `Zugeordnete Domains`{.action}.
>>
>> Rechts neben dem betreffenden Domainnamen können Sie beobachten, dass die Schaltfläche `DKIM` rot ist.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Um DKIM zu aktivieren, klicken Sie einfach auf die rote Schaltfläche `DKIM` und dann auf `Bestätigen`{.action} im Aktivierungsdialog, der angezeigt wird.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **Zimbra**
>>
>> 1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie auf `Zimbra Mail`{.action}.
>> 1. Gehen Sie schließlich zum Registerblatt `Domain`{.action}.
>> 1. Klicken Sie rechts neben der betreffenden Domain auf `⁝`{.action}, und dann auf `Diagnostics`{.action}.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/access.png){.thumbnail .w-400 .h-600}
>>
>> Rechts neben der Bezeichnung `DKIM` auf dem entsprechenden Registerblatt sollten Sie eine Warnung sehen, die anzeigt, dass DKIM fehlschlägt. Klicken Sie auf das Registerblatt `DKIM`{.action}, um den Status der DKIM-Konfiguration anzuzeigen. Um den Fehler zu beheben, müssen Sie zwei DNS-Einträge vom Typ CNAME in der DNS-Zone des zugeordneten Domainnamens hinzufügen oder ändern, basierend auf den Informationen, die in diesem Registerblatt sichtbar sind.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/dkim-cname-conf.png){.thumbnail .w-400 .h-600}
>>
>> > [!primary]
>> > **Tipp zur Erstellung eines CNAME-Eintrags**
>> >
>> > Melden Sie sich im [OVHcloud Kundencenter](/links/manager) an, in dem der Domainname Ihres E-Mail-Dienstes gehostet wird. Gehen Sie in den Bereich `Web Cloud`{.action}, klicken Sie auf `Domainnamen`{.action} in der linken Spalte und wählen Sie den betreffenden Domainnamen aus.<br>
>> > Wählen Sie das Registerblatt `DNS-Zone`{.action} und klicken Sie auf `Eintrag hinzufügen`{.action} im angezeigten Fenster. Wählen Sie `CNAME` und füllen Sie die Werte entsprechend den von Ihnen notierten Werten aus.

Um DKIM zu aktivieren, klicken Sie einfach auf die rote Schaltfläche `DKIM` und dann auf `Bestätigen`{.action} im Aktivierungsdialog, der angezeigt wird.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}

Die automatische DKIM-Aktivierung dauert zwischen 30 Minuten und maximal 24 Stunden. Um zu prüfen, ob Ihr DKIM funktioniert, kehren Sie einfach in den Bereich zur Domainverwaltung zurück, der in den oben genannten Registerblättern erwähnt wird, und stellen Sie sicher, dass die Schaltfläche `DKIM` grün ist oder, bei einer Zimbra-Angebot, dass das Registerblatt `DKIM` keine Warnung mehr anzeigt.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto03.png){.thumbnail .w-400 .h-600}

Falls nach 24 Stunden die Schaltfläche `DKIM` immer noch rot ist, konsultieren Sie den Abschnitt [„Warum ist DKIM nicht funktional und erscheint rot im Kundencenter?“](#reddkim) in diesem Leitfaden.

### DKIM per API für eine E-Mail von OVHcloud konfigurieren <a name="internal-dkim"></a>

Für eine Exchange- oder E-mail Pro-Plattform müssen Sie zunächst die Referenz Ihrer Plattform abrufen, um Ihren DKIM zu konfigurieren.

Klicken Sie auf das unten stehende Registerblatt, das zu Ihrem Angebot passt.

> [!tabs]
> **Exchange**
>>
>> 1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie im Bereich `MICROSOFT` auf `Exchange`{.action}.
>> 1. Wählen Sie die betreffende Plattform aus.
>>
>> Standardmäßig entspricht der Name Ihrer Plattform ihrer Referenz oder diese ist unter dem Namen sichtbar, den Sie ihr gegeben haben (siehe Bild unten).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/general-information/dns-dkim-platform-exchange.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie auf `Email Pro`{.action}.
>> 1. Wählen Sie die betreffende Plattform aus.
>>
>> Standardmäßig entspricht der Name Ihrer Plattform ihrer Referenz oder diese ist unter dem Namen sichtbar, den Sie ihr gegeben haben (siehe Bild unten).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/email-pro/general-information/dns-dkim-platform-emailpro.png){.thumbnail .w-400 .h-600}

Stellen Sie außerdem sicher, dass der Domainname, den Sie für Ihre E-Mails verwenden möchten, in der Registerkarte `Zugeordnete Domains`{.action} aktiv ist.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dns-dkim-domain.png){.thumbnail .w-400 .h-600}

#### API - DKIM vollständig konfigurieren <a name="firststep"></a>

Um DKIM zu konfigurieren, besuchen Sie die [OVHcloud API-Seite](/links/console) und melden Sie sich an:

1. Klicken Sie auf `Authentication`{.action} oben links.
1. Klicken Sie anschließend auf `Login with OVHcloud SSO`{.action}.
1. Geben Sie Ihre OVHcloud-Anmeldeinformationen ein.
1. Klicken Sie auf den Button `Authorize`{.action}, um die API-Aufrufe von dieser Website zu autorisieren.

> [!primary]
>
> Nutzen Sie unseren Leitfaden „[Erste Schritte mit den OVHcloud APIs](/pages/manage_and_operate/api/first-steps)“, falls Sie die APIs noch nie verwendet haben.

Gehen Sie zu dem Abschnitt `/email/domain/` (Angebote MX Plan und Zimbra), `/email/exchange` (Angebot Exchange) oder `/email/pro` (Angebot E-mail Pro) der APIs und geben Sie „dkim“ in das Feld `Filter` ein, um nur die API-Funktionen anzuzeigen, die sich auf DKIM beziehen.

Klicken Sie auf das Registerblatt, das zu Ihrem Angebot passt:

> [!tabs]
> **MX Plan und Zimbra**
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

##### **Für MX Plan und Zimbra** <a name="confemail"></a>

Folgen Sie den **5 Schritten**, indem Sie nacheinander auf die folgenden 5 Registerblätter klicken:

> [!tabs]
> **1. DKIM auf Ihrem Domainnamen aktivieren**
>> Um DKIM auf Ihrem Domainnamen zu aktivieren, verwenden Sie den folgenden API-Aufruf:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : Geben Sie den Domainnamen ein, der mit Ihrem E-Mail-Dienst verknüpft ist, auf dem Sie DKIM aktivieren möchten.
>>
>> Klicken Sie auf `EXECUTE`{.action}, um die Aktivierung zu starten.<br>
>>
>> *Beispiel für das Ergebnis:*
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
>> Sie sollten das gleiche Ergebnis wie im obigen Beispiel erhalten, mit der Angabe `"status": "todo"`, was bedeutet, dass DKIM installiert wird.
>>
> **2. Status der DKIM-Operation prüfen**
>> Nachdem Sie den Aktivierungsprozess für DKIM gestartet haben, überwachen Sie den Installationsstatus, um sicherzustellen, dass die Installation abgeschlossen ist, oder um die DNS-Einträge abzurufen, falls Ihre DNS-Zone außerhalb Ihres OVHcloud Kundencenters verwaltet wird.<br>
>>.
>> <br>
>> Dazu verwenden Sie den folgenden API-Aufruf:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : Geben Sie den Domainnamen ein, der mit Ihrem E-Mail-Dienst verknüpft ist.<br>
>> <br>
>> Klicken Sie auf `EXECUTE`{.action}, um das Ergebnis anzuzeigen.<br>
>>
>> *Beispiel für das Ergebnis :*
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
>> Im obigen Beispiel bedeutet die letzte Zeile `"status": "modifying"`, dass die Konfiguration läuft. Warten Sie etwa **10 Minuten** und starten Sie den API-Aufruf erneut.
>>
>> - wenn der Wert `"status": "enabled"` ist, ist Ihre Konfiguration abgeschlossen und funktional.
>> - wenn der Wert `"status": "disabled"` ist, muss Ihre Konfiguration manuell abgeschlossen werden, gehen Sie zum nächsten Schritt über.
>>
> **3. DNS-Eintrag abrufen**
>> Sie müssen die DNS-Zone Ihres Domainnamens manuell konfigurieren **in folgenden Fällen** :
>>
>> - Ihr E-Mail-Dienst ist mit einem Domainnamen verknüpft, der in einem anderen OVHcloud-Kundenkonto verwaltet wird ;
>> - Ihr E-Mail-Dienst ist mit einem Domainnamen verknüpft, der in einem anderen Registrierungsamt verwaltet wird.
>>
>> Um Ihre DNS-Zone zu konfigurieren, müssen Sie die Werte des DNS-Eintrags **der beiden Selektoren** abrufen. Dazu verwenden Sie das Ergebnis des API-Aufrufs des vorherigen Schritts :
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : Geben Sie den Domainnamen ein, der mit Ihrem E-Mail-Dienst verknüpft ist.
>>
>> Klicken Sie auf `EXECUTE`{.action}, um das Ergebnis anzuzeigen.
>>
>> *Beispiel für das Ergebnis :*
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
>> Die Werte `"status": "toSet"` und `"status": "disabled"` bedeuten, dass die CNAME-Einträge konfiguriert werden müssen. Speichern Sie die beiden `cname`-Werte in einer Textdatei und gehen Sie zum nächsten Schritt über.
>>
> **4. DNS-Eintrag konfigurieren**
>> Melden Sie sich im [OVHcloud Kundencenter](/links/manager) an, in dem der Domainname Ihres E-Mail-Dienstes gehostet wird, klicken Sie im Tab `Web Cloud`{.action} auf `Noms de domaine`{.action} in der linken Spalte und wählen Sie den betreffenden Domainnamen aus.<br>
>> Gehen Sie zum Tab `Zone DNS`{.action} und klicken Sie auf `Ajouter une entrée`{.action} im angezeigten Fenster. Wählen Sie `CNAME` und füllen Sie die Felder entsprechend den von Ihnen notierten Werten aus.
>>
>> Wenn man die Werte des Beispiels im Schritt "**3. DNS-Eintrag abrufen**" analysiert :
>>
>> - `ovhmo3456789-selector1._domainkey.mydomain.ovh` entspricht dem Subdomain des CNAME-Eintrags. Man behält nur `ovhmo3456789-selector1._domainkey`, da der `.mydomain.ovh` bereits vorbelegt ist. <br>
>> - `ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net."` entspricht dem Ziel des Eintrags. Man muss den Punkt am Ende beibehalten, um den Wert abzuschließen.<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api022.png){.thumbnail .w-400 .h-600}
>>
>> Nachdem Sie die Werte eingegeben haben, klicken Sie auf `Suivant`{.action} und dann auf `Valider`{.action}.
>>
>> > [!primary]
>> >
>> > **Wiederholen Sie diese Operation für den zweiten Selektor.**
>>
>> Wenn Sie Ihre DNS-Zone in einer externen Schnittstelle außerhalb von OVHcloud konfigurieren, muss Ihr CNAME-Eintrag folgende Form haben :
>>
>> ```console
>> ovhmo3456789-selector1._domainkey IN CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Vergessen Sie nicht, dass eine Änderung in einer DNS-Zone einer Verbreitungszeit unterliegt. Diese ist in der Regel kurz, kann aber bis zu 24 Stunden dauern.
>>
> **5. DKIM aktivieren**
>>
>> Nachdem sich Ihre DNS-Konfiguration verbreitet hat, verwenden Sie erneut den folgenden API-Aufruf, um DKIM zu aktivieren:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : Geben Sie den Domainnamen ein, der mit Ihrem E-Mail-Dienst verknüpft ist, auf dem Sie DKIM aktivieren möchten.
>>
>> Klicken Sie auf `EXECUTE`{.action}, um die Aktivierung zu starten.<br>
>>
>> *Beispiel für das Ergebnis :*
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
>> - Wenn Sie die Werte `"status": "set"` auf beiden Selektoren feststellen, bedeutet das, dass diese korrekt konfiguriert sind.
>> - Wenn Sie die Werte `"status": "toSet"` auf beiden Selektoren feststellen, bedeutet das, dass Ihre DNS-Änderungen nicht sichtbar sind. Gehen Sie zum Tab « **4. DNS-Eintrag konfigurieren** » zurück.
>> - Wenn Sie die Werte `"status": "toFix"` auf beiden Selektoren feststellen, bedeutet das, dass die CNAME-Einträge in der DNS-Zone Ihres Domainnamens erkannt wurden, aber die Werte falsch sind. Gehen Sie zum Tab « **4. DNS-Eintrag konfigurieren** » zurück.
>>
>> > [!success]
>> >
>> > Sie haben nun alle Schritte durchgeführt, um DKIM zu aktivieren. Um sicherzustellen, dass er aktiviert ist, prüfen Sie seinen Status, indem Sie zum Tab der Schritt « **2. Status der DKIM-Operation prüfen** » zurückkehren, um zu überprüfen, dass der Wert `status:` auf `enabled` steht. Wenn das der Fall ist, ist Ihr DKIM jetzt aktiv.
>>

##### **Für Exchange** <a name="confex"></a>

Folgen Sie den **5 Schritten** unten, indem Sie auf jeden Tab klicken.

> [!tabs]
> **1. Liste der Selektoren**
>> Bevor Sie einen der Selektoren für Ihren Domainnamen erstellen, müssen Sie den Namen ermitteln, der Ihnen automatisch von der Exchange-Plattform zugewiesen wird.<br>
>> <br>
>> Dazu verwenden Sie den folgenden API-Aufruf:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkimSelector
>> >
>> <br>
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer Exchange-Plattform verknüpft ist, auf dem Sie DKIM aktivieren möchten. <br>
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint. <br>
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint. <br>
>>
>> *Beispiel für das Ergebnis:*
>>
>> ```console
>> "ovhex123456-selector1"
>> "ovhex123456-selector2"
>> ```
>>
> **2. Erstellen eines Selektors**
>> Sie erstellen nun einen Selektor, generieren das zugehörige Schlüsselpaar und den zugeordneten DNS-Eintrag für den Domainnamen.<br>
>> <br>
>> Dazu verwenden Sie den folgenden API-Aufruf:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer Exchange-Plattform verknüpft ist, auf dem Sie DKIM aktivieren möchten.
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint.
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint.
>> - `"selectorName"` : Im Tab **BEISPIEL** der Abschnitt **ANFORDERUNGSTEXT**, geben Sie den Namen eines Selektors ein, den Sie im vorherigen Schritt erfasst haben (z. B. "ovhex123456-selector1").
>>
>> *Beispiel für die Eingabe:*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhex123456-selector1"
>> }
>> ```
>>
>> Klicken Sie auf `AUSFÜHREN`{.action}, um die Erstellung des Selektors zu starten.<br>
>>
>> > [!primary]
>> >
>> > Wir empfehlen Ihnen, diese Operation zweimal durchzuführen, für jeden zuvor aufgelisteten Selektor. Der zweite Selektor ermöglicht es Ihnen, das Schlüsselpaar zu wechseln, wenn dies erforderlich ist. Wir empfehlen Ihnen, unseren Use Case [„Wie man sein DKIM-Schlüsselpaar wechselt“](#2selectors) zu konsultieren, wenn Sie auf den zweiten Selektor wechseln möchten.
>> <br>
>>
>> *Beispiel für das Ergebnis:*
>>
>> ```console
>> status: "todo",
>> function: "addExchangeDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Abrufen des DNS-Eintrags**
>> Sie müssen die DNS-Zone Ihres Domainnamens manuell konfigurieren, **in den folgenden Fällen**:
>>
>> - Ihre Exchange-Plattform ist mit einem Domainnamen verknüpft, der in einem anderen OVHcloud-Kundenkonto verwaltet wird;<br>
>> - Ihre Exchange-Plattform ist mit einem Domainnamen verknüpft, der in einem anderen Registrierungsamt verwaltet wird;<br>
>>
>> Um Ihre DNS-Zone zu konfigurieren, müssen Sie die Werte des DNS-Eintrags **für jeden Selektor abrufen, wenn Sie zwei erstellt haben**. Dazu verwenden Sie den folgenden API-Aufruf:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer Exchange-Plattform verknüpft ist, auf dem Sie DKIM konfigurieren möchten.
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint.
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint.
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie im vorherigen Schritt erstellt haben.
>>
>> *Beispiel für das Ergebnis:*
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
>> Speichern Sie die Werte `customerRecord` und `targetRecord` in einer Textdatei. Gehen Sie zum nächsten Schritt über.
>>
>> > [!primary]
>> >
>> > Es ist möglich, dass der `status:` auf `todo` steht, dies hat keinen Einfluss auf die Konfiguration Ihrer DNS-Zone.
>>
> **4. Konfigurieren des DNS-Eintrags**
>> Melden Sie sich im [OVHcloud Kundencenter](/links/manager) an, in dem der Domainname Ihrer Exchange-Plattform gehostet wird, klicken Sie im Tab `Web Cloud`{.action} auf `Domainnamen`{.action} in der linken Spalte und wählen Sie den entsprechenden Domainnamen aus.<br>
>> Gehen Sie zum Tab `DNS-Zone`{.action} und klicken Sie auf `Eintrag hinzufügen`{.action} im angezeigten Fenster. Wählen Sie `CNAME` und füllen Sie die Felder entsprechend den von Ihnen erfassten Werten aus.<br>
>>
>> Wenn wir die Werte des Beispiels aus dem Schritt "**3. Abrufen des DNS-Eintrags**" verwenden:
>>
>> - `customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"` entspricht dem Unterdomain des CNAME-Eintrags. Wir behalten nur `ovhex123456-selector1._domainkey` bei, da `.mydomain.ovh` bereits vorbelegt ist. <br>
>> - `targetRecord: "ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` entspricht der Zieladresse des Eintrags. Wir fügen am Ende einen Punkt hinzu, um den Wert abzuschließen. Das ergibt `ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Nachdem Sie die Werte eingegeben haben, klicken Sie auf `Weiter`{.action} und dann auf `Bestätigen`{.action}.<br>
>>
>> **Wiederholen Sie diese Operation für den zweiten Selektor, wenn Sie ihn erstellt haben.**<br>
>>
>> Wenn Sie Ihre DNS-Zone in einer dritten, nicht OVHcloud-basierten Schnittstelle konfigurieren, muss Ihr CNAME-Eintrag folgende Form haben:
>>
>> ```console
>> ovhex123456-selector1._domainkey IN CNAME ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Vergessen Sie nicht, dass eine Änderung in einer DNS-Zone einer Verbreitungszeit unterliegt. Diese ist in der Regel kurz, kann aber bis zu 24 Stunden dauern.
>>
> **5. Aktivierung von DKIM**
>> > [!warning]
>> >
>> > Überprüfen Sie in der Abschnitt „[API - Die verschiedenen Zustände von DKIM](#dkim-status)“ dieses Leitfadens, ob der Wert `status:` auf `ready` steht, bevor Sie DKIM aktivieren können.
>>
>> Um DKIM zu aktivieren, verwenden Sie den folgenden API-Aufruf:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer Exchange-Plattform verknüpft ist, auf dem Sie DKIM aktivieren möchten.
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint.
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form "hosted-zz111111-1" oder "private-zz111111-1" erscheint.
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie erstellt haben.
>>
>> *Beispiel für das Ergebnis:*
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
>> > Sie haben nun alle erforderlichen Schritte zur Aktivierung von DKIM durchgeführt. Um sicherzustellen, dass dieser aktiviert ist, konsultieren Sie die Abschnitt „[API - Die verschiedenen Zustände von DKIM](#dkim-status)“ dieses Leitfadens, um zu überprüfen, ob der Wert `status:` auf `inProduction` steht. Wenn dies der Fall ist, ist Ihr DKIM nun aktiv.<br><br> **Wenn Sie zwei Selektoren erstellt haben**, sollte der zweite Selektor den Status `status: "ready"` haben.
>>

##### **Für E-Mail Pro** <a name="confemp"></a>

Führen Sie die folgenden **5 Schritte** aus, indem Sie auf jeden der Tabs klicken.

> [!tabs]
> **1. Liste der Selektoren**
>> Vor dem Erstellen eines der Selektoren für Ihren Domainnamen müssen Sie den Namen ermitteln, der Ihnen automatisch von der E-Mail Pro-Plattform zugewiesen wird.<br>
>> <br>
>> Dazu verwenden Sie den folgenden API-Aufruf:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim
>> <br>
>>
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form „emailpro-zz111111-1“ erscheint. <br>
>> - `domainName` : Geben Sie den Domainnamen ein, der an Ihre E-Mail Pro-Plattform angehängt ist, auf dem Sie DKIM aktivieren möchten. <br>
>>
>> *Beispiel für das Ergebnis :*
>>
>> ```console
>> "ovhemp123456-selector1"
>> "ovhemp123456-selector2"
>> ```
>>
> **2. Erstellen eines Selektors**
>> Sie erstellen nun einen Selektor, generieren sein Schlüsselpaar und den zugehörigen DNS-Eintrag für den Domainnamen.<br>
>>
>> > [!primary]
>> >
>> > Wir empfehlen Ihnen, diese Operation zweimal für jeden zuvor aufgelisteten Selektor durchzuführen. Der zweite Selektor ermöglicht Ihnen, das Schlüsselpaar zu wechseln, wenn dies erforderlich ist. Wir empfehlen Ihnen, unser Use Case [„Wie man sein DKIM-Schlüsselpaar wechselt“](#2selectors) zu konsultieren.
>> <br>
>> Dazu verwenden Sie den folgenden API-Aufruf:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der an Ihre E-Mail Pro-Plattform angehängt ist, auf dem Sie DKIM aktivieren möchten.
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form „emailpro-zz111111-1“ erscheint. <br>
>> - `"selectorName"` : Im Tab **BEISPIEL** des Abschnitts **ANFORDERUNGSTEXT**, geben Sie den Namen eines Selektors ein, den Sie in der vorherigen Etappe erfasst haben. (Beispiel: „ovhemp123456-selector1“).
>>
>> *Beispiel für die Eingabe :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhemp123456-selector1"
>> }
>> ```
>>
>> Klicken Sie auf `AUSFÜHREN`{.action}, um die Erstellung des Selektors zu starten.<br>
>>
>> > [!primary]
>> >
>> > Wir empfehlen Ihnen, diese Operation zweimal für jeden zuvor aufgelisteten Selektor durchzuführen. Der zweite Selektor ermöglicht Ihnen, das Schlüsselpaar zu wechseln, wenn dies erforderlich ist. Wir empfehlen Ihnen, unser Use Case [„Wie man sein DKIM-Schlüsselpaar wechselt“](#2selectors) zu konsultieren, wenn Sie auf den zweiten Selektor wechseln möchten.
>>
>> *Beispiel für das Ergebnis :*
>>
>> ```console
>> status: "todo",
>> function: "addDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Abrufen des DNS-Eintrags**
>> Sie müssen die DNS-Zone Ihres Domainnamens manuell konfigurieren **in den folgenden Fällen** :
>>
>> - Ihre E-Mail Pro-Plattform ist an einen Domainnamen gebunden, der in einem anderen OVHcloud-Kundenkonto verwaltet wird ;<br>
>> - Ihre E-Mail Pro-Plattform ist an einen Domainnamen gebunden, der in einem anderen Registrierungsamt verwaltet wird ;<br>
>>
>> Um Ihre DNS-Zone zu konfigurieren, müssen Sie die Werte des DNS-Eintrags **für jeden Selektor abrufen, wenn Sie zwei erstellt haben**. Dazu verwenden Sie den folgenden API-Aufruf :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form „emailpro-zz111111-1“ erscheint.
>> - `domainName` : Geben Sie den Domainnamen ein, der an Ihre E-Mail Pro-Plattform angehängt ist, auf dem Sie DKIM konfigurieren möchten.
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie in der vorherigen Etappe erstellt haben.
>>
>> *Beispiel für das Ergebnis :*
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
>> Speichern Sie die Werte `customerRecord` und `targetRecord` in einer Textdatei. Gehen Sie zur nächsten Etappe über.
>>
>> > [!primary]
>> >
>> > Es ist möglich, dass der `status:` auf `todo` steht, dies hat keinen Einfluss auf die Konfiguration Ihrer DNS-Zone.
>>
> **4. Konfigurieren des DNS-Eintrags**
>> Melden Sie sich im [OVHcloud Kundencenter](/links/manager) an, in dem der Domainname Ihrer E-Mail Pro-Plattform gehostet ist. Klicken Sie im Tab `Web Cloud`{.action} auf `Domainnamen`{.action} in der linken Spalte und wählen Sie den betreffenden Domainnamen aus.<br>
>> Gehen Sie zum Tab `DNS-Zone`{.action} und klicken Sie auf `Eintrag hinzufügen`{.action} in dem sich öffnenden Fenster. Wählen Sie `CNAME` und füllen Sie die Felder entsprechend den Werten aus.<br>
>>
>> Wenn Sie die Werte des Beispiels aus der Etappe "**3. Abrufen des DNS-Eintrags**" verwenden:
>>
>> - `customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"` entspricht dem Subdomain des CNAME-Eintrags. Sie behalten nur `ovhemp123456-selector1._domainkey`, da der `.mydomain.ovh` bereits vorbelegt ist. <br>
>> - `targetRecord: "ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` entspricht dem Ziel des Eintrags. Fügen Sie am Ende einen Punkt hinzu, um den Wert abzuschließen. Das ergibt `ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Nachdem Sie die Werte eingegeben haben, klicken Sie auf `Weiter`{.action} und dann auf `Bestätigen`{.action}.<br>
>>
>> **Wiederholen Sie diese Operation für den zweiten Selektor, wenn Sie ihn erstellt haben.**<br>
>>
>> Wenn Sie Ihre DNS-Zone in einer externen Schnittstelle außerhalb von OVHcloud konfigurieren, muss Ihr CNAME-Eintrag folgende Form haben :
>>
>> ```console
>> ovhemp123456-selector1._domainkey IN CNAME ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Vergessen Sie nicht, dass eine Änderung in einer DNS-Zone einer Verbreitungszeit unterliegt. Diese ist in der Regel kurz, kann aber bis zu 24 Stunden dauern.
>>
> **5. Aktivierung des DKIM**
>> > [!warning]
>> >
>> > Im Abschnitt „[API - Die verschiedenen Zustände des DKIM](#dkim-status)“ dieses Leitfadens überprüfen Sie, dass der Wert `status:` auf `ready` steht, bevor Sie DKIM aktivieren können.
>>
>> Um DKIM zu aktivieren, verwenden Sie den folgenden API-Aufruf :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form „emailpro-zz111111-1“ erscheint. 
>> - `domainName` : Geben Sie den Domainnamen ein, der an Ihre E-Mail Pro-Plattform angehängt ist, auf dem Sie DKIM aktivieren möchten.
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie erstellt haben.
>>
>> *Beispiel für das Ergebnis :*
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
>> > Sie haben nun alle Manipulationen durchgeführt, um DKIM zu aktivieren. Um sicherzustellen, dass er aktiviert ist, konsultieren Sie den Abschnitt „[API - Die verschiedenen Zustände des DKIM](#dkim-status)“ dieses Leitfadens, um zu überprüfen, dass der Wert `status:` auf `inProduction` steht. Wenn dies der Fall ist, ist Ihr DKIM nun aktiv.<br><br> **Wenn Sie zwei Selektoren erstellt haben**, sollte der zweite Selektor auf `status: "ready"` stehen.
>>

#### API - Die verschiedenen Zustände des DKIM <a name="dkim-status"></a>

Wählen Sie das betroffene E-Mail-Angebot in den folgenden Tabs aus :

> [!tabs]
> **MX Plan und Zimbra**
>> Während Ihrer Operationen auf dem DKIM Ihrer E-Mail-Plattform verwenden Sie den folgenden API-Aufruf, um den aktuellen Zustand des DKIM zu prüfen.
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>>
>> - `domain` : Geben Sie den Domainnamen ein, der an Ihren E-Mail-Service angehängt ist, auf dem DKIM vorhanden sein muss.
>>
>> Schauen Sie sich anschließend den allgemeinen Wert `status:` im Ergebnis an :
>>
>> - `disabled` : DKIM ist deaktiviert, er wurde noch nicht konfiguriert oder wurde über die API deaktiviert. <br>
>> - `modifying` : Die Konfiguration des DKIM ist in Bearbeitung, es ist erforderlich, bis zum Ende des Prozesses zu warten.<br>
>> - `toConfigure` : Die Konfiguration des DKIM wartet auf die DNS-Parameter des Domainnamens. Sie müssen die DNS-Einträge manuell in der Zone des Domainnamens eintragen. Dazu beziehen Sie sich auf [Schritt 4 von „die vollständige Konfiguration des DKIM für MX Plan und Zimbra“](#confemail).<br>
>> - `enabled` : DKIM ist konfiguriert und funktioniert.<br>
>> - `error` : Der Installationsprozess hat einen Fehler erkannt. Wir empfehlen Ihnen, ein [Support-Ticket zu öffnen](https://help.ovhcloud.com/csm?id=csm_get_help) und den betroffenen Domainnamen anzugeben.<br>
>>
>> Auf Ebene der Selektoren gibt es ebenfalls drei mögliche Zustände:
>>
>> - `set` : Der Selektor ist korrekt konfiguriert und aktiv.
>> - `toSet` : Der Selektor ist nicht in der DNS-Zone des Domainnamens konfiguriert. Beziehen Sie sich auf [Schritt 4 von „die vollständige Konfiguration des DKIM für MX Plan und Zimbra“](#confemail).
>> - `toFix` : Der Selektor ist zwar in der DNS-Zone des Domainnamens konfiguriert, die Werte sind jedoch falsch. Beziehen Sie sich auf [Schritt 4 von „die vollständige Konfiguration des DKIM für MX Plan und Zimbra“](#confemail).
>>
> **Exchange**
>> Während Ihrer Operationen auf dem DKIM Ihrer Exchange-Plattform verwenden Sie den folgenden API-Aufruf, um den aktuellen Zustand des DKIM zu prüfen.
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der an Ihre Exchange-Plattform angehängt ist, auf dem DKIM vorhanden sein muss. <br>
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form „hosted-zz111111-1“ oder „private-zz111111-1“ erscheint. <br>
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form „hosted-zz111111-1“ oder „private-zz111111-1“ erscheint. <br>
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie erstellt haben. <br>
>>
>> Schauen Sie sich anschließend den Wert `status:` im Ergebnis an :
>>
>> - `todo` : Die Aufgabe wurde initialisiert, sie wird starten. <br>
>> - `WaitingRecord` : Die DNS-Einträge warten auf Konfiguration oder befinden sich in der Validierung in der DNS-Zone des Domainnamens. Eine automatische regelmäßige Prüfung wird durchgeführt, um zu sehen, ob der DNS-Eintrag vorhanden und korrekt eingegeben ist.
>> - `ready` : Die DNS-Einträge sind in der Zone vorhanden. DKIM kann jetzt aktiviert werden. <br>
>> - `inProduction` : DKIM ist korrekt konfiguriert und aktiviert, er ist daher vollständig betriebsbereit. <br>
>> - `disabling` : DKIM wird deaktiviert. <br>
>> - `deleting` : DKIM wird gelöscht. <br>
>>
>> Wenn Sie die folgende Fehlermeldung erhalten, wenn Sie den API-Aufruf starten, bedeutet dies, dass der Selektor nicht existiert oder gelöscht wurde. Sie müssen ihn erstellen.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>
> **E-Mail Pro**
>> Während Ihrer Operationen auf dem DKIM Ihrer E-Mail Pro-Plattform verwenden Sie den folgenden API-Aufruf, um den aktuellen Zustand des DKIM zu prüfen.
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form „emailpro-zz111111-1“ erscheint. <br>
>> - `domainName` : Geben Sie den Domainnamen ein, der an Ihre E-Mail Pro-Plattform angehängt ist, auf dem DKIM vorhanden sein muss. <br>
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie erstellt haben. <br>
>>
>> Schauen Sie sich anschließend den Wert `status:` im Ergebnis an :
>>
>> - `todo` : Die Aufgabe wurde initialisiert, sie wird starten. <br>
>> -

> [!primary]
>
> Beim Rotieren eines DKIM-Selektors können Sie direkt den zweiten Selektor aktivieren, den Sie erstellt haben, um auf diesen umzuschalten, während der erste Selektor weiterhin aktiv bleibt, bis alle mit diesem versandten E-Mails ordnungsgemäß vom Empfänger analysiert wurden.

#### API - DKIM deaktivieren und löschen <a name="disable-switch"></a>

> [!warning]
>
> **Für die Angebote Exchange und E-Mail Pro** <br>
>
> Der DKIM-Selektor muss den Status `inProduction` oder `ready` haben, bevor er deaktiviert werden kann.

Wählen Sie das E-Mail-Angebot aus, das in den folgenden Registerkarten behandelt wird:

> [!tabs]
> **MX Plan und Zimbra**
>> Wenn Sie DKIM deaktivieren möchten, ohne die Selektoren und ihre Schlüsselpaare zu löschen, verwenden Sie den folgenden API-Aufruf:
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/disable
>> <br>
>>
>> - `domain` : Geben Sie den Domainnamen ein, der mit Ihrem E-Mail-Dienst verknüpft ist, auf dem DKIM aktiviert sein soll. <br>
>>
>> *Beispiel für das Ergebnis:*
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
>> Wenn Sie DKIM deaktivieren möchten, ohne den Selektor und sein Schlüsselpaar zu löschen, verwenden Sie den folgenden API-Aufruf:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer Exchange-Plattform verknüpft ist. <br>
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form « hosted-zz111111-1 » oder « private-zz111111-1 » erscheint. <br>
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form « hosted-zz111111-1 » oder « private-zz111111-1 » erscheint. <br>
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie deaktivieren möchten. <br>
>>
>> Wenn Sie den DKIM-Selektor und sein Schlüsselpaar löschen möchten, verwenden Sie den folgenden API-Aufruf:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange DELETE /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer Exchange-Plattform verknüpft ist. <br>
>> - `exchangeService` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form « hosted-zz111111-1 » oder « private-zz111111-1 » erscheint. <br>
>> - `organizationName` : Geben Sie den Namen Ihrer Exchange-Plattform ein, der in der Form « hosted-zz111111-1 » oder « private-zz111111-1 » erscheint. <br>
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie löschen möchten. <br>
>>
> **E-Mail Pro**
>> Wenn Sie DKIM deaktivieren möchten, ohne den Selektor und sein Schlüsselpaar zu löschen, verwenden Sie den folgenden API-Aufruf:
>> 
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer E-Mail Pro-Plattform verknüpft ist. <br>
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie deaktivieren möchten. <br>
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form « emailpro-zz111111-1 » erscheint. <br>
>>
>> Wenn Sie den DKIM-Selektor und sein Schlüsselpaar löschen möchten, verwenden Sie den folgenden API-Aufruf:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro DELETE /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : Geben Sie den Domainnamen ein, der mit Ihrer E-Mail Pro-Plattform verknüpft ist. <br>
>> - `selectorName` : Geben Sie den Namen des Selektors ein, den Sie löschen möchten. <br>
>> - `service` : Geben Sie den Namen Ihrer E-Mail Pro-Plattform ein, der in der Form « emailpro-zz111111-1 » erscheint. <br>
>>

### DKIM für ein E-Mail-Angebot außerhalb Ihres OVHcloud-Kontos konfigurieren <a name="external-dkim"></a>

Wenn Sie Ihre DNS-Zone konfigurieren möchten, um einen DKIM-Eintrag für Ihr Angebot hinzuzufügen, folgen Sie den unten stehenden Anweisungen.

Melden Sie sich im [OVHcloud Kundencenter](/links/manager) an, klicken Sie auf das Register `Web Cloud`{.action} und dann auf `Namen von Domains`{.action} in der linken Spalte, und wählen Sie den gewünschten Domainnamen aus.

Klicken Sie auf das Register `DNS-Zone`{.action} und dann auf `Eintrag hinzufügen`{.action}. Es gibt drei Möglichkeiten, einen Eintrag für die DKIM-Konfiguration in Ihrer DNS-Zone hinzuzufügen:

- [Ein DKIM-Eintrag](#dkim-record) : Konfiguration, die Ihnen ermöglicht, alle Parameter eines DKIM-Eintrags anzuzeigen.
- [Ein TXT-Eintrag](#txt-record) : Eintrag, den Sie verwenden, wenn Ihnen alle DKIM-Parameter bereits bereitgestellt wurden.
- [Ein CNAME-Eintrag](#cname-record) : Eintrag, der für ein E-Mail-Angebot von OVHcloud oder einen Microsoft E-Mail-Server verwendet wird.

#### DKIM-Eintrag <a name="dkim-record"></a>

Dieser Eintrag wird im Interface als DKIM bezeichnet, handelt sich aber tatsächlich um einen TXT-Eintrag. Der DKIM-Eintrag dient dazu, die verschiedenen Konfigurationsparameter übersichtlich in separaten Feldern darzustellen.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-add.png){.thumbnail .w-400 .h-600}

- **Unterdomäne** : Geben Sie den Namen des DKIM-Selektors ein und fügen Sie `._domainkey` als Suffix hinzu. Der Domainname wird automatisch am Ende hinzugefügt.

*Beispiel:*

```console
  selector-name._domainkey.mydomain.ovh.
```

- **Version (v=)** : Dient dazu, die DKIM-Version anzugeben. Es wird empfohlen, sie zu verwenden, und der Standardwert ist `DKIM1`.<br>
Wenn angegeben, muss dieser Tag am Anfang des Eintrags stehen und muss gleich "DKIM1" sein (ohne Anführungszeichen). Einträge, die mit einem Tag "v=" beginnen, das einen anderen Wert hat, müssen ignoriert werden.

- **Granularität (g=)** : Ermöglicht es, den "local-part" einer E-Mail-Adresse anzugeben, also den Teil vor dem " @ ".<br>
Es ermöglicht, die E-Mail-Adresse(n), die berechtigt sind, eine Nachricht mit dem DKIM-Schlüssel des Selektors zu signieren, anzugeben.<br>
Der Standardwert von "g=" ist "\*", was bedeutet, dass alle E-Mail-Adressen berechtigt sind, den DKIM-Signaturschlüssel zu verwenden.<br>
Durch Angabe eines spezifischen Werts für "g=" kann die Nutzung des Schlüssels auf eine bestimmte lokale E-Mail-Adresse oder auf eine Gruppe von Adressen durch Wildcards eingeschränkt werden (z. B. "\*-group").

- **Algorithmus (hash) (h=)** : Ermöglicht es, die Hash-Verfahren anzugeben, die für die Signatur der E-Mail-Header verwendet werden. Dieser Tag ermöglicht es, eine Liste der Hash-Verfahren anzugeben, die für die Erstellung einer DKIM-Signatur für eine bestimmte Nachricht verwendet werden.

- **Schlüsseltyp (k=)** : Gibt den Signaturalgorithmus an, der für die Signatur von ausgehenden E-Mails verwendet wird. Damit können Empfänger erfahren, wie die Nachricht signiert wurde und welche Methode zur Überprüfung der Authentizität verwendet wird.<br>
Mögliche Werte für den Tag "k=" umfassen "rsa" für den RSA-Signaturalgorithmus und "ed25519" für den Ed25519-Signaturalgorithmus. Die Wahl des Algorithmus hängt von der Sicherheitspolitik des Absenders und der Unterstützung durch den Empfänger ab.

- **Notizen (n=)** : Dient dazu, Notizen zu hinterlegen, die für Administratoren, die das DKIM-Schlüsselsystem verwalten, von Interesse sind.<br>
Diese Notizen können für Dokumentationszwecke nützlich sein oder Administratoren helfen, das Funktionieren von DKIM zu verstehen oder zu verwalten. Die in n= enthaltenen Notizen werden von Programmen nicht interpretiert und beeinflussen das Funktionieren von DKIM nicht.

- **Öffentlicher Schlüssel (base64) (p=)** : Wird verwendet, um die Base64-kodierten Daten des öffentlichen DKIM-Schlüssels einzugeben.<br>
Dieser Tag ist in der DKIM-Signatur obligatorisch und ermöglicht Empfängern, den erforderlichen öffentlichen Schlüssel abzurufen, um die Authentizität der signierten Nachricht zu überprüfen.

- **Öffentlichen Schlüssel widerrufen** : Wenn ein öffentlicher DKIM-Schlüssel widerrufen wurde (z. B. bei einem Compromiss des privaten Schlüssels), muss ein leerer Wert für den Tag "p=" verwendet werden, um anzuzeigen, dass dieser öffentliche Schlüssel nicht mehr gültig ist. Empfänger müssen dann für jede DKIM-Signatur, die auf einen widerrufenen Schlüssel verweist, einen Fehler zurückgeben.

- **Diensttyp (s=)**: Der Tag "s=" (Service Type) ist optional und wird standardmäßig nicht angezeigt. Er ermöglicht es, den oder die Diensttypen anzugeben, auf die sich dieser DKIM-Eintrag bezieht.<br>
Die Diensttypen werden mithilfe einer Liste von Schlüsselwörtern, die durch Doppelpunkte ":" getrennt sind, definiert.<br>
Der Empfänger muss diesen Eintrag ignorieren, wenn der entsprechende Diensttyp nicht aufgeführt ist.<br>
Der Tag "s=" ist dazu gedacht, die Nutzung der Schlüssel für andere Zwecke einzuschränken, falls die Nutzung von DKIM für andere Dienste in Zukunft definiert wird.<br>
Die derzeit definierten Diensttypen sind "\*" (alle Diensttypen), "email" (E-Mail).

- **Testmodus (t=y)** : Ermöglicht es den Eigentümern der Domain, die Einrichtung von DKIM zu testen, ohne dass Nachrichten abgelehnt oder als SPAM markiert werden, falls die DKIM-Signaturprüfung fehlschlägt.<br>
Wenn der Flag "t=y" verwendet wird, darf der Empfänger keine besondere Behandlung von Nachrichten im Testmodus oder von Nachrichten ohne Signatur vornehmen. Der Empfänger kann jedoch das Ergebnis des Testmodus verfolgen, um die Signatoren zu unterstützen.

- **Unterdomänen (t=s)** : Ermöglicht es, die Nutzung der DKIM-Signatur auf die Domain selbst einzuschränken (z. B. @mydomain.ovh) oder die Nutzung von der Domain und ihren Unterdomänen zu erlauben (z. B. @mydomain.ovh, @test.mydomain.ovh, @other.mydomain.ovh usw.).

#### TXT-Eintrag <a name="txt-record"></a>

Dies ist der native Eintragstyp, der verwendet wird, um DKIM in der DNS-Zone Ihres Domainnamens zu konfigurieren. Es ist wichtig, seine Syntax gut zu verstehen, um ihn ordnungsgemäß auszufüllen.

Diese DKIM-Konfiguration wird empfohlen, wenn Ihnen die einzugebenden Informationen vom E-Mail-Dienstanbieter bereitgestellt wurden.

Um die Zusammensetzung des DKIM-Eintrags besser zu verstehen, konsultieren Sie den vorhergehenden Abschnitt dieses Leitfadens mit dem Titel « [DKIM-Eintrag](#dkim-record) ».

**Beispiel eines DKIM-Eintrags**

- Unterdomäne :

```console
selector-name._domainkey.mydomain.ovh.
```

- Ziel :

```console
v=DKIM1;t=s;p= MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA77VDAIfyhjtoF0DIE5V7 rev1EKk4L0nxdBpD5O/jPrM4KP0kukeuB6IMpVplkkq52MSDeRcjoO50h0DmwZOr RUkyGjQwOnAh0VhY3fqkuwBYftEX7vWo8C2E1ylzimABkwPpSL62jZ1DheoXcil9 1M35wWBKtlYdXVedKjCQKOEnwTo+0hdNe38rU9NMgq6nbTIMjDntvxoVI+yF3kcx q/VpAY8BIYbcAXkVFvUyfUBABnnKpf0SfblsfcLW0Koy/FRxPDFOvnjNxXeOxMFR UI6K6PaW2WvtbJG2v+gHLY5M4tB0+/FNJU9emZfkPOk3DmRhZ8ENi7+oZa2ivUDj OQIDAQAB
```

#### CNAME-Eintrag <a name="cname-record"></a>

Der CNAME-Eintrag ist ein Alias. Das bedeutet, dass der Zielwert auf eine URL verweist, die selbst den DKIM-Eintrag für den Server bereitstellt, der den CNAME-Eintrag abfragt. Dieser Eintragstyp wird häufig verwendet, wenn ein Microsoft E-Mail-Server genutzt wird.

Es handelt sich genau um den Eintragstyp, der verwendet wird, um DKIM auf einer Domain zu aktivieren, die für ein Exchange-Angebot von OVHcloud deklariert wurde. Dieser Prozess ermöglicht es Ihrem E-Mail-Dienstanbieter, die Sicherheit und Aktualisierung des DKIM für Sie zu verwalten.

### DKIM testen <a name="test-dkim"></a>

Wir empfehlen Ihnen, eine E-Mail von einem Konto auf Ihrer Exchange-Plattform an eine E-Mail-Adresse zu senden, die bei Empfang die DKIM-Signatur überprüft.

Hier finden Sie, was Sie im Header der empfangenen E-Mail finden können :

<pre class="bgwhite"><code>ARC-Authentication-Results: i=1; mx.example.com;
       dkim=pass header.i=@mydomain.ovh header.s=ovhex123456-selector1 header.b=KUdGjiMs;
       spf=pass (example.com: domain of test-dkim@mydomain.ovh designates 54.36.141.6 as permitted sender) smtp.mailfrom=test-dkim@mydomain.ovh
Return-Path: &lt;test-dkim@mydomain.ovh&gt;
</code></pre>

Um den Header einer E-Mail abzurufen, konsultieren Sie unser Leitfaden « [Header einer E-Mail abrufen](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/diagnostic_headers) ».

### Anwendungsfälle <a name="usecases"></a>

#### Wie und warum kann ich das DKIM-Schlüsselpaar auf meinem Angebot ändern ? <a name="2selectors"></a>

> [!warning]
>
> Diese Frage betrifft ausschließlich die Angebote Exchange und E-Mail Pro.

Wenn Sie

Sie stellen fest, dass Ihre E-Mails nicht mit DKIM signiert werden, obwohl dieser aktiviert oder konfiguriert wurde. Zunächst melden Sie sich in Ihrem Kundencenter an, um den Status des DKIM zu prüfen.

Klicken Sie auf das untenstehende Register, das Ihrer Angebotsoption entspricht, um den Status des DKIM auf Ihrer E-Mail-Plattform zu überprüfen.

> [!tabs]
> **Exchange**
>>
>> 1. Melden Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Wählen Sie im Bereich `MICROSOFT` den Punkt `Exchange`{.action} aus.
>> 1. Wählen Sie die betreffende Plattform aus.
>>
>> Im Bereich `Domaines associés`{.action} prüfen Sie die Farbe des Symbols `DKIM` rechts neben dem Namen der betreffenden Domain (siehe Bild unten).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>
> **E-Mail Pro**
>>
>> 1. Melden Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) an.
>> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
>> 1. Klicken Sie auf `Email Pro`{.action}.
>> 1. Wählen Sie die betreffende Plattform aus.
>> 1. Gehen Sie abschließend zum Register `Domaines associés`{.action}.
>>
>> Im Bereich `Domaines associés`{.action} prüfen Sie die Farbe des Symbols `DKIM` rechts neben dem Namen der betreffenden Domain (siehe Bild unten).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>

Hier sind die 4 Zustände, die dazu führen können, dass das DKIM-Symbol in Ihrem Kundencenter rot angezeigt wird. Klicken Sie auf das Register, das zu Ihrem Fehlercode passt:

> [!tabs]
> **501**
>>
>> "Only one dkim selector has been initialized"<br><br>
>> Nur ein DKIM-Selektor ist in Ihrer Konfiguration vorhanden. Damit wir bei Bedarf den Wechsel zu einem neuen Schlüssel ermöglichen können, müssen Sie beide von dem Dienst bereitgestellten Selektoren konfigurieren.<br><br>
>> Um diesen Fehler zu beheben:
>>
>> - Prüfen Sie den Status der DKIM-Selektoren, um den zu identifizieren, der konfiguriert werden muss. Nutzen Sie hierzu den Abschnitt „[API - Les différents états du DKIM](#dkim-status)“ in diesem Leitfaden.
>> - Sobald Sie den zu konfigurierenden Selektor identifiziert haben, folgen Sie den Schritten im Abschnitt „[API - Configuration complète du DKIM](#firststep)“ in diesem Leitfaden, entsprechend Ihrer Anbieteroption (Exchange oder E-Mail Pro), und wenden Sie diese nur auf den betreffenden Selektor an.
>> Warten Sie maximal 24 Stunden nach der Konfiguration des Selektors.
>>
> **502**
>>
>> "One DKIM configuration task is in error"<br><br>
>> Beim Konfigurieren des DKIM ist ein Fehler aufgetreten. Falls sich Ihr Zustand nach 24 Stunden nicht geändert hat, empfehlen wir Ihnen, ein [Support-Ticket](https://help.ovhcloud.com/csm?id=csm_get_help) zu öffnen.
>>
> **503**
>>
>> "CNAME record is wrong"<br><br>
>> Der erforderliche CNAME-Eintrag für die DKIM-Konfiguration wurde nicht korrekt eingegeben. Sie müssen die DNS-Zone der angeschlossenen Domain korrekt konfigurieren.
>> Um Ihre DNS-Zone zu konfigurieren, rufen Sie die Werte des angezeigten CNAME-Eintrags ab:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Wenn wir uns beispielsweise das obige Screenshotbild ansehen, ist die Domain „mydomain.ovh“ und es wird gefordert, den Selektor „2“ zu konfigurieren. Hier müssen Sie einen CNAME-Eintrag hinzufügen, bei dem der Unterdomain-Wert `ovhex1234567-selector2.domainkey.mydomain.ovh` ist und die Zieladresse `ovhex1234567-selector2.domainkey.7890.dkim.mail.ovh.net` lautet.<br><br>
>> Nachdem Sie Ihre DNS-Zone konfiguriert haben, warten Sie bis zur DNS-Propagation (maximal 24 Stunden).
>>
> **504**
>>
>> "One CNAME record is missing"<br><br>
>> Der erforderliche CNAME-Eintrag für die DKIM-Konfiguration fehlt. Sie müssen die DNS-Zone der angeschlossenen Domain konfigurieren.
>> Um Ihre DNS-Zone zu konfigurieren, rufen Sie die Werte des angezeigten CNAME-Eintrags ab:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Wenn wir uns beispielsweise das obige Screenshotbild ansehen, ist die Domain „mydomain.ovh“ und es wird gefordert, den Selektor „2“ zu konfigurieren. Hier müssen Sie einen CNAME-Eintrag hinzufügen, bei dem der Unterdomain-Wert `ovhex1234567-selector2.domainkey.mydomain.ovh` ist und die Zieladresse `ovhex1234567-selector2.domainkey.890123.dkim.mail.ovh.net` lautet.<br><br>
>> Nachdem Sie Ihre DNS-Zone konfiguriert haben, warten Sie bis zur DNS-Propagation (maximal 24 Stunden).
>>

#### Wie kann ich über die OVHcloud API den Zustand des nicht funktionierenden DKIM verstehen? <a name="api-error"></a>

Wenn Sie die OVHcloud API nutzen, um Ihren DKIM zu konfigurieren, und dieser nicht funktioniert, nutzen Sie den Abschnitt „[API - Les différents états du DKIM](#dkim-status)“ in diesem Leitfaden, um den Zustand Ihrer Selektoren zu identifizieren.

Untenstehend finden Sie die Zustände, die den Betrieb Ihres DKIM blockieren können, sowie die jeweilige Lösung für jede Situation.

> [!tabs]
> **Exchange und E-Mail Pro**
>> - `WaitingRecord` : Die DNS-Einträge warten auf Konfiguration oder befinden sich in der Validierung in der DNS-Zone der Domain. Es wird regelmäßig automatisch geprüft, ob der DNS-Eintrag vorhanden und korrekt ist. Je nach Angebot folgen Sie **Schritt 5** im Abschnitt „[API - Configuration complète du DKIM](#firststep)“, um die DNS-Zone der betreffenden Domain korrekt zu konfigurieren.
>> - `ready` : Die DNS-Einträge sind in der Zone vorhanden. Der DKIM kann jetzt aktiviert werden. Sie müssen lediglich den Selektor aktivieren, indem Sie sich auf den Abschnitt „[API - Activer ou changer un sélecteur DKIM](#enable-switch)“ stützen.
>> - `deleting` : Der DKIM wird gelöscht. Nach der Löschung müssen Sie den Abschnitt „[API - Configuration complète du DKIM](#firststep)“ befolgen.
>> - `disabling` : Der DKIM wird deaktiviert. Nach dieser Operation können Sie den Selektor aktivieren, indem Sie sich auf den Abschnitt „[API - Activer ou changer un sélecteur DKIM](#enable-switch)“ stützen.
>> - `todo` : Die Aufgabe wurde initialisiert, sie muss gestartet werden. Falls sich Ihr Selektor nach 24 Stunden immer noch in diesem Zustand befindet, empfehlen wir Ihnen, ein [Support-Ticket](https://help.ovhcloud.com/csm?id=csm_get_help) zu öffnen und die Nummer des betreffenden Selektors anzugeben.
> **MX Plan und Zimbra**
>> - `disabled` : Der DKIM ist deaktiviert, wurde noch nicht konfiguriert oder wurde über die API deaktiviert. <br>
>> - `modifying` : Die DKIM-Konfiguration ist in Bearbeitung, es ist erforderlich, bis zum Ende des Prozesses zu warten.<br>
>> - `toConfigure` : Die DKIM-Konfiguration wartet auf die DNS-Parameter der Domain. Sie müssen die DNS-Einträge manuell in der DNS-Zone der Domain eintragen. Dazu folgen Sie dem Abschnitt „[Configuration complète du DKIM](#confemail)“ in diesem Leitfaden. <br>
>> - `error` : Beim Installationsprozess ist ein Fehler aufgetreten. Wir empfehlen Ihnen, ein [Support-Ticket](https://help.ovhcloud.com/csm?id=csm_get_help) zu öffnen und den Namen der betreffenden Domain anzugeben.
>>
>> Auf Ebene der Selektoren gibt es ebenfalls 2 Zustände, die auf einen Fehler hinweisen:
>>
>> - `toSet` : Der Selektor ist in der DNS-Zone der Domain nicht konfiguriert. Folgen Sie [Schritt 4 von „der vollständigen DKIM-Konfiguration“ für MX Plan und Zimbra](#confemail).
>> - `toFix` : Der Selektor ist zwar in der DNS-Zone der Domain konfiguriert, aber die Werte sind falsch. Folgen Sie [Schritt 4 von „der vollständigen DKIM-Konfiguration“ für MX Plan und Zimbra](#confemail).

## Weiterführende Informationen
Treten Sie unserer [User Community](/links/community) bei.

Im Rahmen der Einrichtung eines dynamischen DNS-Eintrags (DynHost) ist die Verwendung eines Wildcards (Zeichen `*`) im Feld `sous-domaine`{.action} des Formulars für einen DNS-Eintrag nicht verfügbar.