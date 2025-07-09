---
title: "Web Cloud Databases - Wie autorisiere ich eine IP-Adresse?"
excerpt: "Erfahren Sie, wie Sie einer oder mehreren IP-Adressen den Zugriff auf Ihre Web Cloud Databases Lösung erlauben."
updated: 2025-07-10
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

## Ziel

Die Lösungen [Web Cloud Databases](/links/web/databases) können mit OVHcloud-Diensten oder Diensten außerhalb von OVHcloud verwendet werden.

Standardmäßig und aus Sicherheitsgründen für diese Lösungen:

- Nur die IP-Adressen, die mit unserer Shared Hosting Infrastruktur verbunden sind, sind zum Zugriff auf den Inhalt der Datenbanken berechtigt.
- Der Zugriff auf die Logs der Lösung ist nicht auf Basis der IP-Adressen eingeschränkt. So kann zum Beispiel über einen Computer darauf zugegriffen werden.

Möchten Sie diese Berechtigungen/Einschränkungen ändern?

**Diese Anleitung erklärt, wie Sie einer oder mehreren IP-Adressen Zugriff auf Ihre Web Cloud Databases Lösung gewähren.**

## Voraussetzungen

- Sie verfügen über eine Lösung [Web Cloud Databases](/links/web/databases).
- Die IP-Adresse (oder den IP-Adressbereich) kennen, die bzw. der für Ihre Lösung autorisiert werden soll.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

### Eine IP-Adresse oder einen IP-Adressbereich zulassen

> [!primary]
>
> Zur Erinnerung: Wenn Sie Ihre [Web Cloud Databases](/links/web/databases) Lösung gerade aktiviert haben und diese mit einem [OVHcloud Webhosting](/links/web/hosting) Angebot verwenden möchten, sind die IP-Adressen dieser Angebote bereits standardmäßig autorisiert.

Klicken Sie jeweils auf die Tabs, um die **5** Schritte anzuzeigen.

> [!tabs]
> **Schritt 1**
>>
>> Loggen Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) ein und gehen Sie in den Bereich `Web Cloud`{.action}.
>>
>> ![Web Cloud](/pages/assets/screens/control_panel/product-selection/web-cloud.png){.thumbnail}
>>
> **Schritt 2**
>>
>> Klicken Sie auf das Menü `Web Cloud Databases`{.action} und wählen Sie die betreffende Web Cloud Databases Lösung aus.
>>
>> ![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases.png){.thumbnail}
>>
> **Schritt 3**
>>
>> Klicken Sie auf der angezeigten Seite auf den Tab `Autorisierte IPs`{.action}.
>>
>> ![Authorised IPs](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/authorised-ips.png){.thumbnail}
>>
> **Schritt 4**
>>
>> Klicken Sie auf der angezeigten Seite auf den Button `IP-Adresse / Maske hinzufügen`{.action} über der Tabelle.
>>
>> ![Authorised IPs interface](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/authorized-ips/tab-0000-sftp-hosting-enabled.png){.thumbnail}
>>
>> > [!success]
>> >
>> > Wenn Sie eine bereits zugelassene IP-Adresse oder einen bereits zugelassenen IP-Adressbereich ändern möchten, klicken Sie in der Tabelle direkt auf den Button `...`{.action} rechts neben der Zeile, die der zu ändernden IP-Adresse oder dem zu ändernden IP-Adressbereich entspricht, und dann auf `Whitelist bearbeiten`{.action}.
>>
> **Schritt 5**
>>
>> Im angezeigten Fenster müssen mehrere Felder ausgefüllt werden:
>>
>> ![Add an IP address or mask](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/authorized-ips/add-an-ip-address-mask-confirmation.png){.thumbnail}
>>
>> - `IP / Maske *`{.action} : Geben Sie hier die IP-Adresse (zum Beispiel: `203.0.113.44`) oder den IP-Adressbereich (zum Beispiel: `203.0.113.0/24`, der alle IP-Adressen von `203.0.113.0` bis `203.0.113.255` darstellt) ein, die Sie für Ihre Web Cloud Databases Lösung autorisieren möchten.
>> - `Beschreibung`{.action} (optional): Sie können z.B. Informationen zur Rolle der betreffenden IP-Adresse oder des IP-Adressbereichs hinzufügen.
>> - `Datenbanken`{.action} : Aktivieren Sie dieses Kontrollkästchen, damit die IP-Adresse oder der IP-Adressbereich auf die Datenbanken auf Ihrer Web Cloud Databases Lösung zugreifen kann.
>> - `SFTP`{.action} : Setzen Sie hier einen Haken, damit die IP-Adresse oder der IP-Adressbereich auf die Logs Ihrer Web Cloud Databases Lösung zugreifen können.
>>
>> > [!warning]
>> >
>> > Es wird dringend davon abgeraten, das Kontrollkästchen `Datenbanken`{.action} zu aktivieren, um dem IP-Adressbereich `0.0.0.0/0` den Zugriff auf Ihre Datenbanken zu erlauben.
>> >
>> > Dies würde es ermöglichen, den Zugriff auf alle vorhandenen IPv4-Adressen auf Ihre Datenbanken zu ermöglichen.
>>
>> Nachdem Sie die Informationen eingegeben haben, klicken Sie auf `Bestätigen`{.action}.

