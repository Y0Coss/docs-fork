---
title: "Zimbra Pro - E-Mail-Konto über ActiveSync auf dem klassischen Outlook für Windows konfigurieren"
excerpt: "Erfahren Sie, wie Sie Ihre Zimbra Pro-E-Mail-Adresse auf Outlook für Windows über das ActiveSync-Protokoll konfigurieren"
updated: 2025-12-17
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
.h-500 {
  max-width:500px !important;
}
</style>

## Ziel

> [!primary]
>
> Diese Anleitung richtet sich an Kunden, die über das E-Mail-Angebot [Zimbra Pro](/links/web/emails-zimbra) verfügen. Diese Dienstleistung wird ab Juli 2025 als Beta verfügbar sein.

Zimbra Pro-Konten können unter Windows mit dem ActiveSync-Protokoll konfiguriert werden. Damit können Sie alle Funktionen Ihres E-Mail-Kontos in einem Schritt konfigurieren. Die Outlook-App für Windows ermöglicht den Zugriff auf Ihr Zimbra Pro-E-Mail-Konto über das ActiveSync-Protokoll.

**Erfahren Sie, wie Sie Ihre Zimbra Pro-E-Mail-Adresse auf Outlook für Windows über das ActiveSync-Protokoll konfigurieren.**

## Voraussetzungen

- Über eine E-Mail-Adresse [Zimbra Pro](/links/web/emails-zimbra) verfügen.
- Die Anwendung [klassische Outlook](https://support.microsoft.com/de-de/office/outlook-classic-installieren-oder-wiederherstellen-auf-einem-windows-pc-5c94902b-31a5-4274-abb0-b07f4661edf5) auf Windows besitzen.
- Die Zugangsdaten für die E-Mail-Adresse besitzen, die Sie konfigurieren möchten.

/// details | Informationen zur Verwaltung und Konfiguration der OVHcloud-Dienste

OVHcloud stellt Ihnen Dienste zur Verfügung, deren Konfiguration, Verwaltung und Verantwortung in Ihrem Verantwortungsbereich liegen. Es liegt somit in Ihrer Verantwortung, dass diese ordnungsgemäß funktionieren.

Wir haben diesen Leitfaden erstellt, um Sie bei alltäglichen Aufgaben bestmöglich zu unterstützen. Dennoch empfehlen wir Ihnen, bei Schwierigkeiten einen [spezialisierten Partner](/links/transversal/marketplace-support-collaboration) zu kontaktieren und/oder den Dienstanbieter zu kontaktieren. Wir können Ihnen in diesem Fall keine Unterstützung anbieten. Weitere Informationen finden Sie im Abschnitt „[Weitere Informationen](go-further)“ dieses Leitfadens.

///

## In der praktischen Anwendung

> [!warning]
>
> Vor Beginn der Konfiguration ist wichtig zu wissen, dass die mit Windows 11 kostenlos mitgelieferte Outlook-App mit dem ActiveSync-Protokoll, das für die Konfiguration eines Zimbra Pro-Kontos erforderlich ist, nicht kompatibel ist. Sie müssen die Version **klassische Outlook** verwenden, um die Unterstützung des ActiveSync-Protokolls zu nutzen.
>
> Um klassische Outlook auf Ihrem Windows-Computer zu installieren, laden Sie es von der Microsoft-Seite « [Outlook classic installieren oder wiederherstellen auf einem Windows-PC](https://support.microsoft.com/de-de/office/outlook-classic-installieren-oder-wiederherstellen-auf-einem-windows-pc-5c94902b-31a5-4274-abb0-b07f4661edf5) » herunter und installieren Sie es.
>
> Nach Abschluss der Installation können Sie die beiden Versionen unterscheiden, indem Sie „Outlook“ in der Windows-Suchleiste eingeben. Sie können dann den Unterschied wie unten sehen.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}

### Konto hinzufügen <a name="add-account"></a>

Um ein Zimbra Pro-Konto auf klassische Outlook hinzuzufügen, folgen Sie den unten stehenden Schritten, indem Sie nacheinander auf die Registerkarten klicken:

> [!tabs]
> **Schritt 1**
>>
>> 1. Gehen Sie zum **Einstellungenbereich** von Windows.
>> 2. Klicken Sie auf `Benutzerkonten`{.action}.
>> 3. Klicken Sie auf `Postfach`{.action}.
>> 4. Klicken Sie auf `E-Mail-Konten...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Schritt 2**
>>
>> - Öffnen Sie im Fenster **Kontoeinstellungen**, im Register `Postfach`, auf `Neu...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Schritt 3**
>>
>> - Wählen Sie im Fenster **Konto hinzufügen** `Manuelle Konfiguration oder zusätzliche Servertypen`{.action} aus.
>> - Klicken Sie auf `Weiter`{.action}, um fortzufahren.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Schritt 4**
>>
>> - Wählen Sie `Exchange ActiveSync`{.action} aus.
>> - Klicken Sie auf `Weiter`{.action}, um fortzufahren.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Schritt 5**
>>
>> Geben Sie die Verbindungsinformationen zu Ihrem Konto ein:
>>
>> - **Ihr Name** : Geben Sie einen Anzeigenamen ein.
>> - **E-Mail-Adresse** : Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **E-Mail-Server** : Geben Sie « zimbra1.mail.ovh.net » ein.
>> - **Benutzername** : Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **Passwort** : Geben Sie das Passwort ein, das mit Ihrer E-Mail-Adresse verknüpft ist.
>>
>> Klicken Sie auf `Weiter`{.action}, um das Hinzufügen des Kontos abzuschließen.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Schritt 6**
>>
>> Ihre E-Mail-Adresse ist jetzt für Outlook konfiguriert. Um eine vollständige Synchronisierung der Funktionen Ihres Zimbra Pro-Kontos zu ermöglichen, **laden Sie und installieren Sie** das Modul « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) » herunter.
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Schritt 7**
>>
>> Nach der Installation des Moduls « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) », starten Sie klassische Outlook.
>> Beim ersten Start wird das Fenster **Zimbra Server configuration Settings** angezeigt. Füllen Sie die folgenden Informationen aus:
>>
>> - **Servername** : Geben Sie « zimbra1.mail.ovh.net » ein.
>> - **E-Mail-Adresse** : Geben Sie Ihre vollständige E-Mail-Adresse ein.
>> - **Passwort** : Geben Sie das Passwort ein, das mit Ihrer E-Mail-Adresse verknüpft ist.
>>
>> Es ist nicht notwendig, die anderen Einstellungen zu ändern. Klicken Sie auf `Anwenden`{.action}, um die Einstellungen zu bestätigen und sicherzustellen, dass sie korrekt sind. Klicken Sie schließlich auf `OK`{.action}, um auf Outlook zuzugreifen und Ihre E-Mail-Adresse zu nutzen.
>>
>> ![outlook Windows](images/outlook-windows-add-step-07.png){.thumbnail .h-500}

