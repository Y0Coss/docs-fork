---
title: 'So weisen Sie einem Bare Metal server ein Tag zu'
excerpt: 'Erfahren Sie, wie Sie über das OVHcloud Kundencenter Tags für jeden Dedicated Server erstellen und ändern'
updated: 2025-07-01
---

## Ziel

Tags sind Labels, die Ihren Ressourcen zugeordnet werden können, um sie effizienter zu organisieren und zu verwalten.

Jedes Tag besteht aus zwei Teilen:

- **Key**: Stellt ein Attribut oder eine Kategorie dar.
- **Wert**: Entspricht den Informationen, die mit diesem Schlüssel verknüpft sind.

Beispielsweise können Sie Ihre Ressourcen nach Standort, Dienst oder sogar nach Sicherheitsstufe kategorisieren. Die Verwendung von Tags erleichtert die Suche, das Organisieren von Ressourcen, das Verwalten zugehöriger Kosten und das Anwenden von Richtlinien mit der gewünschten Granularität.

**In dieser Anleitung erfahren Sie, wie Sie über das OVHcloud Kundencenter Tags für jeden Dedicated Server erstellen, zuweisen und löschen.**

## Voraussetzungen

- Ein [Dedicated Server](/links/Bare-Metal/Bare-Metal) in Ihrem OVHcloud Account.
- Zugriff auf das [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

### Weisen Sie einem Dedicated Server über das OVHcloud Kundencenter einen Tag zu

So kennzeichnen Sie einen Server:

1. Melden Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) an.
1. Gehen Sie in den Bereich `Bare Metal Cloud`{.action}.
1. Klicken Sie auf `Dedicated Server`{.action} und wählen Sie Ihren Server aus der Liste aus.

Standardmäßig werden Sie auf die Registerkarte `Allgemeine Informationen`{.action} weitergeleitet.

![Allgemeine Informationen](images/general_information.png){.thumbnail}

Klicken Sie im Feld **Tags** auf `Tag hinzufügen`{.action}.

![Tag hinzufügen](images/add_a_tag.png){.thumbnail}

Sie werden automatisch auf die Registerkarte `Tags` gezeigt.

Klicken Sie auf die Schaltfläche `Tag zuweisen`{.action}.

![Leere Stichwortliste](images/tag_list_empty.png){.thumbnail}

Klicken Sie im daraufhin geöffneten Fenster in das Feld `Schlüssel`{.action}, um das Dropdown-Menü zu öffnen, und wählen Sie dann den gewünschten Schlüssel aus.

![Tag zuweisen](images/assign_tag.png){.thumbnail}

Als Nächstes klicken Sie in das Feld `Wert`{.action} und wählen den gewünschten Wert aus dem Dropdown-Menü aus.

![Tag zuweisen - aufgefüllt](images/assign_tag_populated.png){.thumbnail}

> [!Warning]
>
> **Wenn Sie einen Schlüssel oder Wert verwenden möchten, der noch nicht existiert**, können Sie ihn erstellen, indem Sie ihn eingeben und anschließend auf `Hinzufügen Ihr-Mehrwert`{.action} klicken, wobei „Ihr-Mehrwert“ dem eingegebenen Text entspricht.
>

Klicken Sie abschließend auf die Schaltfläche `Hinzufügen`{.action}, um das Tag zu erstellen, und klicken Sie dann auf die Schaltfläche `Zuweisen`{.action} unten rechts im Fenster.

![Tag added](images/tag_added.png){.thumbnail}

Sie erhalten eine grüne Bestätigungsmeldung und sehen dann die Liste der Tags, die auf den ausgewählten Server angewendet wurden.

![Tags - Liste mit Beispiel](images/tag_list_with_example.png){.thumbnail}

### Löschen eines Tags auf einem dedizierten Server

So finden Sie die Liste der Ihrem Server zugewiesenen Tags:

1. Melden Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) an.
1. Gehen Sie in den Bereich `Bare Metal Cloud`{.action}.
1. Klicken Sie auf `Dedicated Server`{.action} und wählen Sie Ihren Server aus der Liste aus.
1. Gehen Sie zu `Tags`{.action}.

Klicken Sie auf die Schaltfläche `...`{.action}' rechts vom Tag, den Sie von Ihrem Server entfernen möchten.
Klicken Sie dann auf `Entfernen`{.action}.

![Tag list remove](images/tag_list_remove.png){.thumbnail}

Ein Bestätigungsfenster wird angezeigt. Klicken Sie auf die Schaltfläche `Bestätigen`{.action}, um die Zuweisung des Tags aufzuheben.

![Tag entfernen](images/remove_tag.png){.thumbnail}

## Weitere Informationen

Treten Sie unserer [User Community](/links/community) bei.