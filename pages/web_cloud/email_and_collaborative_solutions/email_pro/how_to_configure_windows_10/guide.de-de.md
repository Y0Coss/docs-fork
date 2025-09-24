---
title: "E-Mail Pro - Konfigurieren Ihres E-Mail-Profis in der neuen Outlook-App für Windows"
excerpt: "Erfahren Sie, wie Sie Ihre E-Mail-Adresse von E-Mail Pro in der neuen Outlook-App für Windows konfigurieren."
updated: 2025-09-02
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

Die E-Mail-Adressen des [E-Mail-Pro](/links/web/email-pro)-Angebots können in einer kompatiblen E-Mail-Software konfiguriert werden. Dies ermöglicht es, Nachrichten über die gewünschte Anwendung zu senden und zu empfangen.

Die **neue Outlook-App** ersetzt seit dem 1. Januar 2025 die **Mail-App** unter Windows. Für weitere Informationen hierzu besuchen Sie die offizielle Microsoft-Seite « [Outlook für Windows: Die Zukunft von E-Mail, Kalender und Kontakten unter Windows 11](https://support.microsoft.com/office/outlook-pour-windows-l-avenir-du-courrier-du-calendrier-et-des-personnes-sur-windows-11-715fc27c-e0f4-4652-9174-47faa751b199) ».

**Erfahren Sie, wie Sie Ihre E-Mail-Pro-Adresse in der neuen Outlook-App für Windows konfigurieren.**

## Voraussetzungen

- Sie benötigen eine [E-Mail-Pro](/links/web/email-pro)-Adresse.
- Sie benötigen die [neue Outlook-App](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) für Windows.
- Sie benötigen die Zugangsdaten für die E-Mail-Adresse, die Sie konfigurieren möchten.

> [!warning]
>
> Diese Dokumentation gilt ausschließlich für die **neue Outlook-App** und nicht für den « [klassischen Outlook](https://support.microsoft.com/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) », der in der Microsoft 365-Suite verfügbar ist oder zuvor auf Ihrem Computer installiert wurde.

/// details | Informationen zur Verwaltung und Konfiguration von OVHcloud-Diensten

OVHcloud stellt Ihnen verschiedene Dienste zur Verfügung, deren Konfiguration, Verwaltung und Verantwortung in Ihrer Zuständigkeit liegen. Sie sind daher dafür verantwortlich, deren ordnungsgemäßen Betrieb sicherzustellen.

Wir stellen Ihnen diesen Leitfaden zur Verfügung, um Sie bei gängigen Aufgaben bestmöglich zu unterstützen. Dennoch empfehlen wir Ihnen, im Falle von Schwierigkeiten einen [spezialisierten Partner](https://marketplace.ovhcloud.com/c/support-collaboration) zu kontaktieren und/oder sich an den Dienstanbieter zu wenden. Wir können keine weitere Unterstützung leisten. Weitere Informationen finden Sie im Abschnitt « Weiterführende Informationen » dieses Leitfadens.

///

## In der praktischen Anwendung

### Konto hinzufügen <a name="add-account"></a>

> [!warning]
>
> In unserem Beispiel verwenden wir den Serverhinweis: pro?.mail.ovh.net. Sie müssen das «?» durch die Nummer Ihres E-Mail-Pro-Servers ersetzen.
> 
> Den Servernamen finden Sie in Ihrem [OVHcloud-Kundencenter](/links/manager), im Bereich `Web Cloud`{.action} und dann `E-Mail Pro`{.action}. Der Servername ist im Bereich **Verbindung** des Tabs `Allgemeine Informationen`{.action} sichtbar.

> [!tabs]
> **Schritt 1**
>> - Öffnen Sie Outlook. Klicken Sie in der linken Spalte auf `Ein Konto hinzufügen`{.action}, um die Konfiguration zu starten.
>>
>> ![outlook](images/configuration-newoutlook-windows-01.png){.thumbnail .w-400}
>>
> **Schritt 2**
>> - Geben Sie Ihre E-Mail-Adresse ein und klicken Sie auf `Weiter`{.action}.
>> - Geben Sie Ihr Passwort ein und klicken Sie auf den Button `Mehr anzeigen`{.action}.
>>
>> ![outlook](images/configuration-newoutlook-windows-02.png){.thumbnail .w-400}
>>
> **Schritt 3**
>> - Geben Sie die folgenden Parameter ein:
>>    - **IMAP-Eingangsserver**: pro?.mail.ovh.net
>>    - **Port**: 993
>>    - **Sicherheitstyp**: SSL/TLS
>>    - **SMTP-Benutzername**: Die E-Mail-Adresse, die Sie hinzufügen.
>>    - **SMTP-Ausgangsserver**: pro?.mail.ovh.net
>>    - **Port**: 587
>>    - **Sicherheitstyp**: STARTTLS
>>    - **Passwort**: Lassen Sie dieses Feld leer, das zuvor eingegebene Passwort wird verwendet.
>> - Klicken Sie auf `Weiter`{.action}, um die Konfiguration abzuschließen.
>>
>> ![outlook](images/configuration-newoutlook-windows-emp-03.png){.thumbnail .w-400}

### E-Mail-Adresse verwenden <a name="use-account"></a>

Sobald die E-Mail-Adresse konfiguriert ist, können Sie sie sofort verwenden! Sie können nun Nachrichten senden und empfangen.

OVHcloud bietet außerdem eine Webanwendung, über die Sie auf Ihre E-Mail-Adresse zugreifen können. Diese ist über den Webbrowser unter der Adresse [Webmail](/links/web/email) erreichbar. Sie können sich damit anmelden, indem Sie die Zugangsdaten Ihrer E-Mail-Adresse verwenden.

### Bestehende Einstellungen ändern <a name="modify-settings"></a>

Die Outlook-App ermöglicht nicht die Änderung der Servereinstellungen für Ihr E-Mail-Konto.

Wenn Ihr E-Mail-Konto bereits konfiguriert ist und Sie es erneut konfigurieren möchten, müssen Sie es löschen und neu erstellen:

- Klicken Sie auf das Einstellungssymbol « &#9965; » am unteren Ende der linken Spalte.
- Im Bereich « Ihre Konten » klicken Sie auf `Verwalten`{.action} rechts neben der betreffenden E-Mail-Adresse.

![outlook](images/configuration-newoutlook-windows-04.png){.thumbnail .w-400}

- Scrollen Sie nach unten.
- Klicken Sie auf `Löschen`{.action}, um den Löschvorgang zu starten.
- Bestimmen Sie, ob Sie das Konto nur von diesem Gerät oder auch von anderen Geräten, die Outlook verwenden, löschen möchten.

![outlook](images/configuration-newoutlook-windows-emp-05.png){.thumbnail .w-400}

> [!success]
>
> Nachdem Sie das E-Mail-Konto gelöscht haben, folgen Sie den Anweisungen im Abschnitt « [Konto hinzufügen](#add-account) » in dieser Dokumentation.

### Allgemeine Senden- und Empfangseinstellungen <a name="settings-account"></a>

#### IMAP- und POP-Empfangseinstellungen <a name="imap-pop"></a>

Für den Empfang von E-Mails empfehlen wir die Verwendung von **IMAP**. Sie können jedoch auch **POP** auswählen.

Wählen Sie den entsprechenden Tab je nach Konfigurationstyp:

> [!tabs]
> **IMAP-Konfiguration**
>>
>> - **Benutzername**: Geben Sie die **vollständige** E-Mail-Adresse ein.
>> - **Passwort**: Geben Sie das Passwort der E-Mail-Adresse ein.
>> - **Eingangsserver**: pro?.mail.ovh.net (ersetzen Sie «?» durch die Nummer Ihres Servers).
>> - **Port**: 993.
>> - **Sicherheitstyp**: SSL/TLS.
>>
> **POP-Konfiguration**
>>
>> - **Benutzername**: Geben Sie die **vollständige** E-Mail-Adresse ein.
>> - **Passwort**: Geben Sie das Passwort der E-Mail-Adresse ein.
>> - **Eingangsserver**: pro?.mail.ovh.net (ersetzen Sie «?» durch die Nummer Ihres Servers).
>> - **Port**: 995.
>> - **Sicherheitstyp**: SSL/TLS.

#### SMTP-Sendeinstellungen <a name="smtp"></a>

Für den Versand von E-Mails finden Sie unten die zu verwendenden **SMTP**-Parameter:

**SMTP-Konfiguration**

- **Benutzername**: Geben Sie die **vollständige** E-Mail-Adresse ein.
- **Passwort**: Geben Sie das Passwort der E-Mail-Adresse ein.
- **Ausgangsserver**: pro?.mail.ovh.net (ersetzen Sie «?» durch die Nummer Ihres Servers).
- **Port**: 587.
- **Sicherheitstyp**: STARTTLS.

## Weiterführende Informationen

> [!primary]
>
> Für weitere Informationen zur Konfiguration einer E-Mail-Adresse in der neuen Outlook-App für Windows besuchen Sie [das Microsoft-Hilfezentrum](https://support.microsoft.com/office/start-using-new-outlook-for-windows-4395454d-cb2f-4c16-bb24-fa4bb36650ae).

[Erste Schritte mit der E-Mail-Pro-Lösung](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config)

Für spezialisierte Dienstleistungen (Suchmaschinenoptimierung, Entwicklung etc.) kontaktieren Sie die [OVHcloud-Partner](/links/partner).

Wenn Sie Unterstützung bei der Verwendung und Konfiguration Ihrer OVHcloud-Lösungen benötigen, empfehlen wir Ihnen, unsere [Support-Angebote](/links/support) zu konsultieren.

Treten Sie unserer [Nutzercommunity](/links/community) bei.