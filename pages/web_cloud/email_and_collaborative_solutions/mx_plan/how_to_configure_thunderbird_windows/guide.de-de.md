---
title: 'MX Plan – E-Mail-Adresse in Thunderbird unter Windows konfigurieren'
excerpt: 'Erfahren Sie, wie Sie Ihre MX Plan-E-Mail-Adresse in Thunderbird unter Windows konfigurieren'
updated: 2025-09-19
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
.w-400 {
  max-width:400px !important;
}
</style>

## Ziel

MX Plan-E-Mail-Konten können auf verschiedenen kompatiblen E-Mail-Programmen eingerichtet werden. Dies ermöglicht es Ihnen, Ihre E-Mail-Adresse von Ihrem bevorzugten Gerät aus zu nutzen. Thunderbird ist ein freier und kostenloser E-Mail-Client.

**Erfahren Sie, wie Sie Ihre MX Plan-E-Mail-Adresse in Thunderbird unter Windows konfigurieren.**

## Voraussetzungen

- Über ein MX Plan-Angebot verfügen. Dieses ist verfügbar über:
    - Eine [Webhosting-Angebot](/links/web/hosting).
    - Ein [kostenloses 100M-Webhosting](/links/web/domains-free-hosting), das mit einem Domainnamen (vorher aktiviert) einhergeht.
    - Ein separat bestelltes MX Plan-Angebot.
    - Über eine [Zimbra Starter-E-Mail-Adresse](/links/web/zimbra) verfügen.
- Das Thunderbird-Programm auf Ihrem Windows-Gerät installiert haben.
- Die Zugangsdaten für die zu konfigurierende E-Mail-Adresse besitzen.

/// details | Informationen zur Verwaltung und Konfiguration von OVHcloud-Diensten

Dieser Leitfaden zeigt Ihnen, wie Sie OVHcloud-Lösungen mit externen Tools nutzen können und welche Anpassungen in spezifischen Kontexten erforderlich sind. Es kann sein, dass Sie die Anweisungen an Ihre Situation anpassen müssen.

