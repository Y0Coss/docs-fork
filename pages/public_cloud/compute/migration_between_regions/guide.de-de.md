---
title: 'Migration von Instanzen zwischen verschiedenen Regionen'
excerpt: 'Dieses Handbuch beschreibt, wie Sie eine OVHcloud Public Cloud-Instanz zwischen zwei Regionen, 1AZ und 3AZ, migrieren. Es behandelt die Schritte Backup, Übertragung und Neuanlage mit Anweisungen über den Manager, Horizon oder die OpenStack CLI.'
updated: 2025-10-15
---

## Ziel

Dieses Handbuch erklärt, wie Sie eine Public Cloud-Instanz von einer Region in eine andere migrieren, von 1AZ zu 3AZ oder umgekehrt. Es fasst die Schlüsselschritte (Backup, Übertragung und Neuanlage) zusammen und verweist auf die detaillierten Handbücher für jeden Schritt.

## Voraussetzungen

- Eine [OVHcloud Public Cloud-Instanz](/pages/public_cloud/compute/public-cloud-first-steps).
- Zugriff auf das [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

> [!primary]
>
> Vor der Migration einer Instanz ist es wichtig, die Unterschiede zwischen den Bereitstellungsmodi zu verstehen, die in der OVHcloud Public Cloud angeboten werden. Jeder Modus (1AZ, 3AZ oder Local Zones) hat einen direkten Einfluss auf die Ausfallsicherheit, Verfügbarkeit und den Aufbau Ihrer Infrastruktur.
>
> Weitere Informationen finden Sie in der Dokumentation: [Comparison and resilience of Deployment Modes - Understanding 3-AZ / 1-AZ / Local Zones (EN)](/pages/public_cloud/public_cloud_cross_functional/deployment_modes_comparison_resilience_details).
>

### Schritt 1. Backup Ihrer Instanz

Beginnen Sie mit der Erstellung eines Backups der zu migrierenden Instanz oder verwenden Sie ein vorhandenes, sofern es noch gültig ist.

OVHcloud bietet zwei Arten von Backups an, mit unterschiedlichem Verhalten, abhängig vom gewünschten Migrationsmodus:

- Lokales Backup: Erfordert eine manuelle Übertragung, wenn Sie in eine andere Region oder AZ migrieren.
- Remote-Backup (**empfohlen**): Automatisch von OVHcloud verwaltet, wird das lokale Backup in die ausgewählte Region repliziert. Keine manuelle Übertragung erforderlich.

> [!primary]
>
> Wenn Ihr lokales Backup in einer 3AZ-Region durchgeführt wurde und Sie die Instanz in einer anderen AZ innerhalb derselben Region wiederherstellen möchten, ist keine Übertragung erforderlich.
>
> Lokale Backups sind in allen Verfügbarkeitszonen innerhalb einer 3AZ-Region zugänglich. Sie können direkt zum Schritt der Instanzneuanlage übergehen.
>
> Derzeit ist die Erstellung eines entfernten Backups nicht über das OVHcloud Kundencenter möglich. Diesen Vorgang können Sie nur über die OVHcloud API oder OpenStack durchführen.
>

Eine Instanz kann gesichert werden:

- über das OVHcloud Kundencenter.
- über die OVHcloud API.
- über die OpenStack CLI.
- über Horizon.

Alle detaillierten Informationen finden Sie im Abschnitt **Backup einer Instanz erstellen** in unserem Handbuch „[Backup einer Instanz erstellen](/pages/public_cloud/compute/save_an_instance)“.

### Schritt 2. Migrieren Sie Ihr Backup in eine andere Region

> [!primary]
>
> Wenn Sie ein Remote-Backup verwendet haben, können Sie direkt zum [Schritt 3: Wiederherstellen der Instanz in der neuen Region](#step3recreateinstance) springen.
>

> [!tabs]
> Über die Openstack CLI
>> Um Ihr Backup von einer AZ zu einer anderen über die Openstack CLI zu übertragen, folgen Sie unserem Handbuch: [Backup einer Instanz herunterladen und in eine andere OpenStack-Region übertragen](/pages/public_cloud/compute/transfer_instance_backup_from_one_datacentre_to_another).
>>

### Schritt 3. Wiederherstellen der Instanz in der neuen Region <a name="step3recreateinstance"></a>

Die Instanz kann in der neuen Region wiederhergestellt werden:

- über das OVHcloud Kundencenter.
- über die OVHcloud API.
- über die OpenStack CLI.
- über Horizon.

Alle detaillierten Informationen finden Sie im Abschnitt **Eine Instanz aus einem Backup erstellen** in unserem Handbuch "[Verwenden von Backups zum Erzeugen oder Wiederherstellen von Instanzen](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup)".

## Weiterführende Informationen

Treten Sie unserer [User Community](/links/community) bei.