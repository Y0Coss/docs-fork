---
title: "E-Mail-Adressen von einer E-Mail-Plattform von OVHcloud zu einer anderen migrieren"
excerpt: "Erfahren Sie, wie Sie E-Mail-Adressen von einer Exchange- oder E-mail Pro-Plattform zu einer anderen Exchange-, E-mail Pro-, MX Plan- oder Zimbra-Plattform migrieren können"
updated: 2025-12-22
---

## Ziel

Sie möchten E-Mail-Adressen von einer Exchange- oder E-mail Pro-Plattform zu einer anderen Exchange-, E-mail Pro- oder MX Plan-Plattform migrieren. In diesem Leitfaden finden Sie einen zweistufigen Migrationsprozess:

1. **Die Zielplattform konfigurieren**.
2. **Die E-Mail-Konten** von Ihrer aktuellen Plattform zur neuen Plattform migrieren.

![email-migration](images/migration_platform01.gif){.thumbnail}

> [!primary]
>
> Um eine MX Plan-Lösung zu einer Exchange- oder E-mail Pro-Plattform zu migrieren, empfehlen wir Ihnen, unseren Leitfaden [Migrieren einer MX Plan-E-Mail-Adresse zu einem E-mail Pro- oder Exchange-Konto](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel) zu befolgen.
>

**Erfahren Sie, wie Sie E-Mail-Adressen von einer Exchange- oder E-mail Pro-Plattform zu einer anderen Exchange- oder E-mail Pro-Plattform migrieren können.**

## Voraussetzungen

