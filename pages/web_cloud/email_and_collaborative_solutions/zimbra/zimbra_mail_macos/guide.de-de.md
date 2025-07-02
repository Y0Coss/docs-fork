---
title: "Zimbra Pro - Konfiguration Ihres E-Mail-Accounts via EWS in Mail auf Mac"
excerpt: "Erfahren Sie, wie Sie Ihre Zimbra Pro E-Mail-Adresse über das EWS-Protokoll in der Mail App auf dem Mac einrichten."
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

Zimbra Pro Accounts können auf einem macOS mit dem EWS Protokoll konfiguriert werden (**E**xchange **W**eb **S**services). So können Sie alle kollaborativen Funktionen Ihrer E-Mail-Adresse in einem Schritt konfigurieren. Die Mail App ist nativ auf macOS verfügbar.

**Erfahren Sie, wie Sie Ihre Zimbra Pro E-Mail-Adresse über das EWS-Protokoll auf der Mail App auf dem Mac einrichten.**

> [!warning]
>
> OVHcloud stellt Ihnen Dienste zur Verfügung, für deren Konfiguration, Verwaltung und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt in Ihrer Verantwortung, das ordnungsgemäße Funktionieren dieser Dienste sicherzustellen.
>
> Dieses Handbuch soll Ihnen bei der Durchführung häufiger Aufgaben helfen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Partner](https://marketplace.ovhcloud.com/c/support-collaboration) und/oder den Herausgeber des Dienstes zu kontaktieren. Für externe Dienstleistungen bieten wir leider keine Unterstützung. Weitere Informationen finden Sie im Abschnitt [Weiterführende Informationen](#go-further) dieser Anleitung.

## Voraussetzungen

- Sie besitzen eine E-Mail-Adresse [Zimbra Pro](/links/web/emails-zimbra).
- Sie haben die Mail App auf Ihrem Mac.
- Sie haben die Login-Daten der E-Mail-Adresse, die Sie einrichten möchten.

## In der Praxis

### Konto <a name="add-account"></a> hinzufügen

- **Beim ersten Start der Mail App** erscheint ein Konfigurationsassistent direkt und Sie werden aufgefordert, Ihren Account-Typ auszuwählen.

- **Wenn bereits ein Account für die Mail App eingerichtet ist**:
    - Klicken Sie auf `Mail`{.action} in der Menüleiste oben auf Ihrem Bildschirm.
    - Klicken Sie auf `Konten`{.action}.
    - Klicken Sie im angezeigten Fenster „Internetkonten“ auf `Einen Account hinzufügen`{.action}

![mail macOS](images/mail-macos-add-step00.png){.thumbnail .h-500}

Folgen Sie den Installationsschritten, indem Sie nacheinander auf die unten stehenden **3** Registerkarten klicken:

> [!tabs]
> **Schritt 1**
>>
>> - Wählen Sie `Microsoft Exchange`{.action} aus.
>> - Legen Sie einen **Namen** fest und geben Sie Ihre **E-Mail-Adresse** ein.
>> - Klicken Sie dann auf `Verbinden`{.action}.
>>
>> ![mail macos](images/mail-macos-add-step01.png){.thumbnail .h-500}
>>
> **Schritt 2**
>>
>> - Wählen Sie `Manuell konfigurieren`{.action} aus dem angezeigten Fenster.
>> - Geben Sie anschließend zusätzlich zu den bereits eingegebenen Informationen das **Passwort** Ihrer E-Mail-Adresse ein.
>>
>> ![mail macos](images/mail-macos-add-step02.png){.thumbnail .h-500}
>>
> **Schritt 3**
>>
>> Überprüfen und vervollständigen Sie die folgenden Informationen:
>>
>> - **E-Mail-Adresse**: Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **Benutzername**: Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **Passwort**: Geben Sie das Passwort Ihrer E-Mail-Adresse ein.
>> - **Interne URL**: Geben Sie „zimbra1.mail.ovh.net“ ein.
>> - **Externe URL**: Geben Sie „zimbra1.mail.ovh.net“ ein.
>>
>> Um die Konfiguration abzuschließen, tippen Sie auf `Verbinden`{.action} und wählen Sie die Funktionen aus, die Sie auf Ihrem Mac erkunden möchten.
>>
>> ![mail macos](images/mail-macos-add-step04.png){.thumbnail .h-500}
>>
>> > [!warning]
>> >
>> > Es ist normal, wenn die rote Meldung „**Kontoname oder Kennwort nicht überprüfen**“ angezeigt wird, wenn das Fenster zum ersten Mal angezeigt wird. Wenn diese Meldung jedoch nach der Validierung weiterhin angezeigt wird, sind die eingegebenen Informationen fehlerhaft.

> [!warning]
>
> Wenn Sie nach dem Befolgen der oben genannten Konfigurationsschritte einen Fehler beim Senden oder Empfangen feststellen, lesen Sie den Abschnitt „[Vorhandene Einstellungen ändern](#modify-settings)“ in dieser Anleitung.

### E-Mail-Adresse verwenden

Sobald die E-Mail-Adresse eingerichtet ist, können Sie sie verwenden! Sie können ab sofort Nachrichten senden und empfangen sowie Ihre Kalender und Aufgaben verwalten.

OVHcloud bietet auch eine Web-Anwendung an, mit der Sie über einen Webbrowser auf Ihre E-Mail-Adresse zugreifen können. Sie können sich mit den Zugangsdaten Ihrer E-Mail-Adresse im [OVHcloud Webmail](/links/web/email) einloggen. Wenn Sie Fragen zur Verwendung haben, lesen Sie unsere Anleitung „[Zimbra Webmail verwenden](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra)“.

### Wie kann ich vorhandene Einstellungen ändern?<a name="modify-settings"></a>

Die Mail App auf dem Mac erlaubt es nicht, die Servereinstellungen eines Exchange E-Mail-Accounts zu ändern.

Wenn Ihr E-Mail-Account bereits eingerichtet ist und Sie seine Einstellungen ändern möchten, müssen Sie ihn löschen und neu erstellen.

So löschen Sie einen Exchange E-Mail-Account:

1. Klicken Sie in der Menüleiste oben auf `Mail`{.action}.
1. Klicken Sie auf `Accounts`{.action}, und wählen Sie den betreffenden E-Mail-Account aus.
1. Drücken Sie `Account löschen`{.action}.

![mail macos](images/mail-macos-modify-delete-01.png){.thumbnail .h-500}

> [!success]
>
> Nachdem Sie Ihren E-Mail-Account gelöscht haben, folgen Sie den Installationsschritten im Abschnitt „[Account hinzufügen](#add-account)“ in dieser Anleitung.

## Weitere Informationen <a name="go-further"></a>

> [!primary]
>
> Weitere Informationen zum Einrichten einer E-Mail-Adresse in der Mail App auf macOS finden Sie im [Apple Help Center](https://support.apple.com/de-de/102619).

Für spezielle Dienstleistungen (Referenzierung, Entwicklung usw.) wenden Sie sich bitte an die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Verwendung und Konfiguration Ihrer OVHcloud Lösungen benötigen, empfehlen wir Ihnen unsere verschiedenen [Support-Angebote](/links/support).

Für den Austausch mit unserer [User Community](/links/community).