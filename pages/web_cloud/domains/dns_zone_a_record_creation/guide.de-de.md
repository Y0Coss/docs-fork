---
title: "DNS-A-Eintrag für eine Domain hinzufügen"
excerpt: "Erfahren Sie, wie Sie einen DNS-Eintrag vom Typ A zu einer von OVHcloud verwalteten DNS-Zone für Ihre Domain hinzufügen."
updated: 2025-05-12
---

<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>

## Ziel

Sie möchten, dass Ihre Website über Ihren Domainnamen erreichbar ist? Hierzu muss Ihr Domainname auf die IP-Adresse des Dienstes verweisen, auf dem sich Ihre Website befindet (Webhosting, Dedicated Server, VPS...). Konfigurieren Sie anschließend die aktive DNS-Zone Ihrer Domain mit einem DNS-Eintrag vom Typ A.

**Erfahren Sie, wie Sie einen DNS-Eintrag vom Typ A zu einer von OVHcloud verwalteten DNS-Zone für Ihre Domain hinzufügen.**

> [!primary]
>
> Befolgen Sie [diese Anleitung](/pages/web_cloud/domains/dns_zone_edit), um einen DNS-Eintrag vom Typ A aus einer OVHcloud DNS-Zone zu ändern oder zu löschen.

## Voraussetzungen

- Sie besitzen eine [Domain](/links/web/domains).
- Sie besitzen eine diesem Domainnamen zugeordnete DNS-Zone bei OVHcloud.
- Sie sind in Ihrem [OVHcloud Kundencenter](/links/manager) eingeloggt und befinden sich im Bereich `Web Cloud`{.action}.

## In der praktischen Anwendung

> [!warning]
>
> Das Hinzufügen, Ändern oder Löschen von DNS-Einträgen in einer aktiven DNS-Zone ist ein schwieriges Unterfangen. Im Zweifelsfall wenden Sie sich an einen [spezialisierten Dienstleister](/links/partner).

### Einen DNS-Eintrag vom Typ A für eine Domain hinzufügen

1. Klicken Sie auf das Menü `DNS-Zone`{.action} und wählen Sie den Domainnamen aus.
2. Klicken Sie auf der angezeigten Seite auf die Schaltfläche `Eintrag hinzufügen`{.action}.
3. Wählen Sie im angezeigten Fenster das Stempelfeld vom Typ `A`{.action} aus.
4. Geben Sie anschließend in das Feld `Ziel *` die IP-Adresse (zum Beispiel `203.0.113.0`) des Dienstes ein, auf dem sich Ihre Website befindet (Webhosting, Dedicated Server, VPS etc.), und klicken Sie dann auf `Weiter`{.action}.
5. Überprüfen Sie die Zusammenfassung, und klicken Sie auf `Bestätigen`{.action}. Warten Sie bis **24** Stunden, bis die Propagation des Hinzufügens im DNS-Netzwerk voll wirksam ist.

/// details | Klicken Sie hier für weitere Informationen.

Lesen Sie unsere detaillierten Anleitungen:

- [Alle Informationen zu DNS-Zonen](/pages/web_cloud/domains/dns_zone_general_information).
- [Alle Informationen zu DNS-Einträgen](/pages/web_cloud/domains/dns_zone_records).
- [Bearbeiten der OVHcloud DNS-Zone](/pages/web_cloud/domains/dns_zone_edit).
- [Mehrere Websites auf einem Webhosting einrichten](/pages/web_cloud/web_hosting/multisites_configure_multisite).
- [Webhosting - Ändern von mit einem Webhosting verbundenen Domainnamen](/pages/web_cloud/web_hosting/multisites_modify_domain).

///

### Einen DNS-Eintrag vom Typ A für die Subdomain einer Domain hinzufügen

1. Klicken Sie auf das Menü `DNS-Zone`{.action} und wählen Sie den Domainnamen aus.
2. Klicken Sie auf der angezeigten Seite auf die Schaltfläche `Eintrag hinzufügen`{.action}.
3. Wählen Sie im angezeigten Fenster das Stempelfeld vom Typ `A`{.action} aus.
4. Geben Sie anschließend in das Feld `Subdomain` die betreffende Subdomain (zum Beispiel `www` für die Subdomain `www.domain.tld`) und im Feld `Ziel *` die IP-Adresse (zum Beispiel `203.0.113.0`) des Dienstes ein, auf dem sich Ihre Website befindet (Webhosting, Dedicated Server, VPS..). Klicken Sie anschließend auf `Weiter`{.action}.
5. Überprüfen Sie die Zusammenfassung, und klicken Sie auf `Bestätigen`{.action}. Warten Sie bis **24** Stunden, bis die Propagation des Hinzufügens im DNS-Netzwerk voll wirksam ist.

/// details | Klicken Sie hier für weitere Informationen.

Lesen Sie unsere detaillierten Anleitungen:

- [Alle Informationen zu DNS-Zonen](/pages/web_cloud/domains/dns_zone_general_information).
- [Alle Informationen zu DNS-Einträgen](/pages/web_cloud/domains/dns_zone_records).
- [Erstellung einer Subdomain](/pages/web_cloud/domains/domain_create_subdomains).
- [Bearbeiten der OVHcloud DNS-Zone](/pages/web_cloud/domains/dns_zone_edit).
- [Mehrere Websites auf einem Webhosting einrichten](/pages/web_cloud/web_hosting/multisites_configure_multisite).
- [Webhosting - Ändern von mit einem Webhosting verbundenen Domainnamen](/pages/web_cloud/web_hosting/multisites_modify_domain).

///

## Weiterführende Informationen

[Alle Informationen zu DNS-Zonen](/pages/web_cloud/domains/dns_zone_general_information).
[Alle Informationen zu DNS-Einträgen](/pages/web_cloud/domains/dns_zone_records).

Für spezielle Dienstleistungen (Referenzierung, Entwicklung etc.) wenden Sie sich bitte an die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Verwendung und Konfiguration Ihrer OVHcloud Lösungen benötigen, empfehlen wir Ihnen unsere verschiedenen [Support-Angebote](/links/support).

Für den Austausch mit unserer [User Community](/links/community).