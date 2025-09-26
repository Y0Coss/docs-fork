---
title: 'E-Mail Pro - Konfigurieren Ihrer E-Mail-Adresse in Thunderbird unter Windows'
excerpt: 'Erfahren Sie, wie Sie Ihre E-Mail Pro-Adresse in Thunderbird unter Windows konfigurieren'
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
.w-600 {
  max-width:600px !important;
}
</style>

## Ziel

Die Konten von E-Mail Pro können in verschiedenen, kompatiblen E-Mail-Clients konfiguriert werden. Dies ermöglicht es Ihnen, Ihre E-Mail-Adresse von jedem Gerät aus zu verwenden. Thunderbird ist ein kostenloser und freier E-Mail-Client.

**Erfahren Sie, wie Sie Ihre E-Mail Pro-Adresse in Thunderbird unter Windows konfigurieren.**

## Voraussetzungen

- Sie müssen über eine [E-Mail Pro-Adresse](/links/web/email-pro) verfügen.
- Sie müssen den Thunderbird-Client auf Ihrem Windows-Gerät installiert haben.
- Sie müssen die Zugangsdaten für die E-Mail-Adresse haben, die Sie konfigurieren möchten.

/// details | Informationen zur Verwaltung und Konfiguration von OVHcloud-Diensten

In dieser Anleitung erfahren Sie, wie Sie OVHcloud Lösungen mit externen Tools verwenden und wie Sie in bestimmten Kontexten Änderungen vornehmen. Die Anweisungen müssen gegebenenfalls an Ihre Situation angepasst werden.

