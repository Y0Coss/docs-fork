---
title: "Webhosting - Wie man seinen Cluster und sein Filer kennt"
excerpt: "Diese Anleitung erklärt, wie Sie die Cluster-Nummer und/oder die Filer-Nummer Ihres Webhostings"
updated: 2025-05-20
---

## Ziel

Die Webhostings laufen auf einer gemeinsam genutzten Infrastruktur namens *cluster*. OVHcloud verfügt über mehrere Cluster, auf die mehrere Webhostings verteilt sind.
Aus Gründen der Effizienz und Sicherheit wird jedes Cluster auch virtuell in mehrere Segmente aufgeteilt, die als *filers* bezeichnet werden. Die Filer enthalten selbst mehrere Webhostings.
Bei der Verwendung Ihres Webhostings muss Ihnen möglicherweise die Nummer des Clusters und/oder Filers bekannt gegeben werden, in dem sich Ihr Webhosting befindet.

**Diese Anleitung erklärt, wie Sie die Cluster-Nummer und die Filer-Nummer Ihres Webhostings.**

## Voraussetzungen

- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).
- Sie haben ein [OVHcloud Webhosting](/links/web/hosting) in Ihrem Kunden-Account.

## In der praktischen Anwendung

### Finden Sie die Nummer des Webhosting-Clusters

Klicken Sie auf die Tabs, um die **4** Schritte anzuzeigen.

> [!tabs]
> **Schritt 1**
>>
>> Loggen Sie sich in Ihr [OVHcloud Kundencenter](/links/manager) ein und gehen Sie dann in den Bereich `Web Cloud`{.action}.
>>
>> ![Web Cloud](/pages/assets/screens/control_panel/product-selection/web-cloud.png){.thumbnail}
>>
> **Schritt 2**
>>
>> Klicken Sie auf das Menü `Hosting-Pakete`{.action} und wählen Sie das betreffende Webhosting aus.
>>
>> ![Web Hosting](/pages/assets/screens/control_panel/product-selection/web-cloud/hosting-plans.png){.thumbnail}
>>
> **Schritt 3**
>>
>> Klicken Sie auf den Tab `FTP - SSH`{.action}.
>>
>> ![FTP-SSH](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/ftp-ssh.png){.thumbnail}
>> 
> **Schritt 4**
>>
>> Auf dieser Seite finden Sie die Cluster-Nummer des Webhostings unter **FTP- und SFTP-Server** (3 Ziffern von `0` bis `9`).
>>
>> ![FTP-SSH find cluster](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/find-cluster-ftp-ssh.png){.thumbnail}

### Die Filer-Nummer eines Webhostings finden

Klicken Sie auf die Tabs, um die **3** Schritte anzuzeigen.

> [!tabs]
> **Schritt 1**
>>
>> Loggen Sie sich in Ihr [OVHcloud Kundencenter](/links/manager) ein und gehen Sie dann in den Bereich `Web Cloud`{.action}.
>>
>> ![Web Cloud](/pages/assets/screens/control_panel/product-selection/web-cloud.png){.thumbnail}
>>
> **Schritt 2**
>>
>> Klicken Sie auf das Menü `Hosting-Pakete`{.action} und wählen Sie das betreffende Webhosting aus.
>>
>> ![Web Hosting](/pages/assets/screens/control_panel/product-selection/web-cloud/hosting-plans.png){.thumbnail}
>>
> **Schritt 3**
>>
>> Suchen Sie in der Randleiste **Allgemeine Informationen** auf der angezeigten Seite nach der Filer-Nummer unter `Filer`{.action}.
>>
>> ![Filer-Nummer](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/filer.png){.thumbnail}

## Weiterführende Informationen

[Webhosting - Liste der IP-Adressen pro Cluster](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP).
 
Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).
 
Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).
 
Treten Sie unserer [User Community](/links/community) bei.