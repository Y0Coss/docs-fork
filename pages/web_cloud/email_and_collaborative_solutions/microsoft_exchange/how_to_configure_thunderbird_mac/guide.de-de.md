---
title: 'Exchange - E-Mail-Adresse in Thunderbird auf macOS konfigurieren'
excerpt: 'Erfahren Sie, wie Sie Ihre Exchange-E-Mail-Adresse in Thunderbird für macOS konfigurieren'
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

Exchange-Konten können auf verschiedenen kompatiblen E-Mail-Programmen konfiguriert werden. Dies ermöglicht es Ihnen, Ihre E-Mail-Adresse von Ihrem Gerät Ihrer Wahl aus zu nutzen. Thunderbird ist ein freies und kostenloses E-Mail-Programm.

**Erfahren Sie, wie Sie Ihre Exchange-E-Mail-Adresse in Thunderbird für macOS konfigurieren.**

## Voraussetzungen

- Eine [Hosted Exchange](/links/web/emails-hosted-exchange) oder [Private Exchange](/links/web/emails-private-exchange)-E-Mail-Adresse besitzen.
- Das Softwareprogramm Thunderbird auf Ihrem Mac installiert haben.
- Die Zugangsdaten für die E-Mail-Adresse, die Sie konfigurieren möchten, besitzen.

/// details | Informationen zur Verwaltung und Konfiguration der OVHcloud-Dienste

Ce guide vous montre comment utiliser des solutions OVHcloud avec des outils externes ainsi que les modifications à apporter dans des contextes spécifiques. Il se peut que vous deviez adapter les instructions en fonction de votre situation.

