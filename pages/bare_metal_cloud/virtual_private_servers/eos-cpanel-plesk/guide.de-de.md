---
title: "End of Plesk und cPanel-Support für VPS - Gewährleistung der Kontinuität Ihrer Dienste"
excerpt: "Finden Sie heraus, wann die Betriebssysteme Ihres OVHcloud VPS, die die Plesk- und cPanel-Lizenzen betreffen, nicht mehr unterstützt werden"
updated: 2025-07-21
---

## Ziel

In dieser Anleitung erfahren Sie, wie Sie die Kontinuität Ihrer Dienste gewährleisten können, indem Sie Ihren OVHcloud VPS nach dem angekündigten Auslaufen des Supports für mehrere Betriebssysteme auf ein Betriebssystem migrieren, das mit den neuesten Versionen von **Plesk** und **cPanel** kompatibel ist.

**Hier finden Sie die Support-Enddaten für die Betriebssysteme Ihres OVHcloud VPS, die sich auf Plesk- und cPanel-Lizenzen auswirken.**

## Voraussetzungen

- Eine [VPS](/links/bare-metal/vps) Lösung mit einer [kompatiblen Distribution](/links/bare-metal/vps-os).

## In der praktischen Anwendung

Die Herausgeber **Plesk** und **cPanel** kündigen das Ende der Unterstützung für die folgenden Betriebssysteme an:

| Betriebssystem | Produkt      | Ende des Supports  |
| -------------- | ------------ | ------------------ |
| Ubuntu 18.04   | Plesk        | **1. Januar 2026** |
| Debian 10      | Plesk        | **1. Januar 2026** |
| CentOS 7       | Plesk/cPanel | **1. Januar 2026** |
| CloudLinux 7   | Plesk/cPanel | **1. Januar 2026** |

Weitere Informationen zu Support-Zwecken finden Sie in der offiziellen Dokumentation:

- [Plesk](https://docs.plesk.com/release-notes/obsidian/system-requirements/){.external}.
- [cPanel](https://docs.cpanel.net/knowledge-base/cpanel-product/cpanel-deprecation-plan/){.external}.

### Was kann ich konkret tun?

> [!primary]
>
> Aus der Sicht der **Sicherheit** setzt die fortgesetzte Verwendung eines nicht unterstützten Betriebssystems Angriffe voraus.
Wir empfehlen Ihnen, die folgenden Dokumente zu lesen: [cPanel Recommendations](https://docs.cpanel.net/knowledge-base/security/tips-to-make-your-server-more-secure/){.external} und [Plesk Recommendations](https://docs.plesk.com/en-US/obsidian/administrator-guide/plesk-administration/securing-plesk.59464/){.external}.

#### 1. Aktuelles System überprüfen

Loggen Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager), gehen Sie zum Bereich `Bare Metal Cloud`{.action} und wählen Sie Ihren Server im Bereich `Virtual Private Server`{.action} aus.

![EOS Plesk cPanel](images/vpshome.png){.thumbnail}

Auf der Registerkarte `Start`{.action} finden Sie die Details Ihres Betriebssystems im Abschnitt `Betriebssystem / Distribution` aus der Box `Ihr VPS`.

#### 2. Ermitteln eines kompatiblen Betriebssystems

Wenn Ihr Betriebssystem Teil des Betriebssystems ist, das nicht mehr unterstützt wird, migrieren Sie zu einem kompatiblen System, das vom Herausgeber empfohlen wird.

Weitere Informationen finden Sie in der offiziellen Dokumentation zu unterstützten Betriebssystemen:

- [Liste der von Plesk unterstützten Betriebssysteme](https://docs.plesk.com/release-notes/obsidian/system-requirements/){.external}.
- [Liste der cPanel kompatiblen Betriebssysteme](https://docs.cpanel.net/installation-guide/system-requirements/){.external}.

#### 3. Dienst migrieren

**Option A — Manuelle Neuinstallation**

1. [Backup Eurer Daten](/pages/bare_metal_cloud/virtual_private_servers/using-automated-backups-on-a-vps) (Web-Inhalte, Datenbanken, E-Mails, etc.).
2. Installieren Sie ein kompatibles Betriebssystem über das OVHcloud Kundencenter im Abschnitt „Neuinstallation Ihres VPS“ unseres Handbuchs [Erste Schritte mit einem VPS](/pages/bare_metal_cloud/virtual_private_servers/starting_with_a_vps).
3. [Reinstall cPanel](/pages/bare_metal_cloud/virtual_private_servers/cpanel) oder Plesk auf dem neuen System.
4. Stellen Sie Ihre Daten aus Ihren Backups wieder her.

**Option B - Migration über Plesk oder cPanel**

Diese Methode wird empfohlen, wenn Sie eine neue VPS-Instanz mit einem aktualisierten System zusammen mit der alten Instanz bereitstellen können.

Bestellen Sie einen neuen VPS mit einem kompatiblen Betriebssystem, falls Sie dies noch nicht getan haben. [Install cPanel](/pages/bare_metal_cloud/virtual_private_servers/cpanel) oder Plesk.

Verwenden Sie das Migrations-Tool Ihrer Wahl. Mit diesen Tools können Sie Ihre Websites, Datenbanken, E-Mail-Accounts und Konfigurationen automatisch von einem VPS auf einen anderen übertragen:

- Plesk Migrator - [Offizielle Dokumentation](https://docs.plesk.com/en-US/obsidian/migration-guide/introduction.75496/){.external}.
- cPanel Transfer Tool - [Official documentation](https://docs.cpanel.net/whm/transfers/transfer-tool/){.external}.

**Option C - Aktualisierung vor Ort (erweitert)**

Wenn Sie keine neue Instanz eines VPS bereitstellen können, können Sie bestimmte Tools verwenden, um **Ihr Betriebssystem direkt zu aktualisieren**, während Plesk oder cPanel installiert bleibt. Diese Methode ist für fortgeschrittene Benutzer vorgesehen, da sie Risiken birgt, wenn sie falsch ausgeführt wird.

- **Plesk** (Wechsel von CentOS 7 zu AlmaLinux 8): Verwenden Sie das Skript `centos2alma` in der [offiziellen Plesk-Dokumentation](https://github.com/plesk/centos2alma){.external}. Siehe auch die ausführlichen Anweisungen in [Plesk Support](https://support.plesk.com/hc/en-us/articles/12377714344983){.external}.

- Verwenden Sie für **cPanel** (Wechsel von CentOS 7 zu AlmaLinux 8) das Tool **Elevate**, das in der [offiziellen cPanel-Dokumentation](https://cpanel.github.io/elevate/){.external}. zur Verfügung gestellt wird.

> [!primary]
>
> Diese Tools sind nicht zu 100 % garantiert und erfordern vollständige Backups, bevor Sie fortfahren. Stellen Sie außerdem sicher, dass Ihr VPS über ausreichende Ressourcen verfügt (RAM, CPU, Festplatte).

## Weiterführende Informationen <a name="go-further"></a>

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Treten Sie unserer [User Community](/links/community) bei.