---
title: 'E-Mail-Adresse MX Plan zu einem E-Mail Pro-, Exchange- oder Zimbra-Konto migrieren'
excerpt: 'Erfahren Sie, wie Sie eine MX Plan-E-Mail-Adresse zu einem E-Mail Pro-, Exchange- oder Zimbra-Konto migrieren'
updated: 2025-12-22
---

## Ziel
OVHcloud bietet mehrere E-Mail-Lösungen an: MX Plan (allein oder in einem Web-Hosting-Angebot enthalten), E-Mail Pro, Exchange und Zimbra. Diese verfügen über eigene Funktionen und können sich an verschiedene Anwendungsfälle anpassen. Ändern sich Ihre Anforderungen? OVHcloud stellt Ihnen ein Migrationswerkzeug zur Verfügung, mit dem Sie von einer Lösung zur anderen wechseln können.

**Erfahren Sie, wie Sie eine MX Plan-E-Mail-Adresse zu einem E-Mail Pro- oder Exchange-Konto migrieren können.**

<iframe class="video" width="560" height="315" src="https://www.youtube-nocookie.com/embed/0JLLoBBvsCc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> [!warning]
>
> [OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm) ermöglicht es Ihnen, Ihre Nachrichten von einem E-Mail-Server zu einem anderen zu migrieren.<br>
> Wenn Ihre E-Mails nur lokal gespeichert sind (POP-Konfiguration oder lokales Archiv), können Sie eine [Exportdatei aus Ihrem E-Mail-Client erstellen](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), und anschließend [die PST-Datei über OMM importieren](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm#realiser-une-migration-par-fichier) oder [direkt aus Ihrem E-Mail-Client importieren](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

## Voraussetzungen
- Eine MX Plan-E-Mail-Adresse besitzen (über das MX Plan-Angebot oder in einem [OVHcloud-Webhosting-Angebot](/links/web/hosting) enthalten).
- Einen Dienst [Exchange](/links/web/emails-hosted-exchange), [E-Mail Pro](/links/web/email-pro) mit mindestens einem nicht konfigurierten Konto (der wird in der Form „@configureme.me“ angezeigt) oder [Zimbra](/links/web/zimbra) besitzen.
- **Keine Weiterleitung auf der MX Plan-E-Mail-Adresse eingerichtet haben, die Sie migrieren möchten**.
- Angemeldet sein in Ihrem [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

### Schritt 1: Projektumfang bestimmen

Die Lösungen E-Mail Pro und Exchange verfügen über eine gemeinsame Basisfunktionalität. Dennoch gibt es Unterschiede je nach Anwendungsfall. Wenn Sie sich für ein Exchange-Konto entscheiden, stehen Ihnen alle Funktionen der Zusammenarbeit zur Verfügung, wie z. B. die Synchronisation von Kalender und Kontakte. Die Lösung E-Mail Pro bietet einige dieser Funktionen, doch diese sind auf die Nutzung über einen Webmailer beschränkt.

Bevor Sie fortfahren, ist es daher wichtig zu wissen, zu welcher Angebotsoption Sie Ihre MX Plan-E-Mail-Adressen migrieren möchten. Um Ihnen bei dieser Wahl zu helfen, besuchen Sie die Seite der [OVHcloud professionellen E-Mail-Lösungen](/links/web/emails), die einen detaillierten Vergleich der Angebote bietet. Sie können die Lösungen kombinieren und somit für denselben Domainnamen ein oder mehrere E-Mail Pro- und Exchange-Konten nutzen. Zudem empfehlen wir Ihnen, bei der Migration mehrerer Konten einen Migrationsplan zu erstellen.

### Schritt 2: Ihre E-Mail Pro- oder Exchange-Konten bestellen

Dieser Schritt ist optional, wenn Sie bereits über einen Exchange- oder E-Mail Pro-Service verfügen, zu dem Sie diese Migration durchführen.

Andernfalls melden Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) an und bestellen Sie den gewünschten E-Mail Pro- oder Exchange-Service. Folgen Sie den verschiedenen Schritten und warten Sie, bis der Service installiert ist. Ihnen wird eine E-Mail gesendet, sobald dieser Prozess abgeschlossen ist.

> [!primary]
>
> Nachdem das Konto bestellt wurde, lassen Sie es zunächst in der Form „@configureme.me“. Es wird bei der Migration umbenannt.
>

### Schritt 3: Migration durchführen

Bevor Sie Ihre Migration starten, müssen Sie die Version des MX Plan identifizieren, von dem Sie migrieren.

> [!primary]
>
> Die E-Mail-Technologie Ihrer MX Plan-Angebot kann je nach Aktivierungsdatum Ihres Angebots oder bei kürzlich erfolgter Migration variieren. Diese Technologie ist besonders durch die Oberfläche ihres Webmails zu erkennen. Um sie in Ihrem Kundencenter zu identifizieren, folgen Sie diesen Schritten :
>
> 1. Melden Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) an.
> 1. Gehen Sie in den Bereich `Web Cloud`{.action}.
> 1. Klicken Sie auf `MX Plan`{.action}.
> 1. Wählen Sie den betreffenden Domainnamen aus.
> 1. Der Tab `Allgemeine Informationen`{.action} ist standardmäßig ausgewählt.
> 1. Notieren Sie sich die genutzte Technologie unter der Bezeichnung **Webmail** im Feld `Abonnement`.
>
> ![MX plan](/pages/assets/schemas/emails/technology-email.png){.thumbnail .w-640}
>

