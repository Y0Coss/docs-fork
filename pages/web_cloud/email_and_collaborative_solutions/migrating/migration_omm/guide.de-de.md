---
title: 'E-Mail-Accounts mit dem OVH Mail Migrator migrieren'
excerpt: 'Erfahren Sie hier, wie Sie Ihre E-Mail-Accounts mit dem OVH Mail Migrator zu OVHcloud migrieren'
updated: 2025-11-25
---

<style>
.w-600 {
  max-width:600px !important;
}
.w-300 {
  max-width:300px !important;
}
</style>

## Ziel

[OVH Mail Migrator](/links/web/omm) ist ein von OVHcloud entwickeltes Tool, das den Bedarf an Rückverfolgbarkeit abdeckt. Es ermöglicht Ihnen, Ihre E-Mail-Konten zu Ihren OVHcloud-E-Mail-Adressen oder zu einem externen E-Mail-Service zu migrieren. Der Prozess unterstützt verschiedene Arten von Inhalten, wie E-Mails, Kontakte, Kalender und Aufgaben, solange diese mit Ihren E-Mail-Adressen kompatibel sind.

**Erfahren Sie, wie Sie Ihre E-Mail-Konten mit unserem OVH Mail Migrator-Tool zu OVHcloud migrieren können.**

## Voraussetzungen

- Ein externer E-Mail-Service oder ein OVHcloud-Service, wie z. B. ein [Zimbra](/links/web/zimbra), [Exchange](/links/web/emails), [E-mail Pro](/links/web/email-pro) oder MX Plan (über das einzelne MX Plan-Angebot oder in ein [OVHcloud-Webhosting-Angebot](/links/web/hosting) integriert).
- Die Zugangsdaten der E-Mail-Konten, die Sie migrieren möchten (Quell-E-Mail-Konten).
- Die Zugangsdaten der Ziel-E-Mail-Konten.

## In der praktischen Anwendung

Um auf OMM zuzugreifen, besuchen Sie die Adresse <omm.ovhcloud.com>

![omm](images/omm-01.png){.thumbnail .w-600}

### Projekt für Migration erstellen <a name="create-project"></a>

Bevor Sie eine Migration starten, müssen Sie ein Projekt erstellen. Dieses Projekt ermöglicht es Ihnen, eine oder mehrere Migrationen zu starten und diese zu verfolgen.

Klicken Sie auf `New migration`{.action}, um mit der Erstellung Ihres Projekts zu beginnen:

**E-Mail-Adresse des Projekt-Kontakts** : Geben Sie eine E-Mail-Adresse ein, die zur Empfangung der Zugangsdaten und der Benachrichtigungen zu Ihren Migrationen verwendet wird. Es wird nicht empfohlen, eine der E-Mail-Adressen einzugeben, die in Ihrem Projekt migriert werden.
**Projekt-Passwort** : Geben Sie ein Passwort ein, das zur Anmeldung in Ihr Projekt verwendet wird. Es muss mindestens 10 Zeichen enthalten, darunter mindestens 1 Sonderzeichen, 1 Zahl, 1 Großbuchstabe und 1 Kleinbuchstabe.

Klicken Sie auf `Create my project`{.action}, um die Erstellung des Projekts zu starten.

Auf die E-Mail-Adresse des Projekt-Kontakts erhalten Sie eine Bestätigungs-E-Mail, die die eindeutige Projekt-ID und einen Link enthält, um darauf zuzugreifen.

![omm](images/omm-create-project-01.png){.thumbnail .w-600}

> [!primary]
>
> Das Migrationsprojekt und die damit verbundenen Daten werden nach 60 Tagen Inaktivität automatisch gelöscht.

### Migration erstellen <a name="create-migration"></a>

Sobald Ihr Projekt erstellt ist, melden Sie sich wie folgt an:

- Klicken Sie auf `Track a migration`{.action}.
- Geben Sie die `Project ID` ein, die Sie per E-Mail erhalten haben.
- Geben Sie das `Project password` ein, das Sie bei der Erstellung festgelegt haben.
- Klicken Sie auf `Connect to project`{.action}, um abzuschließen.

![omm](images/omm-create-migration-01.png){.thumbnail .w-600}