Si vous éprouvez des difficultés à effectuer ces opérations, nous vous recommandons de contacter un [prestataire de services spécialisé](/links/partner) et/ou d'en discuter avec notre communauté. OVHcloud ne peut pas vous fournir d’assistance technique sur l'utilisation d'outils externes. Plus d'informations dans la section [Aller plus loin](#gofurther) de ce guide.

///

## In der praktischen Anwendung

> [!primary]
>
> Dans notre exemple, nous utilisons la mention serveur : ex?.mail.ovh.net. Vous devrez remplacer le "?" par le chiffre désignant le serveur de votre service Exchange.
>
> Pour retrouver le nom du serveur :
>
> 1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
> 2. Rendez-vous dans la partie `Web Cloud`{.action}.
> 3. Dans la rubrique `MICROSOFT`, cliquez sur `Exchange`{.action}.
> 4. Sélectionnez la plateforme concernée.
> 5. Le nom du serveur est visible dans le cadre **Connexion** de l'onglet `Informations Générales`{.action}.

### Konto hinzufügen

- **Beim ersten Start der Anwendung**: Erscheint ein Konfigurationsassistent, der Sie auffordert, Ihre E-Mail-Adresse einzugeben.

- **Wenn bereits ein Konto konfiguriert ist**:

    1. Klicken Sie auf das Menü `☰`{.action} in der oberen horizontalen Leiste.
    2. Klicken Sie auf `Neues Konto`{.action}.
    3. Klicken Sie auf `E-Mail-Adresse`{.action}.

![thunderbird](images/configuration-thunderbird-mac-01.png){.thumbnail .w-600}

Folgen Sie den Konfigurationsschritten, indem Sie nacheinander auf die folgenden **5** Register klicken:

> [!tabs]
> **Schritt 1**
>>
>> Geben Sie in dem angezeigten Fenster folgende zwei Informationen ein:
>>
>>  - Ihren vollständigen Namen (Anzeigename).
>>  - Die zu konfigurierende E-Mail-Adresse.
>>
>> Klicken Sie auf `Weiter`{.action}, um die Einstellungen abzuschließen.
>>
>> ![thunderbird](images/configuration-thunderbird-exchange-02.png){.thumbnail .w-600}
>>
> **Schritt 2**
>>
>> Wenn Thunderbird einen OVHcloud-Domänennamen erkennt, wird eine automatische Konfiguration für das MX Plan-Angebot vorgeschlagen. Klicken Sie auf `KONFIGURATION ÄNDERN`{.action}.
>>
>> ![thunderbird](images/configuration-thunderbird-ssl0-03.png){.thumbnail .w-600}
>>
> **Schritt 3**
>>
>> Empfangsservereinstellungen:
>>
>>  - **Protokoll**: IMAP
>>  - **Hostname**: ex?.mail.ovh.net (ersetzen Sie das „?“ durch die Nummer Ihres Servers)
>>  - **Port**: 993
>>  - **Verbindungssicherheit**: SSL/TLS
>>  - **Authentifizierungsart**: Normales Passwort
>>  - **Benutzername**: Ihre vollständige E-Mail-Adresse
>>
>> ![thunderbird](images/configuration-thunderbird-exchange-04.png){.thumbnail .w-600}
>>
> **Schritt 4**
>>
>> Einstellungen des Sendeservers:
>>
>>  - **Protokoll**: SMTP 
>>  - **Hostname**: ex?.mail.ovh.net (ersetzen Sie das „?“ durch die Nummer Ihres Servers)
>>  - **Port**: 587
>>  - **Verbindungssicherheit**: STARTTLS
>>  - **Authentifizierungsart**: Normales Passwort
>>  - **Benutzername**: Ihre vollständige E-Mail-Adresse
>> 
>> 1\. Klicken Sie auf `Testen`{.action}, um die eingegebenen Einstellungen zu überprüfen.
>> 2\. Klicken Sie auf `Weiter`{.action}, um diese Einstellungen zu bestätigen.
>>
>> ![thunderbird](images/configuration-thunderbird-exchange-05.png){.thumbnail .w-600}
>>
> **Schritt 5**
>>
>> Geben Sie das Passwort ein, das mit der E-Mail-Adresse verknüpft ist, und klicken Sie dann auf `Weiter`{.action}, um die Konfiguration abzuschließen.
>>
>> ![thunderbird](images/configuration-thunderbird-password-06.png){.thumbnail .w-600}
>>

> [!primary]
>
> **POP-Konfiguration**
>
> Wenn Sie eine POP-Konfiguration für Ihre E-Mail-Adresse wünschen, ersetzen Sie die Einstellungen des **Schritts 3** durch folgende:
>
> Empfangsservereinstellungen:
>
> - **Protokoll**: POP3
> - **Hostname**: ex?.mail.ovh.net (ersetzen Sie das „?“ durch die Nummer Ihres Servers)
> - **Port**: 995
> - **Verbindungssicherheit**: SSL/TLS
> - **Authentifizierungsart**: Normales Passwort
> - **Benutzername**: Ihre vollständige E-Mail-Adresse

### E-Mail-Adresse nutzen

Sobald Ihre E-Mail-Adresse konfiguriert ist, können Sie sie nutzen! Sie können nun E-Mails senden und empfangen.

OVHcloud bietet außerdem eine Webanwendung an, mit der Sie Ihre E-Mail-Adresse über einen Webbrowser zugreifen können. Um auf das OVHcloud-Webmail zuzugreifen, klicken Sie auf [diesen Link](/links/web/email). Sie können sich dort mit den Zugangsdaten Ihrer E-Mail-Adresse anmelden.

### Sicherung Ihrer E-Mail-Adresse erstellen

Wenn Sie eine Aktion durchführen müssen, die zu Datenverlusten Ihres E-Mail-Kontos führen könnte, empfehlen wir Ihnen, vorher eine Sicherung des betroffenen E-Mail-Kontos durchzuführen. Dazu konsultieren Sie den Abschnitt „**Exportieren**“ im Bereich „**Thunderbird**“ unseres Leitfadens „[Manuelle Migration Ihrer E-Mail-Adresse](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration#exporter)“.

### Vorhandene Einstellungen ändern

Wenn Ihr E-Mail-Konto bereits konfiguriert ist und Sie die Einstellungen des Kontos ändern müssen:

1. Klicken Sie auf das Menü `☰`{.action} in der oberen horizontalen Leiste.
2. Klicken Sie auf `Kontoeinstellungen`{.action}.

![Thunderbird](images/configuration-thunderbird-mac-07.png){.thumbnail .w-600}

- Um die Einstellungen, die mit der **Empfangs**-Funktion Ihrer E-Mails verbunden sind, zu ändern, klicken Sie auf `Servereinstellungen`{.action} in der linken Spalte unter Ihrer E-Mail-Adresse.

![thunderbird](images/configuration-thunderbird-exchange-mac-08.png){.thumbnail .w-600}

- Um die Einstellungen, die mit der **Versand**-Funktion Ihrer E-Mails verbunden sind, zu ändern, klicken Sie auf `Ausgehender Server (SMTP)`{.action} ganz unten in der linken Spalte.
- Klicken Sie auf die betroffene E-Mail-Adresse in der Liste, und dann auf `Ändern`{.action}.

![thunderbird](images/configuration-thunderbird-exchange-mac-09.png){.thumbnail .w-600}

## Weiterführende Informationen <a name="go-further"></a>

> [!primary]
>
> Für weitere Informationen zur Konfiguration einer E-Mail-Adresse über den Thunderbird-E-Mail-Client konsultieren Sie [das Mozilla-Hilfezentrum](https://support.mozilla.org/products/thunderbird).

[Erste Schritte mit dem Hosted Exchange-Dienst](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted)

[Erste Schritte mit dem Private Exchange-Dienst](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_private)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.