Falls Sie Schwierigkeiten bei diesen Vorgängen haben, empfehlen wir Ihnen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren und/oder mit unserer Community zu diskutieren. OVHcloud kann keine technische Unterstützung für die Nutzung externer Tools anbieten. Weitere Informationen finden Sie im Abschnitt [Weitere Informationen](#gofurther) dieses Leitfadens.

///

## In der praktischen Anwendung

### Konto hinzufügen

- **Beim ersten Start der Anwendung**: Ein Konfigurationsassistent wird angezeigt und bittet Sie, Ihre E-Mail-Adresse einzugeben.

- **Wenn bereits ein Konto in der Anwendung eingerichtet ist**:

    1. Klicken Sie auf das Menü `☰`{.action} in der oberen horizontalen Leiste.
    2. Klicken Sie auf `Neues Konto`{.action}.
    3. Klicken Sie auf `E-Mail-Adresse`{.action}.

![thunderbird](images/configuration-thunderbird-win-01.png){.thumbnail .w-600}

> [!warning]
>
> Es ist wichtig, die für Ihre Region (**EUROPE** oder **AMERIQUE / ASIE-PACIFIQUE**) relevante Wertung zu beachten.

Folgen Sie den Konfigurationsschritten, indem Sie nacheinander auf die folgenden **5** Register klicken:

> [!tabs]
> **Schritt 1**
>>
>> Geben Sie in dem angezeigten Fenster die folgenden beiden Informationen ein:
>>
>>  - Ihren vollständigen Namen (Anzeigename).
>>  - Die zu konfigurierende E-Mail-Adresse.
>>
>> Klicken Sie auf `Weiter`{.action}, um die Einstellungen abzuschließen.
>>
>> ![thunderbird](images/configuration-thunderbird-mxplan-02.png){.thumbnail .w-600}
>>
> **Schritt 2**
>>
>> Wenn Thunderbird einen OVHcloud-Domänennamen erkennt, wird eine automatische Konfiguration für das MX Plan-Angebot vorgeschlagen:
>>
>>  - Wenn die Informationen korrekt sind, klicken Sie auf `Weiter`{.action} und gehen Sie zum Schritt 5.
>>  - Andernfalls klicken Sie auf `KONFIGURATION ÄNDERN`{.action}, um eine manuelle Konfiguration vorzunehmen.
>>
>> ![thunderbird](images/configuration-thunderbird-ssl0-03.png){.thumbnail .w-600}
>>
> **Schritt 3**
>>
>> Empfangsservereinstellungen:
>>
>>  - **Protokoll**: IMAP
>>  - **Hostname EUROPE (Empfang)**: imap.mail.ovh.net **oder** ssl0.ovh.net
>>  - **Hostname AMERIQUE/ASIE-PACIFIQUE (Empfang)**: imap.mail.ovh.ca
>>  - **Port**: 993
>>  - **Verbindungssicherheit**: SSL/TLS
>>  - **Authentifizierungsart**: Normales Passwort
>>  - **Benutzername**: Ihre vollständige E-Mail-Adresse
>>
>> ![thunderbird](images/configuration-thunderbird-mxplan-04.png){.thumbnail .w-600}
>>
> **Schritt 4**
>>
>> Einstellungen des Sendeservers:
>>
>>  - **Protokoll**: SMTP 
>>  - **Server EUROPE (Ausgang)**: smtp.mail.ovh.net **oder** ssl0.ovh.net
>>  - **Server AMERIQUE/ASIE-PACIFIQUE (Ausgang)**: smtp.mail.ovh.ca
>>  - **Port**: 587
>>  - **Verbindungssicherheit**: STARTTLS
>>  - **Authentifizierungsart**: Normales Passwort
>>  - **Benutzername**: Ihre vollständige E-Mail-Adresse
>> 
>> 1\. Klicken Sie auf `Testen`{.action}, um die eingegebenen Einstellungen zu überprüfen.<br>
>> 2\. Klicken Sie auf `Weiter`{.action}, um diese Einstellungen zu bestätigen.
>>
>> ![thunderbird](images/configuration-thunderbird-mxplan-05.png){.thumbnail .w-600}
>>
> **Schritt 5**
>>
>> Geben Sie das Passwort für die E-Mail-Adresse ein und klicken Sie auf `Weiter`{.action}, um die Konfiguration abzuschließen.
>>
>> ![thunderbird](images/configuration-thunderbird-password-06.png){.thumbnail .w-600}
>>

> [!primary]
>
> **POP-Konfiguration**
>
> Wenn Sie eine POP-Konfiguration für Ihre E-Mail-Adresse wünschen, ersetzen Sie die Einstellungen von **Schritt 3** durch die folgenden:
>
> Empfangsservereinstellungen:
>
> - **Protokoll**: POP3
> - **Hostname EUROPE (Empfang)**: pop.mail.ovh.net **oder** ssl0.ovh.net
> - **Hostname AMERIQUE/ASIE-PACIFIQUE (Empfang)**: pop.mail.ovh.ca
> - **Port**: 995
> - **Verbindungssicherheit**: SSL/TLS
> - **Authentifizierungsart**: Normales Passwort
> - **Benutzername**: Ihre vollständige E-Mail-Adresse

### E-Mail-Adresse nutzen

Sobald Ihre E-Mail-Adresse konfiguriert ist, können Sie damit beginnen, sie zu nutzen! Sie können nun E-Mails senden und empfangen.

OVHcloud bietet außerdem eine Webanwendung an, mit der Sie Ihre E-Mail-Adresse über einen Webbrowser nutzen können. Um auf den OVHcloud-Webmail-Zugriff zu erhalten, klicken Sie auf [diesen Link](/links/web/email). Sie können sich dort mit den Zugangsdaten Ihrer E-Mail-Adresse anmelden.

### Sicherung Ihrer E-Mail-Adresse erstellen

Wenn Sie eine Aktion durchführen müssen, die zu einem Datenverlust Ihres E-Mail-Kontos führen könnte, empfehlen wir Ihnen, vorher eine Sicherung des betreffenden E-Mail-Kontos durchzuführen. Dazu konsultieren Sie den Abschnitt „**Exportieren**“ im Bereich „**Thunderbird**“ unseres Leitfadens „[Manuelle Migration Ihrer E-Mail-Adresse](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration)“.

### Vorhandene Einstellungen ändern

Wenn Ihr E-Mail-Konto bereits eingerichtet ist und Sie auf die Kontoeinstellungen zugreifen müssen, um sie zu ändern:

1. Klicken Sie auf das Menü `☰`{.action} in der oberen horizontalen Leiste.
2. Klicken Sie auf `Kontoeinstellungen`{.action}.

![Thunderbird](images/configuration-thunderbird-win-07.png){.thumbnail .w-600}

- Um die Einstellungen, die sich auf den **Empfang** Ihrer E-Mails beziehen, zu ändern, klicken Sie auf `Servereinstellungen`{.action} in der linken Spalte unter Ihrer E-Mail-Adresse.

![thunderbird](images/configuration-thunderbird-mxplan-win-08.png){.thumbnail .w-600}

- Um die Einstellungen, die sich auf den **Versand** Ihrer E-Mails beziehen, zu ändern, klicken Sie auf `Ausgehender Server (SMTP)`{.action} ganz unten in der linken Spalte.
- Klicken Sie auf die betreffende E-Mail-Adresse in der Liste und dann auf `Ändern`{.action}.

![thunderbird](images/configuration-thunderbird-mxplan-win-09.png){.thumbnail .w-600}

## Weiterführende Informationen <a name="go-further"></a>

> [!primary]
>
> Weitere Informationen zur Konfiguration einer E-Mail-Adresse über den Thunderbird-E-Mail-Client finden Sie im [Mozilla-Hilfezentrum](https://support.mozilla.org/products/thunderbird).

[Erste Schritte mit dem MX Plan-Angebot](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.