Sie befinden sich nun auf der Startseite des Projekts, von der aus Sie Ihre erste Migration starten können.

- Klicken Sie auf `New migration`{.action} oben links in der Tabelle.

![omm](images/omm-create-migration-02.png){.thumbnail .w-600}

Eine neue Seite wird angezeigt, auf der Sie die Verbindungsinformationen für das Quellkonto und das Zielkonto eingeben können, um die Migration zu planen oder direkt zu starten. Zu Erinnerung: Der Inhalt des **source account** wird zum **destination account** migriert.

Bevor Sie Ihre Migration starten, ist es wichtig, die 3 Arten von Konten zu kennen, die migriert werden können und wohin Sie migrieren können:

- **OVHcloud** : Die `Auto detection` wird empfohlen, wenn Sie ein Konto migrieren müssen, das auf irgendeinem OVHcloud-E-Mail-Angebot gehostet wird. Wenn Sie viele OVHcloud-E-Mail-Konten haben, wählen Sie aus den Angeboten `MX Plan`, `E-mail Pro`, `Exchange` und `Zimbra`. Sie werden aufgefordert, sich zum mit der Migration verbundenen Angebot verbundenen OVHcloud-Konto anzumelden. Weitere Informationen finden Sie im Abschnitt „[Über eine Anmeldung beim OVHcloud-Konto migrieren](#sso-migration)“.
- **Others**: Sie beziehen sich auf E-Mail-Dienste, die außerhalb von OVHcloud abgeschlossen wurden, Sie finden eine nicht erschöpfende Liste der von OMM unterstützten E-Mail-Dienste. Wenn Ihr E-Mail-Konto-Typ nicht aufgelistet ist, verwenden Sie die Protokolle `Imap` oder `Pop`, die mit den meisten E-Mail-Servern kompatibel sind.
- **Importing files**: Es ist möglich, den Inhalt von PST-, ICS-, CSV- und Xml Rules-Dateien über OMM zu einem Ziel-E-Mail-Konto zu migrieren. Wenn diese Funktion ausgewählt wird, genügt es, Ihre Datei in das dafür vorgesehene Feld zu ziehen oder über den Button `Browse your files`{.action} Ihr Terminal zu durchsuchen.

![omm](images/omm-create-migration-03.png){.thumbnail .w-600}

Füllen Sie die Informationen entsprechend des Kontotyps aus:

- **Source account**
    - **Account type** : Wählen Sie den Typ des Quellkontos.
    - **E-Mail** : Geben Sie die E-Mail-Adresse des Quellkontos ein.
    - **Password** : Geben Sie das Passwort des Quellkontos ein.
    - **Server URL** / **Server domain** *(je nach Typ)*: Geben Sie den Hostnamen des E-Mail-Servers ein, der mit dem zu migrierenden E-Mail-Konto verbunden ist.
    - **OVHcloud Account ID** *(je nach Typ)*: Dieses Feld wird automatisch ausgefüllt, wenn Sie sich in ein OVHcloud-Konto angemeldet haben. Weitere Informationen finden Sie im Abschnitt „[Über eine Anmeldung beim OVHcloud-Konto migrieren](#sso-migration)“.
    - **Organization** *(je nach Typ)*: Wählen Sie die Organisation aus, die mit dem Quell-E-Mail-Konto verbunden ist.
    - **Platform** *(je nach Typ)*: Wählen Sie die Plattform aus, die mit dem Quell-E-Mail-Konto verbunden ist.
    - **Service** *(je nach Typ)*: Wählen Sie den Dienst aus, der mit dem Quell-E-Mail-Konto verbunden ist.
    - **Advanced settings** > **Delegation account ID** *(je nach Typ)*: Wenn das zu migrierende E-Mail-Konto ein geteiltes Konto ist, müssen Sie die E-Mail-Adresse des Administratorkontos auf diesem Delegationskonto eingeben.
- **Zielkonto**
    - **Account type** : Wählen Sie den Typ des Zielkontos.
    - **E-Mail** : Geben Sie die Ziel-E-Mail-Adresse ein.
    - **Password** : Geben Sie das Passwort ein, das mit dem Zielkonto verbunden ist.
    - **Server URL** / **Server domain** *(je nach Typ)*: Geben Sie den Hostnamen des E-Mail-Servers ein, der mit dem Ziel-E-Mail-Konto verbunden ist.
    - **OVHcloud Account ID** *(je nach Typ)*: Dieses Feld wird automatisch ausgefüllt, wenn Sie sich in ein OVHcloud-Konto angemeldet haben. Weitere Informationen finden Sie im Abschnitt „[Über eine Anmeldung beim OVHcloud-Konto migrieren](#sso-migration)“.
    - **Organization** *(je nach Typ)*: Wählen Sie die Organisation aus, die mit dem Ziel-E-Mail-Konto verbunden ist.
    - **Platform** *(je nach Typ)*: Wählen Sie die Plattform aus, die mit dem Ziel-E-Mail-Konto verbunden ist.
    - **Service** *(je nach Typ)*: Wählen Sie den Dienst aus, der mit dem Ziel-E-Mail-Konto verbunden ist.
    - **Advanced settings** > **Delegation account ID** *(je nach Typ)*: Wenn das Ziel-E-Mail-Konto ein geteiltes Konto ist, müssen Sie die E-Mail-Adresse des Administratorkontos auf diesem Delegationskonto eingeben.
- **Start of Transfers** : Sie können die Migration `sofort` starten oder `Später` ankreuzen, um die Migration zu verschieben. Die verschobene Migration ermöglicht es Ihnen, diese automatisch an einem von Ihnen definierten Datum und Uhrzeit zu starten.
- **Data to transfer** : Abhängig vom Typ des zu migrierenden E-Mail-Kontos und des Zielkontos zeigt Ihnen dieser Abschnitt die verschiedenen Arten von Daten an, die bei der Migration unterstützt werden. Dies hängt vom Quellkonto und vom Zielkonto ab.

![omm](images/omm-create-migration-04.png){.thumbnail .w-600}

> [!warning]
>
> Wenn Sie ein Konto migrieren, das Funktionen hat, die das Zielkonto nicht hat, müssen Sie die Elemente, die von OMM nicht migriert werden können, eigenständig sichern. Um Ihnen zu helfen, konsultieren Sie unseren Leitfaden „[Manuelles Migrieren Ihrer E-Mail-Adresse](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration)“.

Sobald die Parameter der Quell- und Zielkonten ausgefüllt sind, klicken Sie auf:

- `Migrate and add another account`{.action}, wenn Sie eine weitere Migration in die Liste Ihres Projekts hinzufügen möchten 
- `Migrate my account`{.action}, um die konfigurierte Migration zu starten und zur Startseite des Projekts zurückzukehren.

### Über eine Anmeldung beim OVHcloud-Konto migrieren <a name="sso-migration"></a>

Bei einer Migration zu oder von einem OVHcloud-Konto können Sie eine unserer Angebote `MX Plan`, `E-mail Pro`, `Exchange` und `Zimbra` auswählen.

![omm](images/omm-migration-sso-00.png){.thumbnail .w-300}

Wenn Sie eines dieser Angebote auswählen, folgen Sie den unten stehenden Schritten:

> [!tabs]
> **Schritt 1**
>>
>> - Klicken Sie auf `Login`{.action}, um das Anmeldefenster für den OVHcloud-Kundenbereich anzuzeigen.
>>
>> ![omm](images/omm-migration-sso-01.png){.thumbnail .w-600}
>>
> **Schritt 2**
>>
>> Melden Sie sich beim OVHcloud-Kundenbereich an:
>>
>> - Geben Sie die Identifikationsnummer oder die E-Mail-Adresse ein, die mit dem OVHcloud-Konto verbunden ist, geben Sie das dazugehörige Passwort ein und klicken Sie auf `Login`{.action}.
>> - Klicken Sie auf `Continue`{.action}, wenn Sie bereits identifiziert waren.
>>
>> > [!primary]
>> >
>> > Das OVHcloud-Kundenkonto muss mit dem E-Mail-Angebot verbunden sein, das Gegenstand der Migration ist.
>>
>> ![omm](images/omm-migration-sso-02.png){.thumbnail .w-600}
>>
> **Schritt 3**
>>
>> - Ein neues Fenster wird angezeigt, das Ihnen ermöglicht, OMM die Berechtigung zu erteilen, auf die Funktionen Ihres Kundenbereichs zuzugreifen, die die verfügbaren Angebote und E-Mail-Konten auflisten. Standardmäßig beträgt die Gültigkeit (Validity) dieser Berechtigungen 24 Stunden (1 Tag). Legen Sie die gewünschte zeitliche Gültigkeit fest und klicken Sie auf `Authorize`{.action}.
>>
>> ![omm](images/omm-migration-sso-03.png){.thumbnail .w-600}
>>
> **Schritt 4**
>>
>> - Sie können nun Ihre Dienste und Konten über Dropdown-Menüs auswählen, was die Suche nach Elementen erleichtert und Eingabefehler vermeidet. Es ist jedoch erforderlich, das Passwort des ausgewählten E-Mail-Kontos einzugeben.
>>
>> Beispiel mit einem Zimbra-Dienst:
>>
>> ![omm](images/omm-migration-sso-04.png){.thumbnail .w-600}

> [!warning]
>
> Sie können die laufenden Zugriffe über einen OVHcloud-Kundenbereich durch Klicken auf `Log out`{.action} beenden. Klicken Sie darunter bei der Angabe `OVHcloud account ID` auf `Log out the account`{.action}.
>
> ![omm](images/omm-migration-sso-05.png){.thumbnail .w-300}

### Migrationsprojekt verfolgen <a name="follow-migration"></a>

Es gibt zwei Möglichkeiten, den Migrationsprojektstatus zu verfolgen:

- Über die E-Mail, die Sie beim Erstellen Ihres Projekts erhalten haben. Sie finden einen Link, der Ihnen den Zugang zur Projekt-Anmeldepage mit der vorbelegten `Project ID` ermöglicht. Nur das `Project Password` muss eingegeben werden.
- Über die Startseite von OMM, klicken Sie auf `Track a migration`{.action}. Geben Sie Ihre `Project ID` und Ihr `Project Password` ein.

Klicken Sie anschließend auf `Connect to project`{.action}, um zur Startseite des Projekts zu gelangen und Ihre Migrationen zu verfolgen.

![omm](images/omm-create-migration-01.png){.thumbnail .w-600}

Auf dieser Seite finden Sie die Liste der laufenden oder geplanten Migrationen. Der Status des Projekts wird ebenfalls rechts angezeigt.

Klicken Sie auf den Button `⋮`{.action} rechts neben der Zeile einer Migration, um die Optionen anzuzeigen:

- `See more details`{.action} : Sie werden zu einer Seite weitergeleitet, auf der Sie den Fortschritt einer Migration verfolgen können oder den Bericht lesen können, sobald diese abgeschlossen ist.
- `Cancel migration`{.action} : Ermöglicht es, die laufende Migration abzubrechen. Die bereits migrierten Elemente bleiben auf dem Zielkonto.
- `Delete migration data (GDPR)`{.action} : Diese Option löst die Löschung aller Daten aus, die mit der Migration des Kontos verbunden sind. Sie behalten jedoch die Informationen zu den Ereignissen, die während der Migration stattgefunden haben.

![omm](images/omm-migration-follow-02.png){.thumbnail .w-600}

Beispiel für die Nachverfolgung einer Migration:

![omm](images/omm-migration-follow-03.png){.thumbnail .w-600}

> [!primary]
>
> Wenn während der Migration ein Fehler auftritt, wird Ihnen in dem Fenster `See more details`{.action} ein Link zum Fehlerprotokoll bereitgestellt.

## Weiterführende Informationen

[Mit E-Mail-Adresse manuell migrieren](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration)

[E-Mail-Adresse MX Plan zu einem E-mail Pro- oder Exchange-Konto migrieren](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel)

Für spezialisierte Dienstleistungen (Suchmaschinenoptimierung, Entwicklung usw.) kontaktieren Sie die [OVHcloud-Partner](/links/partner).

Wenn Sie Unterstützung bei der Nutzung und Konfiguration Ihrer OVHcloud-Lösungen wünschen, können Sie unsere verschiedenen [Support-Angebote](/links/support) konsultieren.

Tauschen Sie sich mit unserer [Nutzercommunity](/links/community) aus.