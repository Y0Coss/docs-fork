---
title: 'MX Plan / Zimbra Starter - Hinzufügen eines E-Mail-Kontos in der neuen Outlook-App für Windows'
excerpt: "Erfahren Sie, wie Sie Ihre E-Mail-Adresse im neuen Outlook für Windows konfigurieren."
updated: 2025-09-26
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

Die E-Mail-Adressen der Angebote **MX Plan** und [Zimbra](/links/web/emails-zimbra) Starter können in einer kompatiblen E-Mail-Software konfiguriert werden. Dies ermöglicht das Senden und Empfangen von Nachrichten über die gewünschte Anwendung.

Die **neue Outlook-App** ersetzt seit dem 1. Januar 2025 die **Mail-App** unter Windows. Weitere Informationen hierzu finden Sie auf der offiziellen Microsoft-Seite « [Outlook für Windows: Die Zukunft von E-Mail, Kalender und Kontakten unter Windows 11](https://support.microsoft.com/office/outlook-for-windows-the-future-of-mail-calendar-and-people-on-windows-11-715fc27c-e0f4-4652-9174-47faa751b199) ».

**Erfahren Sie, wie Sie Ihre E-Mail-Adresse des MX Plans in der neuen Outlook-App für Windows konfigurieren.**

## Voraussetzungen

- Sie benötigen eine vorab konfigurierte OVHcloud-E-Mail-Lösung, wie z.B.:
    - **MX Plan**, angeboten mit unseren [Webhosting-Tarifen](/links/web/hosting) oder enthalten im [kostenlosen 100M-Tarif](/links/web/domains-free-hosting).
    - [Zimbra](/links/web/emails-zimbra) Starter (nur).
- Sie benötigen die [neue Outlook-Version](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627), installiert auf Ihrem Windows-System.
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
> Es ist erforderlich, den entsprechenden Tab in Schritt 3 auszuwählen, der Ihrer Standortauswahl entspricht (**EUROPA** oder **NORDAMERIKA/ASIEN-Pazifik**), um die richtigen Werte zu erhalten.

> [!tabs]
> **Schritt 1**
>> - Öffnen Sie Outlook. Klicken Sie in der linken Spalte auf `Ein Konto hinzufügen`{.action}, um die Konfiguration zu starten.
>>
>> ![outlook](images/configuration-newoutlook-windows-01.png){.thumbnail .w-600}
>>
> **Schritt 2**
>> - Geben Sie Ihre E-Mail-Adresse ein und klicken Sie auf `Weiter`{.action}.
>> - Geben Sie Ihr Passwort ein und klicken Sie auf den Button `Mehr anzeigen`{.action}.
>>
>> ![outlook](images/configuration-newoutlook-windows-02.png){.thumbnail .w-600}
>>
> **Schritt 3 EUROPA**
>> - Geben Sie die folgenden Parameter ein:
>>    - **IMAP-Eingangsserver**: imap.mail.ovh.net **oder** ssl0.ovh.net.
>>    - **Port**: 993
>>    - **Sicherheitstyp**: SSL/TLS
>>    - **SMTP-Benutzername**: Die E-Mail-Adresse, die Sie hinzufügen.
>>    - **SMTP-Ausgangsserver**: smtp.mail.ovh.net **oder** ssl0.ovh.net.
>>    - **Port**: 465
>>    - **Sicherheitstyp**: SSL/TLS
>>    - **Passwort**: Lassen Sie dieses Feld leer, das zuvor eingegebene Passwort wird verwendet.
>> - Klicken Sie auf `Weiter`{.action}, um die Konfiguration abzuschließen.
>>
>> ![outlook](images/configuration-newoutlook-windows-03.png){.thumbnail .w-600}
>>
> **Schritt 3 NORDAMERIKA/ASIEN-Pazifik**
>> - Geben Sie die folgenden Parameter ein:
>>    - **IMAP-Eingangsserver**: imap.mail.ovh.ca
>>    - **Port**: 993
>>    - **Sicherheitstyp**: SSL/TLS
>>    - **SMTP-Benutzername**: Die E-Mail-Adresse, die Sie hinzufügen.
>>    - **SMTP-Ausgangsserver**: smtp.mail.ovh.ca
>>    - **Port**: 465
>>    - **Sicherheitstyp**: SSL/TLS
>>    - **Passwort**: Lassen Sie dieses Feld leer, das zuvor eingegebene Passwort wird verwendet.
>> - Klicken Sie auf `Weiter`{.action}, um die Konfiguration abzuschließen.
>>
>> ![outlook](images/configuration-newoutlook-windows-03ca.png){.thumbnail .w-600}

### E-Mail-Adresse verwenden <a name="use-account"></a>

Sobald die E-Mail-Adresse konfiguriert ist, können Sie sie sofort verwenden! Sie können nun Nachrichten senden und empfangen.

OVHcloud bietet außerdem eine Webanwendung, über die Sie auf Ihre E-Mail-Adresse zugreifen können. Diese ist über den Webbrowser unter der Adresse [Webmail](/links/web/email) erreichbar. Sie können sich damit anmelden, indem Sie die Zugangsdaten Ihrer E-Mail-Adresse verwenden.

### Bestehende Einstellungen ändern <a name="modify-settings"></a>

Die Outlook-App ermöglicht nicht die Änderung der Servereinstellungen für Ihr E-Mail-Konto.

Wenn Ihr E-Mail-Konto bereits konfiguriert ist und Sie es erneut konfigurieren möchten, müssen Sie es zuerst löschen und neu erstellen:

- Klicken Sie auf das Einstellungssymbol « &#9965; » am unteren Ende der linken Spalte.
- Im Bereich « Ihre Konten » klicken Sie auf `Verwalten`{.action} rechts neben der betreffenden E-Mail-Adresse.

![outlook](images/configuration-newoutlook-windows-04.png){.thumbnail .w-600}

- Scrollen Sie nach unten.
- Klicken Sie auf `Löschen`{.action}, um den Löschvorgang zu starten.
- Bestimmen Sie, ob Sie das Konto nur von diesem Gerät oder auch von anderen Geräten, die Outlook verwenden, löschen möchten.

![outlook](images/configuration-newoutlook-windows-05.png){.thumbnail .w-600}

> [!success]
>
> Nachdem Sie das E-Mail-Konto gelöscht haben, folgen Sie den Anweisungen im Abschnitt « [Konto hinzufügen](#add-account) » dieser Dokumentation.

### Allgemeine Senden- und Empfangseinstellungen <a name="settings-account"></a>

#### Empfangseinstellungen IMAP und POP <a name="imap-pop"></a>

Für den Empfang von E-Mails empfehlen wir die Verwendung von **IMAP**. Sie können jedoch auch **POP** auswählen.

> [!warning]
>
> Es ist erforderlich, den richtigen Wert für Ihre Standortauswahl (**EUROPA** oder **NORDAMERIKA/ASIEN-Pazifik**) zu überprüfen.

Wählen Sie den entsprechenden Tab je nach Konfigurationstyp:

> [!tabs]
> **IMAP-Konfiguration**
>>
>> - **Benutzername**: Geben Sie die **vollständige** E-Mail-Adresse ein.
>> - **Passwort**: Geben Sie das Passwort der E-Mail-Adresse ein.
>> - **EUROPA-Eingangsserver**: imap.mail.ovh.net **oder** ssl0.ovh.net.
>> - **NORDAMERIKA/ASIEN-Pazifik-Eingangsserver**: imap.mail.ovh.ca.
>> - **Port**: 993.
>> - **Sicherheitstyp**: SSL/TLS.
>>
> **POP-Konfiguration**
>>
>> - **Benutzername**: Geben Sie die **vollständige** E-Mail-Adresse ein.
>> - **Passwort**: Geben Sie das Passwort der E-Mail-Adresse ein.
>> - **EUROPA-Eingangsserver**: pop.mail.ovh.net **oder** ssl0.ovh.net.
>> - **NORDAMERIKA/ASIEN-Pazifik-Eingangsserver**: pop.mail.ovh.ca.
>> - **Port**: 995.
>> - **Sicherheitstyp**: SSL/TLS.

#### Senden von E-Mails (SMTP) <a name="smtp"></a>

Für den Versand von E-Mails verwenden Sie die folgenden **SMTP**-Parameter:

**SMTP-Konfiguration**

- **Benutzername**: Geben Sie die **vollständige** E-Mail-Adresse ein.
- **Passwort**: Geben Sie das Passwort der E-Mail-Adresse ein.
- **EUROPA-Ausgangsserver**: smtp.mail.ovh.net **oder** ssl0.ovh.net.
- **NORDAMERIKA/ASIEN-Pazifik-Ausgangsserver**: smtp.mail.ovh.ca.
- **Port**: 465.
- **Sicherheitstyp**: SSL/TLS.

## Weiterführende Informationen

> [!primary]
>
> Für weitere Informationen zur Konfiguration einer E-Mail-Adresse in der neuen Outlook-App für Windows besuchen Sie [das Microsoft-Hilfezentrum](https://support.microsoft.com/office/start-using-new-outlook-for-windows-4395454d-cb2f-4c16-bb24-fa4bb36650ae).

[Erste Schritte mit dem MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities)

[Erste Schritte mit dem Zimbra-Angebot](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Für spezialisierte Dienstleistungen (SEO, Entwicklung etc.) kontaktieren Sie die [OVHcloud-Partner](/links/partner).

Wenn Sie Unterstützung bei der Verwendung und Konfiguration Ihrer OVHcloud-Lösungen benötigen, empfehlen wir Ihnen, unsere [Support-Angebote](/links/support) zu konsultieren.

Treten Sie unserer [Nutzercommunity](/links/community) bei.