## Sonderfälle

**Klicken Sie auf die unten stehenden Fälle, um die zugehörigen Informationen anzuzeigen.**

/// details | Der IP-Adressbereich 0.0.0.0/0

Bei der Aktivierung Ihrer Web Cloud Databases Lösung ist bereits standardmäßig eine Zeile für den IP-Adressbereich `0.0.0.0/0` vorhanden, um den Zugriff per **SFTP** zu erlauben.

Diese Berechtigung wird bewusst eingerichtet, damit Sie auf die Logdateien Ihrer Web Cloud Databases Lösung zugreifen können, ohne die IP-Adresse Ihres Internet Access Points angeben zu müssen.

Diese IP-Adresse kann sich nämlich je nach Internet Service Provider regelmäßig ändern.

Außerdem empfehlen wir Ihnen, diese Berechtigung **nicht zu ändern** und den Zugriff auf die Datenbanken auf Ihrer Web Cloud Databases Lösung nicht zu erlauben.

Auf diese Weise könnte der Zugriff auf die Datenbanken auf alle vorhandenen IPv4-Adressen ermöglicht werden, was ein Risiko für die Sicherheit Ihrer Daten darstellt.

///


/// details | Autorisierung des Zugriffs auf die OVHcloud Webhostings

Bei der Aktivierung Ihrer Web Cloud Databases Lösung ist die Autorisierung für den Zugriff auf die OVHcloud Webhostings standardmäßig aktiviert.

Wenn Sie diese Berechtigung deaktivieren möchten, da Sie kein Webhosting mit Ihrer Web Cloud Databases Lösung verwenden, folgen Sie den nachfolgenden **4** Schritten:

> [!tabs]
> **Schritt 1**
>>
>> Loggen Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) ein und gehen Sie in den Bereich `Web Cloud`{.action}.
>>
>> ![Web Cloud](/pages/assets/screens/control_panel/product-selection/web-cloud.png){.thumbnail}
>>
> **Schritt 2**
>>
>> Klicken Sie auf das Menü `Web Cloud Databases`{.action} und wählen Sie die betreffende Web Cloud Databases Lösung aus.
>>
>> ![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases.png){.thumbnail}
>>
> **Schritt 3**
>>
>> Klicken Sie auf der angezeigten Seite auf den Tab `Autorisierte IPs`{.action}.
>>
>> ![Authorised IPs](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/authorised-ips.png){.thumbnail}
>>
> **Schritt 4**
>>
>> Deaktivieren Sie auf der angezeigten Seite das Kontrollkästchen vor `Den OVHcloud Webhostings den Zugriff auf die Datenbank erlauben`{.action}.
>>
>> ![Authorised IPs interface](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/authorized-ips/tab-0000-sftp-hosting-enabled.png){.thumbnail}

///

## Weiterführende Informationen
 
Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).
 
Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).
 
Treten Sie unserer [User Community](/links/community) bei.