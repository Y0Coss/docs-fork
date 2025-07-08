---
title: "Was tun, wenn die Seite „Your IP has been banned“ angezeigt wird?"
excerpt: "Hier erfahren Sie, wie Sie Ihre IP-Adresse entsperren, wenn Ihre Website eine Seite mit der Aufschrift „Your IP has been banned“ anzeigt."
update: 2025-07-08
---

## Ziel

Die Shared Hosting Infrastruktur, auf der sich die OVHcloud Webhostings befinden, verfügt über mehrere Sicherheitssysteme.
Wenn Ihre Website eine Seite namens „Your IP has been banned“ anzeigt, bedeutet dies, dass die IP-Adresse, von der aus Sie auf Ihre Website zugreifen möchten, von unseren Sicherheitssystemen vorübergehend blockiert wurde.

![your-ip-has-been-banned](/pages/assets/screens/other/browsers/errors/your-ip-has-been-banned.png){.thumbnail}

**Erfahren Sie, wie Sie Ihre IP-Adresse entsperren können, wenn Ihre Website eine „Your IP has been banned“ Seite anzeigt.**

## Voraussetzungen

- Sie haben ein [OVHcloud Webhosting](/links/web/hosting).
- Sie verfügen über die [Login-Daten](/pages/web_cloud/web_hosting/ftp_connection) für den FTP-Speicherplatz Ihres Hostings.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

Die Seite „Your IP has been banned“ kann aus verschiedenen Gründen angezeigt werden (nicht abschließende Liste):

- Von derselben IP-Adresse aus werden sehr viele ähnliche oder andere Anfragen innerhalb eines extrem kurzen Zeitrahmens gestellt.
- Anfragen von der betreffenden IP-Adresse aus sind verdächtig.

### 1 - Rufen Sie die Informationen auf der Seite „Your IP has been banned“ ab

Rufen Sie zunächst die folgenden drei Informationen auf, die auf der Seite „Your IP has been banned“ angezeigt werden:

- `IP address` (Beispiel: 203.0.113.0).
- `Date` (z.B.: 2025-07-01T16:30:45:150Z).
- `Request ID` (zum Beispiel: AbCdEf-your-request-ID-GhIjKlM).

### 2 - Support kontaktieren

Sobald diese Daten erfasst wurden, erstellen Sie ein [Support-Ticket](https://help.ovhcloud.com/csm?id=csm_get_help) im OVHcloud Help Center. Geben Sie dabei Folgendes an:

- Die auf der Seite angetroffene Nachricht („Your IP has been banned“).
- Die drei zuvor abgerufenen Elemente (`IP address`, `Date` und `Request ID`).
- Die URL, unter der die Seite angezeigt wird (z. B.: `https://www.domain.tld/index.php`).
- Der verwendete Internetbrowser.

Der Support wird Sie schnellstmöglich kontaktieren und Ihnen den Grund für die Sperrung mitteilen.

## Weiterführende Informationen

[Anwendungsbeispiele - Ihre Website ist von einem Hack betroffen](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked)
 
Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).
 
Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).
 
Treten Sie unserer [User Community](/links/community) bei.