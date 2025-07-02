---
title: "Zimbra Pro - Konfiguration Ihres E-Mail-Accounts via EWS auf Outlook für Mac"
excerpt: "So konfigurieren Sie Ihre Zimbra Pro E-Mail-Adresse auf Outlook für macOS über das EWS-Protokoll"
updated: 2025-06-27
---

<style>
.h-500 {
  max-height:500px !important;
}
</style>

## Ziel

> [!primary]
> Diese Anleitung richtet sich an Kunden, die über ein E-Mail-Angebot von [Zimbra Pro] verfügen (/links/web/emails-zimbra). Diese Dienstleistung wird ab Juli 2025 als Beta verfügbar sein.

Zimbra Pro Accounts können auf einem Mac mit dem EWS Protokoll konfiguriert werden (**E**xchange **W**eb **S**services). So können Sie alle kollaborativen Funktionen Ihrer E-Mail-Adresse in einem Schritt konfigurieren. Die App [Outlook auf macOS](https://apps.apple.com/de/app/microsoft-outlook/id985367838?mt=12) ist im Apple App Store verfügbar.

**Erfahren Sie, wie Sie Ihre Zimbra Pro E-Mail-Adresse auf Outlook für macOS über das EWS-Protokoll konfigurieren.**

> [!warning]
>
> OVHcloud stellt Ihnen Dienste zur Verfügung, für deren Konfiguration, Verwaltung und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt in Ihrer Verantwortung, das ordnungsgemäße Funktionieren dieser Dienste sicherzustellen.
>
> Dieses Handbuch soll Ihnen bei der Durchführung häufiger Aufgaben helfen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Partner](https://marketplace.ovhcloud.com/c/support-collaboration) und/oder den Herausgeber des Dienstes zu kontaktieren. Für externe Dienstleistungen bieten wir leider keine Unterstützung. Weitere Informationen finden Sie im Abschnitt [Weiterführende Informationen](#go-further) dieser Anleitung.

## Voraussetzungen

- Sie besitzen eine E-Mail-Adresse [Zimbra Pro](/links/web/emails-zimbra).
- Sie haben die App [Outlook auf macOS](https://apps.apple.com/de/app/microsoft-outlook/id985367838?mt=12).
- Sie haben die Login-Daten der E-Mail-Adresse, die Sie einrichten möchten.

## In der Praxis

### Konto <a name="add-account"></a> hinzufügen

- **Beim ersten Start der Outlook-Anwendung**: Ein Konfigurationsassistent erscheint direkt und fordert Sie zur Eingabe der ersten E-Mail-Adresse auf, die Sie hinzufügen möchten.

- **Wenn bereits ein Account für die Outlook-App eingerichtet ist**:
    1. Klicken Sie in der Menüleiste oben auf `Extras`{.action}.
    2. Klicken Sie auf `Konten`{.action}.
    3. Klicken Sie im angezeigten Fenster „Accounts“ unten links auf `+`{.action} und dann auf `Neuer Account`{.action}.

![mail macOS](images/outlook-macos-add-step00.png){.thumbnail .h-500}

Folgen Sie den Installationsschritten, indem Sie nacheinander auf die unten stehenden **3** Registerkarten klicken:

> [!tabs]
> **Schritt 1**
>>
>> Geben Sie Ihre E-Mail-Adresse unter „E-Mail-Adresse“ ein und klicken Sie auf `Weiter`{.action}.
>>
>> ![mail macos](images/outlook-macos-add-step01.png){.thumbnail .h-500}
>>
> **Schritt 2**
>>
>> Zwei Szenarien sind möglich:
>>
>> - **Wenn das Fenster „IMAP/POP“ angezeigt wird** : Klicken Sie auf `Dies ist kein POP/IMAP-Konto`{.action} und wählen Sie `Exchange`{.action} aus dem Fenster „Anbieter auswählen“.
>> - **Wenn Sie direkt auf „Anbieter auswählen“** treffen, wählen Sie `Exchange`{.action}.
>>
>> ![mail macos](images/outlook-macos-add-step02.png){.thumbnail .h-500}
>>
> **Schritt 3**
>>
>> Überprüfen und vervollständigen Sie die folgenden Informationen:
>>
>> - **Methode**: Wählen Sie `Benutzername und Passwort`.
>> - **E-Mail-Adresse**: Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **DOMAIN\Benutzername oder E-Mail-Adresse**: Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **Passwort**: Geben Sie das Passwort Ihrer E-Mail-Adresse ein.
>> - **Server**: Geben Sie „zimbra1.mail.ovh.net“ ein.
>>
>> Um die Konfiguration abzuschließen, tippen Sie auf `Konto hinzufügen`{.action} und wählen Sie die Funktionen aus, die Sie auf Ihrem Mac erkunden möchten.
>>
>> ![mail macos](images/outlook-macos-add-step03.png){.thumbnail .h-500}
>>

> [!warning]
>
> Wenn Sie nach dem Befolgen der oben genannten Konfigurationsschritte einen Fehler beim Senden oder Empfangen feststellen, lesen Sie den Abschnitt „[Vorhandene Einstellungen ändern](#modify-settings)“ in dieser Anleitung.

### E-Mail-Adresse verwenden

Sobald die E-Mail-Adresse eingerichtet ist, können Sie sie verwenden! Sie können ab sofort Nachrichten senden und empfangen sowie Ihre Kalender und Aufgaben verwalten.

OVHcloud bietet auch eine Web-Anwendung an, mit der Sie über einen Webbrowser auf Ihre E-Mail-Adresse zugreifen können. Sie können sich mit den Zugangsdaten Ihrer E-Mail-Adresse im [OVHcloud Webmail](/links/web/email) einloggen. Wenn Sie Fragen zur Verwendung haben, lesen Sie unsere Anleitung „[Zimbra Webmail verwenden](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra)“.

### Wie kann ich vorhandene Einstellungen ändern?<a name="modify-settings"></a>

Um die Einstellungen eines bereits konfigurierten E-Mail-Accounts zu ändern, befolgen Sie die folgenden Anweisungen:

1. Klicken Sie in der Menüleiste oben auf `Extras`{.action}.
1. Klicken Sie auf `Konten`{.action}.
1. Wählen Sie in der linken Spalte Ihr Konto aus.
1. Klicken Sie auf `Erweitert...`{.action} unten rechts.

![Outlook macos](images/outlook-macos-modify-01.png){.thumbnail .h-500}

Die Einstellungen finden Sie in **Schritt 3** im Kapitel [Account hinzufügen](#add-account).

### Wie lösche ich einen E-Mail-Account?<a name="delete-account"></a>

1. Klicken Sie in der Menüleiste oben auf `Extras`{.action}.
1. Klicken Sie auf `Konten`{.action}.
1. Wählen Sie in der linken Spalte Ihr Konto aus.
1. Klicken Sie unten links auf `-`{.action}

![Outlook macos](images/outlook-macos-delete-01.png){.thumbnail .h-500}


## Weitere Informationen <a name="go-further"></a>

> [!primary]
>
> Weitere Informationen zum Einrichten einer E-Mail-Adresse in der Mail App auf macOS finden Sie im [Apple Help Center](https://support.apple.com/de-de/102619).

Für spezielle Dienstleistungen (Referenzierung, Entwicklung usw.) wenden Sie sich bitte an die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Verwendung und Konfiguration Ihrer OVHcloud Lösungen benötigen, empfehlen wir Ihnen unsere verschiedenen [Support-Angebote](/links/support).

Für den Austausch mit unserer [User Community](/links/community).