- Eine **Quellplattform** mit konfigurierten Konten [Exchange](/links/web/emails-hosted-exchange) oder [E-mail Pro](/links/web/email-pro) oder [Zimbra](/links/web/zimbra) vorliegen.
- Eine **Zielplattform** mit Konten [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) oder MX Plan (über das MX Plan-Angebot oder in einem [OVHcloud-Webhosting-Angebot](/links/web/hosting) enthalten). Diese Plattform muss über nicht konfigurierte oder verfügbare Konten verfügen, um die zu migrierenden E-Mail-Adressen aufzunehmen.
- Sie müssen angemeldet sein bei Ihrem [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

### Zielplattform konfigurieren

> [!warning]
>
> Vor Beginn der Migration, wenn Sie gerade Ihr neues E-Mail-Angebot bestellt haben, fügen Sie zunächst den Domainnamen zu Ihrer E-Mail-Plattform hinzu. Wenn Sie zu einer MX Plan-Plattform migrieren, ist der angeschlossene Domainname „fest“, Sie können direkt zur [nächsten Etappe](#accountsmigration) übergehen.
>
> Wählen Sie den Tab `Zugeordnete Domains`{.action} oder `Domain`{.action} auf Ihrer Plattform aus und klicken Sie auf `Domain hinzufügen`{.action}. Nachdem der Domainname hinzugefügt wurde, stellen Sie sicher, dass die Bezeichnung `OK` oder `Aktiv`{.action} in der Spalte `Status` angezeigt wird.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Weitere Informationen zum Hinzufügen eines Domainnamens finden Sie im [E-mail Pro-Leitfaden](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), im [Exchange-Leitfaden](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) oder im [Zimbra-Leitfaden](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

### E-Mail-Konten migrieren <a name="accountsmigration"></a>

Die Migration Ihrer E-Mail-Konten erfolgt in drei großen Schritten: **Umbenennen** des ursprünglichen E-Mail-Kontos, **Erstellen** des neuen E-Mail-Kontos und **Migration** von der ursprünglichen Plattform zur neuen.

![email-migration](images/migration_platform03.gif){.thumbnail}

> [!warning]
>
> Besonderer Fall:
>
> - Wenn Sie **ein Exchange- oder Zimbra PRO-Konto** zu einem **E-mail Pro-** oder **Zimbra STARTER-Konto** migrieren müssen, müssen Sie sicherstellen, dass Ihre E-Mail-Konten nicht mehr als 10 Go (E-mail Pro) oder 15 Go (Zimbra STARTER) enthalten. Die Funktionen zur Zusammenarbeit, die Synchronisierung von Kalendern und Kontakten sind bei E-mail Pro oder Zimbra STARTER nicht vorhanden und können nicht migriert werden.
> - Wenn Sie **ein Exchange-, E-mail Pro- oder Zimbra-Konto** zu einem **MX Plan-Konto** migrieren müssen, müssen Sie sicherstellen, dass Ihr E-Mail-Konto nicht mehr als 5 Go enthält. Die Funktionen zur Zusammenarbeit, die Synchronisierung von Kalendern und Kontakten sind bei MX Plan nicht vorhanden und können nicht migriert werden.

#### Schritt 1: Umbenennen

Benennen Sie das zu migrierende E-Mail-Konto mit einem vorübergehenden Namen um (z. B. um das Konto *john.smith@mydomain.ovh* zu migrieren, benennen Sie es in *john.smith01@mydomain.ovh* um).

Wählen Sie den Tab `E-Mail-Konten`{.action} auf Ihrer E-Mail-Plattform aus und klicken Sie auf den Button `...`{.action}, gefolgt von `Bearbeiten`{.action}.

![email-migration](images/migration_platform04.png){.thumbnail}

#### Schritt 2: Erstellen

Erstellen Sie Ihre E-Mail-Adresse auf dem neuen Konto Ihrer E-mail Pro-, Exchange- oder MX Plan-Plattform (nehmen wir das vorherige Beispiel, Sie erstellen also *john.smith@mydomain.ovh* auf Ihrer neuen Plattform).

Wählen Sie den Tab `E-Mail-Konten`{.action} auf Ihrer Plattform aus und klicken Sie auf den Button `...`{.action}, rechts neben dem Ziel-E-Mail-Konto, gefolgt von `Bearbeiten`{.action}.

![email-migration](images/migration_platform05.png){.thumbnail}

#### Schritt 3: Migrieren

> [!warning]
> 
> Nur die Daten Ihrer E-Mail-Konten werden migriert (E-Mails, Kontakte, Kalender, Empfangsregeln usw.). Die Funktionen, die mit Ihrer Plattform verbunden sind, müssen auf der neuen Plattform neu erstellt werden :
>
> - [Alias](/pages/web_cloud/email_and_collaborative_solutions/common_email_features/feature_redirections) 
> - [Berechtigungsdelegationen](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_delegation) 
> - [Gruppen](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_groups)
> - Externe Kontakte
> - [Unterschrift](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_footers)

Migrieren Sie das „Quell“-E-Mail-Konto zu Ihrem Konto auf der neuen Plattform mithilfe unseres Tools [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Weitere Informationen zu OMM finden Sie in unserem Leitfaden [Migrieren von E-Mail-Konten über OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![email-migration](images/migration_platform06.png){.thumbnail}

Die Dauer der Migration hängt von der Menge der zu migrierenden Daten ab und kann zwischen einigen Minuten und mehreren Stunden variieren.

Überprüfen Sie nach der Migration, ob Sie alle Elemente wiederfinden, indem Sie sich über den Webmail-Client unter der Adresse [Webmail](/links/web/email) anmelden.

Nach Abschluss der Migration können Sie das Konto mit vorübergehendem Namen entweder behalten oder löschen.

Wenn Sie es löschen möchten, gehen Sie zum Tab `E-Mail-Konten`{.action} auf Ihrer ursprünglichen E-Mail-Plattform, klicken Sie auf den Button `...`{.action} und dann auf `Dieses Konto zurücksetzen`{.action}.

### Überprüfen oder ändern Sie die Konfiguration Ihres Domains

An dieser Stelle sollten Ihre E-Mail-Adressen bereits migriert und funktionsfähig sein. Aus Sicherheitsgründen empfehlen wir Ihnen, zu prüfen, dass die Konfiguration Ihres Domains korrekt ist, indem Sie sich in Ihrem Kundencenter anmelden.

Wählen Sie den betreffenden E-mail Pro-, Exchange- oder Zimbra-Service aus und gehen Sie zum Tab `Zugeordnete Domains`{.action} oder `Domain`{.action} auf Ihrer Plattform. Überprüfen Sie den Abschnitt oder die Spalte `Diagnose`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Wenn Sie gerade eine Migration durchgeführt haben oder einen DNS-Eintrag Ihres Domains geändert haben, kann es sein, dass die Anzeige in Ihrem [OVHcloud Kundencenter](/links/manager) einige Stunden dauert, bis sie aktualisiert wird.
>

Um die Konfiguration zu ändern, klicken Sie auf das rote Symbol und führen Sie die geforderte Aktion durch. Diese benötigt eine Ausbreitungszeit von maximal 4 bis 24 Stunden, bis sie vollständig wirksam ist.

![email-migration](images/check_the_dns_records_associated_domains.png){.thumbnail}

### Ihre migrierten E-Mail-Adressen nutzen

Sie können nun Ihre migrierten E-Mail-Adressen nutzen. Dazu stellt OVHcloud eine Onlineanwendung (_Web App_) unter der Adresse [Webmail](/links/web/email) bereit. Sie müssen dort Ihre Zugangsdaten für Ihre E-Mail-Adresse eingeben.

Wenn Sie eines der migrierten Konten in einem E-Mail-Client (z. B. Outlook, Thunderbird) konfiguriert haben, müssen Sie diese erneut einrichten. Die Verbindungsinformationen zum OVHcloud-Server haben sich nach der Migration geändert.

> [!primary]
>
> Sie können auch manuell E-Mail-Adressen zu OVHcloud migrieren, indem Sie unser Tool [OVHcloud Mail Migrator (OMM)](/links/web/omm) verwenden. Dazu müssen Sie über die Zugangsdaten (Benutzername, Passwort, Server) sowohl für die Quell- als auch für die Ziel-E-Mail verfügen.
>

## Weiterführende Informationen

[Kontakte Ihrer Dienste verwalten](/pages/account_and_service_management/account_information/managing_contacts).

[Erste Schritte mit dem E-mail Pro-Angebot](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Erste Schritte mit dem Exchange-Angebot](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Erste Schritte mit dem Zimbra-Angebot](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Treten Sie unserer [User Community](/links/community) bei.