Sollten Sie bei der Durchführung dieser Operationen Schwierigkeiten haben, empfehlen wir Ihnen, sich mit einem [spezialisierten Dienstleister](/links/partner) in Verbindung zu setzen und/oder mit unserer Community zu sprechen. OVHcloud kann Ihnen keinen technischen Support für die Verwendung externer Tools anbieten. Weitere Informationen finden Sie im Abschnitt [Weiterführende Informationen](#gofurther) dieser Anleitung.


///

## In der Praxis

> [!warning]
>
> In unserem Beispiel verwenden wir den Serverhinweis: pro?.mail.ovh.net. Sie müssen das "?" durch die Zahl ersetzen, die den Server Ihres E-Mail Pro-Dienstes bezeichnet.
>
> 1. Melden Sie sich bei Ihrem [OVHcloud-Kundencenter](/links/manager) an.
> 1. Gehen Sie zum Bereich `Web Cloud`{.action}.
> 1. Klicken Sie auf `E-Mail Pro`{.action}.
> 1. Wählen Sie die betreffende Plattform aus.
> 1. Der Name des Servers ist im Rahmen **Verbindung** des Reiters `Allgemeine Informationen`{.action} sichtbar.

### Hinzufügen des Kontos

- **Beim ersten Starten der Anwendung**: Ein Konfigurationsassistent wird angezeigt und fordert Sie auf, Ihre E-Mail-Adresse einzugeben.

- **Wenn bereits ein Konto in der Anwendung konfiguriert ist**:

    1. Klicken Sie auf das Menü `☰`{.action} in der oberen horizontalen Leiste.
    2. Klicken Sie auf `Neues Konto`{.action}.
    3. Klicken Sie auf `E-Mail-Adresse`{.action}.

![thunderbird](images/configuration-thunderbird-win-01.png){.thumbnail .w-600}

Folgen Sie den Konfigurationsschritten, indem Sie nacheinander auf die **5** Registerkarten klicken:

> [!tabs]
> **Schritt 1**
>>
>> Geben Sie im angezeigten Fenster die beiden folgenden Informationen ein:
>>
>>  - Ihren vollständigen Namen (Anzeigename).
>>  - Die E-Mail-Adresse, die Sie konfigurieren möchten.
>>
>> Klicken Sie auf `Weiter`{.action}, um die Einstellungen zu vervollständigen.
>>
>> ![thunderbird](images/configuration-thunderbird-emp-02.png){.thumbnail .w-600}
>>
> **Schritt 2**
>>
>> Wenn Thunderbird einen OVHcloud-Domänennamen erkennt, wird eine automatische Konfiguration im Zusammenhang mit dem MX Plan-Angebot vorgeschlagen. Klicken Sie auf `KONFIGURATION BEARBEITEN`{.action}.
>>
>> ![thunderbird](images/configuration-thunderbird-ssl0-03.png){.thumbnail .w-600}
>>
> **Schritt 3**
>>
>> Einstellungen für den Empfangsserver:
>>
>>  - **Protokoll**: IMAP
>>  - **Servername**: pro?.mail.ovh.net (ersetzen Sie das "?" durch die Nummer Ihres Servers)
>>  - **Port**: 993
>>  - **Verbindungssicherheit**: SSL/TLS
>>  - **Authentifizierungsmethode**: Normales Passwort
>>  - **Benutzername**: Ihre vollständige E-Mail-Adresse
>>
>> ![thunderbird](images/configuration-thunderbird-emp-04.png){.thumbnail .w-600}
>>
> **Schritt 4**
>>
>> Einstellungen für den Sendeserver:
>>
>>  - **Protokoll**: SMTP
>>  - **Servername**: pro?.mail.ovh.net (ersetzen Sie das "?" durch die Nummer Ihres Servers)
>>  - **Port**: 587
>>  - **Verbindungssicherheit**: STARTTLS
>>  - **Authentifizierungsmethode**: Normales Passwort
>>  - **Benutzername**: Ihre vollständige E-Mail-Adresse
>> 
>> 1\. Klicken Sie auf `Testen`{.action}, um die eingegebenen Einstellungen zu überprüfen.<br>
>> 2\. Klicken Sie auf `Weiter`{.action}, um diese Einstellungen zu bestätigen.
>>
>> ![thunderbird](images/configuration-thunderbird-emp-05.png){.thumbnail .w-600}
>>
> **Schritt 5**
>>
>> Geben Sie das Passwort ein, das mit der E-Mail-Adresse verknüpft ist, und klicken Sie auf `Weiter`{.action}, um die Konfiguration abzuschließen.
>>
>> ![thunderbird](images/configuration-thunderbird-password-06.png){.thumbnail .w-600}
>>

> [!primary]
>
> **POP-Konfiguration**
>
> Wenn Sie eine POP-Konfiguration für Ihre E-Mail-Adresse wünschen, ersetzen Sie die Einstellungen von **Schritt 3** durch die folgenden:
>
> Einstellungen für den Empfangsserver:
>
> - **Protokoll**: POP3
> - **Servername**: pro?.mail.ovh.net (ersetzen Sie das "?" durch die Nummer Ihres Servers)
> - **Port**: 995
> - **Verbindungssicherheit**: SSL/TLS
> - **Authentifizierungsmethode**: Normales Passwort
> - **Benutzername**: Ihre vollständige E-Mail-Adresse

### Verwenden der E-Mail-Adresse

Sobald Ihre E-Mail-Adresse konfiguriert ist, können Sie sie verwenden! Sie können nun E-Mails senden und empfangen.

OVHcloud bietet auch eine Webanwendung, mit der Sie auf Ihre E-Mail-Adresse über einen Internetbrowser zugreifen können. Um auf das OVHcloud-Webmail zuzugreifen, klicken Sie auf [diesen Link](/links/web/email). Sie können sich damit anmelden, indem Sie die Zugangsdaten für Ihre E-Mail-Adresse verwenden.

### Sichern einer Sicherungskopie Ihrer E-Mail-Adresse

Wenn Sie eine Aktion durchführen müssen, die möglicherweise zum Verlust der Daten in Ihrem E-Mail-Konto führen könnte, empfehlen wir Ihnen, vorher eine Sicherungskopie des betreffenden E-Mail-Kontos zu erstellen. Hierfür können Sie den Abschnitt "**Exportieren**" im Teil "**Thunderbird**" unserer Anleitung "[Manuelles Migrieren Ihrer E-Mail-Adresse](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration#exporter)" konsultieren.

### Ändern der bestehenden Einstellungen

Wenn Ihr E-Mail-Konto bereits konfiguriert ist und Sie auf die Kontoeinstellungen zugreifen müssen, um sie zu ändern:

1. Klicken Sie auf das Menü `☰`{.action} in der oberen horizontalen Leiste.
2. Klicken Sie auf `Kontoeinstellungen`{.action}.

![Thunderbird](images/configuration-thunderbird-win-07.png){.thumbnail .w-600}

- Um die Einstellungen zu ändern, die mit dem **Empfang** von E-Mails zusammenhängen, klicken Sie auf `Servereinstellungen`{.action} in der linken Spalte unter Ihrer E-Mail-Adresse.

![thunderbird](images/configuration-thunderbird-emp-win-08.png){.thumbnail .w-600}

- Um die Einstellungen zu ändern, die mit dem **Senden** von E-Mails zusammenhängen, klicken Sie auf `Ausgehender Server (SMTP)`{.action} am unteren Ende der linken Spalte.
- Klicken Sie auf die betreffende E-Mail-Adresse in der Liste und dann auf `Bearbeiten`{.action}.

![thunderbird](images/configuration-thunderbird-emp-win-09.png){.thumbnail .w-600}

## Weiterführende Informationen <a name="go-further"></a>

> [!primary]
>
> Für weitere Informationen zur Konfiguration einer E-Mail-Adresse im Thunderbird-Client besuchen Sie bitte das [Mozilla-Supportcenter](https://support.mozilla.org/products/thunderbird).

[Erste Schritte mit der E-Mail Pro-Lösung](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.