#### 3.1 Manuelle Migration eines MX Plan-Angebots zu Exchange, E-Mail Pro oder Zimbra  <a name="all-mxplan"></a>

> [!warning]
>
> Dieser Abschnitt betrifft alle MX Plan-Dienste, die die Webmail-Technologie Rouncube, Zimbra oder OWA nutzen.
>
> Wenn Sie jedoch einen MX Plan-Dienst mit Rouncube-Webmail zu einer OVHcloud E-Mail Pro- oder Exchange-Plattform migrieren möchten, folgen Sie dem Abschnitt « [Automatische Migration eines MX Plan Rouncube-Angebots zu Exchange oder E-Mail Pro](#roundcube-mxplan) » in diesem Leitfaden.

> [!warning]
>
> Wenn Sie gerade Ihr neues E-Mail-Angebot bestellt haben, fügen Sie zunächst den Domainnamen zu Ihrer E-Mail-Plattform hinzu, bevor Sie mit der Migration beginnen. <br> - *Zum Beispiel, um das Konto « myemail@mydomain.ovh » zu migrieren, müssen Sie den Domainnamen « mydomain.ovh » zu Ihrer Plattform hinzufügen.*
>
> Wählen Sie den Tab `Zugeordnete Domains`{.action} oder `Domain`{.action} auf Ihrer Plattform aus und klicken Sie auf `Domain hinzufügen`{.action}. Sobald der Domainname hinzugefügt wurde, stellen Sie sicher, dass die Bezeichnung `OK` oder `Aktiv`{.action} in der Spalte `Status` angezeigt wird.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Weitere Informationen zum Hinzufügen eines Domainnamens finden Sie in unserem [E-Mail Pro-Leitfaden](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [Exchange-Leitfaden](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) oder [Zimbra-Leitfaden](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

Die Migration Ihres MX Plan erfolgt in drei großen Schritten: **Umbenennen**, **Erstellen** und **Migrieren**.

![exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Umbenennen** des zu migrierenden MX Plan-Kontos mit einem vorübergehenden Namen (z. B. für das MX Plan-Konto *john.smith@mydomain.ovh*, benennen Sie dieses in *john.smith01@mydomain.ovh* um).

Im Tab `E-Mail-Konten`{.action} Ihrer MX Plan-Plattform klicken Sie auf den Button `...`{.action} und dann auf `Bearbeiten`{.action}.

![exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> Die Änderung des Kontos ist nicht unmittelbar, warten Sie bis das Verfahren abgeschlossen ist, bevor Sie zum nächsten Schritt übergehen.

2\. **Erstellen** Sie Ihre E-Mail-Adresse auf dem neuen Konto Ihrer E-Mail Pro- oder Exchange-Plattform (nehmen wir das vorherige Beispiel, erstellen Sie also *john.smith@mydomain.ovh* auf Ihrer neuen Plattform).

Im Tab `E-Mail-Konten`{.action} Ihrer E-Mail Pro- oder Exchange-Plattform klicken Sie auf den Button `...`{.action} und dann auf `Bearbeiten`{.action}.

![exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Migrieren** Sie das MX Plan-Konto zu Ihrem neuen Plattformkonto mit unserem Tool [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Weitere Informationen zu OMM finden Sie in unserem Leitfaden [E-Mail-Konten über OVHcloud Mail Migrator migrieren](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

Die Dauer der Migration hängt von der Menge an Inhalten ab, die zu Ihrem neuen Konto migriert werden müssen. Sie kann zwischen einigen Minuten und mehreren Stunden variieren.

Überprüfen Sie nach der Migration, ob Sie Ihre Elemente wiederfinden, indem Sie sich mit dem Webmail unter der Adresse [Webmail](/links/web/email) einloggen.

Sie können das Konto mit vorübergehendem Namen nach dieser Migration behalten oder löschen.

Wenn Sie es löschen möchten, gehen Sie in den Tab `E-Mail-Konten`{.action} Ihres MX Plan, klicken Sie auf den Button `...`{.action} und dann auf `Dieses Konto zurücksetzen`{.action}.

#### 3.2 Automatische Migration eines MX Plan Rouncube-Angebots zu Exchange oder E-Mail Pro <a name="roundcube-mxplan"></a>

> [!warning]
>
> Dieser Abschnitt betrifft ausschließlich MX Plan-Dienste, die die Webmail-Technologie Rouncube nutzen.

> [!primary]
>
> Ihr OVHcloud-Konto muss vorab Administrator-**und** Technik-Kontakt des zu migrierenden MX Plan-Dienstes **sowie** des E-Mail Pro- oder Exchange-Dienstes sein, zu dem Sie migrieren.
>
> Weitere Informationen zu Änderungen der Kontakte finden Sie in unserem Leitfaden [Kontakte zu Ihren Diensten verwalten](/pages/account_and_service_management/account_information/managing_contacts).
>

Die Migration kann über zwei Schnittstellen durchgeführt werden:<br>

- **über den Hosted Exchange-Konfigurationsassistenten**, nur wenn Sie gerade einen Hosted Exchange-Dienst bestellt haben und auf diesem noch nichts konfiguriert wurde ;
- **über die MX Plan-Schnittstelle**, sobald Sie über einen E-Mail Pro- oder Exchange-Dienst (konfiguriert oder nicht) und eine MX Plan-E-Mail-Adresse verfügen, die Sie migrieren möchten.

> Erinnern Sie sich daran, bevor Sie die Migration starten, dass keine **Weiterleitung** oder kein **Anrufbeantworter** auf Ihrem MX Plan konfiguriert ist.
>
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Sobald Sie bereit sind, fahren Sie mit der Lektüre dieser Dokumentation fort, abhängig von der ausgewählten Schnittstelle. Wir erinnern Sie daran, dass die Dauer der Migration von der Menge an Inhalten abhängt, die zu Ihrem neuen Konto migriert werden müssen. Sie kann zwischen einigen Minuten und mehreren Stunden variieren.

> [!warning]
>
> Sobald die Migration bestätigt ist, können Sie nicht mehr auf Ihre alte MX Plan-E-Mail-Adresse zugreifen oder den Migrationsprozess stornieren. Wir empfehlen Ihnen dringend, diesen Vorgang zu einem geeigneten Zeitpunkt durchzuführen.
>
> Auch wenn Sie nicht mehr auf Ihre aktuelle E-Mail-Adresse zugreifen können, werden die bereits empfangenen und empfangenen Nachrichten nicht verloren gehen. Sie sind sofort über Ihr neues Konto zugänglich.
>

##### **Migration über den Exchange-Konfigurationsassistenten**

Um darauf zuzugreifen, wählen Sie in Ihrem [OVHcloud Kundencenter](/links/manager) den betreffenden Dienst aus. Der Assistent sollte angezeigt werden, um Ihnen bei der Konfiguration Ihres neuen Exchange-Dienstes zu helfen. Während dieses Prozesses können Sie die zu migrierenden MX Plan-E-Mail-Konten auswählen.

Falls der Konfigurationsassistent nicht angezeigt wird, werden stattdessen die allgemeinen Informationen des Exchange-Dienstes angezeigt. In diesem Fall müssen Sie die Migration Ihrer Konten über die MX Plan-Schnittstelle durchführen.

##### **Migration über die MX Plan-Schnittstelle**

Um die Migration über diese Schnittstelle durchzuführen, gehen Sie in den Bereich `E-Mails`{.action} Ihres OVHcloud Kundencenters. Wählen Sie anschließend den Dienst aus, der den Domainnamen Ihrer E-Mail-Adressen trägt. Klicken Sie auf das Zahnradsymbol in der Zeile des betreffenden E-Mail-Kontos (auch als Quellkonto bezeichnet) und dann auf `Konto migrieren`{.action}.

![exchange](images/access_the_migration_tool.png){.thumbnail}

Im angezeigten Fenster wählen Sie den Ziel-Dienst (den Dienst, zu dem Sie die E-Mail-Adresse migrieren möchten) aus und klicken Sie auf `Weiter`{.action}. Wenn dieser Dienst mindestens ein „freies“ Konto (also noch nicht konfiguriert) hat, erfolgt die Migration zu einem dieser Konten. Lesen Sie anschließend die angezeigten Informationen, bestätigen Sie diese und klicken Sie auf `Weiter`{.action}, um die Aktion fortzusetzen.

Falls Sie kein „freies“ Konto haben, wird der Button `Konten bestellen`{.action} angezeigt. Folgen Sie den Schritten und warten Sie, bis die Konten installiert sind, um die Aktion erneut durchzuführen.

Bestätigen Sie abschließend das Passwort der Quelle-Mail-Adresse (die Sie migrieren möchten) und klicken Sie auf `Migrieren`{.action}. Diesen Vorgang müssen Sie so oft wiederholen, wie es für die Migration weiterer Konten erforderlich ist.

![exchange](images/account_migration_steps.png){.thumbnail}

### Schritt 4: Konfiguration Ihres Domains überprüfen oder ändern

An dieser Stelle sollten Ihre E-Mail-Adressen bereits migriert und funktionsfähig sein. Aus Sicherheitsgründen empfehlen wir Ihnen, sicherzustellen, dass die Konfiguration Ihres Domains korrekt ist, indem Sie Ihr Kundencenter konsultieren.

Dazu wählen Sie den betreffenden E-Mail Pro-, Exchange- oder Zimbra-Dienst aus und gehen Sie auf den Tab `Zugeordnete Domains`{.action} oder `Domain`{.action} auf Ihrer Plattform. Überprüfen Sie den Abschnitt oder die Spalte `Diagnose`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Wenn Sie gerade die Migration durchgeführt haben oder einen DNS-Eintrag Ihres Domains geändert haben, kann es sein, dass die Anzeige im [OVHcloud Kundencenter](/links/manager) einige Stunden braucht, um sich zu aktualisieren.
>

Um die Konfiguration zu ändern, klicken Sie auf das rote Symbol und führen Sie die geforderte Aktion durch. Diese benötigt eine Ausbreitungszeit von maximal 4 bis 24 Stunden, bevor sie vollständig wirksam ist.

### Schritt 5: Ihre migrierten E-Mail-Adressen nutzen

Sie können nun Ihre migrierten E-Mail-Adressen nutzen. Dazu stellt Ihnen OVHcloud eine Onlineanwendung (_Web App_) unter der Adresse [Webmail](/links/web/email) zur Verfügung. Sie müssen dort Ihre Zugangsdaten für Ihre E-Mail-Adresse eingeben.

Wenn Sie eines der migrierten Konten auf einem E-Mail-Client (z. B. Outlook) konfiguriert haben, müssen Sie diese erneut einrichten. Die Verbindungsinformationen zum OVHcloud-Server haben sich nach der Migration geändert. Um Ihnen bei den Aktionen zu helfen, konsultieren Sie unsere Dokumentation in den Abschnitten der Leitfäden zu [E-Mail Pro](/products/web-cloud-email-collaborative-solutions-email-pro) und [Hosted Exchange](/products/web-cloud-email-collaborative-solutions-mx-plan). Falls Sie das Konto nicht unmittelbar neu konfigurieren können, ist der Zugriff über die Onlineanwendung weiterhin möglich.

### Organisation des Inhalts Ihrer E-Mail-Adressen nach einer Migration <a name="content-after-migration"></a>

Wenn Sie sich das erste Mal auf Ihrem neuen E-Mail-Konto anmelden, kann der migrierte Inhalt teilweise versteckt sein. Um alle Elemente anzuzeigen, klicken Sie im Webmail auf das Pfeilsymbol neben der `Posteingang`-Option, um die Unterordner anzuzeigen. Der migrierte Inhalt Ihres alten E-Mail-Kontos sollte angezeigt werden.

![exchange](images/owa_migrate_content.png){.thumbnail}

Standardordner wie „Gesendete Elemente“ oder „Papierkorb“ erscheinen auf Englisch („Sent items“ und „Trash“), mit Ausnahme der Ordner, die Sie selbst erstellt haben.

Nach einer Migration empfehlen wir Ihnen, alle Ordner und Unterordner Ihres Kontos zu durchsuchen, um sicherzustellen, dass alle Elemente vorhanden sind.

### Manuelle Migration

Sie können Ihre E-Mail-Adressen auch manuell zu Ihrem neuen OVHcloud-E-Mail-Angebot migrieren, indem Sie lediglich Ihre E-Mail-Software nutzen. Nutzen Sie unseren Leitfaden [Manuelle Migration Ihrer E-Mail-Adresse](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration). Wir empfehlen Ihnen jedoch, diese Methode nur anzuwenden, wenn die Hauptmethoden nicht möglich sind.

## Weitere Informationen

[Kontakte zu Ihren Diensten verwalten](/pages/account_and_service_management/account_information/managing_contacts).

[Erste Schritte mit dem E-Mail Pro-Angebot](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Erste Schritte mit dem Exchange-Angebot](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Erste Schritte mit dem Zimbra-Angebot](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Treten Sie unserer [User Community](/links/community) bei.