> [!warning]
>
> Wenn Sie Probleme beim Senden oder Empfangen nach Abschluss der oben genannten Konfigurationsschritte haben, konsultieren Sie den Abschnitt « [Bestehende Einstellungen ändern](#modify-settings) » in diesem Leitfaden.

### E-Mail-Adresse nutzen

Sobald die E-Mail-Adresse konfiguriert ist, können Sie sie nutzen! Sie können nun Nachrichten senden und empfangen, sowie Ihre Kalender und Aufgaben verwalten.

OVHcloud bietet außerdem eine Webanwendung an, mit der Sie auf Ihre E-Mail-Adresse über einen Internetbrowser zugreifen können. Sie können sich über die [OVHcloud-Webmail](/links/web/email) mit den Zugangsdaten Ihrer E-Mail-Adresse einloggen. Für Fragen zur Nutzung konsultieren Sie bitte unseren Leitfaden « [Webmail Zimbra nutzen](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra) ».

### Wie können bestehende Einstellungen geändert werden? <a name="modify-settings"></a>

Um die Einstellungen eines bereits konfigurierten E-Mail-Kontos zu ändern, folgen Sie den unten stehenden Anweisungen:

1. Gehen Sie zum **Einstellungenbereich** von Windows.
1. Klicken Sie auf `Benutzerkonten`{.action}.
1. Klicken Sie auf `Postfach`{.action}.
1. Klicken Sie auf `E-Mail-Konten...`{.action}.
1. Wählen Sie das betreffende E-Mail-Konto in der Liste aus und klicken Sie auf `Ändern...`{.action}.

![outlook ios](images/outlook-windows-modify-01.png){.thumbnail .h-500}

Finden Sie die Einstellungen im **Schritt 7** des Abschnitts « [Konto hinzufügen](#add-account) ».

### Wie kann ein E-Mail-Konto gelöscht werden? <a name="delete-account"></a>

Um Ihr E-Mail-Konto zu löschen, folgen Sie den unten stehenden Anweisungen:

1. Gehen Sie zum **Einstellungenbereich** von Windows.
1. Klicken Sie auf `Benutzerkonten`{.action}.
1. Klicken Sie auf `Postfach`{.action}.
1. Klicken Sie auf `E-Mail-Konten...`{.action}.
1. Wählen Sie das betreffende E-Mail-Konto in der Liste aus und klicken Sie auf `Löschen`{.action}.

![outlook ios](images/outlook-windows-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> Um Ihr E-Mail-Konto löschen zu können, muss es sich nicht um das Standard-E-Mail-Konto handeln.

## Weiterführende Informationen <a name="go-further"></a>

> [!primary]
>
> Weitere Informationen zur Konfiguration einer E-Mail-Adresse über die Outlook-App für Windows finden Sie im [Microsoft-Hilfezentrum](https://support.microsoft.com/de-de/office/eine-e-mail-konto-in-outlook-fuer-windows-hinzufuegen-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794).

Für spezialisierte Dienstleistungen (Suchmaschinenoptimierung, Entwicklung usw.) kontaktieren Sie die [OVHcloud-Partner](/links/partner).

Wenn Sie Unterstützung bei der Nutzung und Konfiguration Ihrer OVHcloud-Lösungen benötigen, können Sie unsere verschiedenen [Support-Angebote](/links/support) konsultieren.

Tauschen Sie sich mit unserer [Nutzercommunity](/links/community) aus.