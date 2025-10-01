---
title: "Wie reagieren Sie auf eine ungewöhnliche Aktivität, die auf Ihrem Webhosting erkannt wurde"
excerpt: "Erfahren Sie, welche Schritte Sie unternehmen sollten, wenn eine ungewöhnliche Aktivität auf Ihrem OVHcloud Webhosting erkannt wird"
updated: 2025-10-01
---

## Ziel

Dieses Handbuch erklärt, warum eine **ungewöhnliche Aktivität** auf Ihrem Webhosting erkannt werden kann, welche **vorübergehenden Auswirkungen** (Sicherheitsblockierungen) es gibt und **wie Sie die Funktionen wiederherstellen**, sobald das Problem behoben ist.

**Erfahren Sie, wie Sie auf eine ungewöhnliche Aktivität auf Ihrem OVHcloud Webhosting reagieren.**

## Voraussetzungen

- Eine [OVHcloud Webhosting-Angebot](/links/web/hosting) besitzen.
- Angemeldet sein bei Ihrem [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

> [!primary]
> Um Ihre Website und Ihre Besucher zu schützen, aktivieren wir automatisch Sicherheitsmaßnahmen, sobald eine ungewöhnliche Aktivität auf Ihrem Webhosting erkannt wird. Es handelt sich nicht immer um einen Angriff: Die Ursache kann beispielsweise eine falsche Konfiguration Ihrer Website, ein Drittanbieter-Skript oder eine fehlerhafte Erweiterung sein.

### Warum wird diese Nachricht angezeigt?

Wir haben eine ungewöhnliche Aktivität erkannt, die Ihren Dienst beeinträchtigen könnte:

- Fall 1 – **Erkennung von Malware**: Wahrscheinlich vorhandene **schädliche Dateien**.
- Fall 2 – **Unüblicher E-Mail-Versand über PHP** (Skripte/Anwendungen).
- Fall 3 – **Unüblicher Ausgangsverkehr** (Verbindungen nach außen).

Aus Sicherheitsgründen und je nach Situation können einige Funktionen vorübergehend blockiert werden:

- **Zugriff auf die Website** (Fall 1)
- **E-Mail-Versand über PHP** (Fall 1 und Fall 2).
- **Ausgangsverkehr (TCP OUT)** (Fall 1 und Fall 3).

### Welche Auswirkungen hat dies auf meine Website?

- Abhängig von der erkannten ungewöhnlichen Aktivität kann Ihre **Website nicht mehr online** sein und für Besucher nicht zugänglich sein.
- Der **E-Mail-Versand über PHP** (Formulare, Benachrichtigungen usw.) und/oder die **Ausgangsverbindungen** (externe APIs, Webhooks, Updates über HTTP usw.) können **vorübergehend deaktiviert** sein, je nach Fall.

### Schritte zur Behebung der Situation

#### Fall 1 — Erkennung von Malware

Ihr Webhosting enthält wahrscheinlich schädliche Dateien. Um diese Anomalien zu verstehen und zu beheben, folgen Sie unserem Leitfaden [Fallbeispiel - Tipps nach einem Hackerangriff auf Ihre Website](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked).

**Nachdem die Reinigung abgeschlossen ist**, besuchen Sie den Abschnitt [Sicherheitsmaßnahmen aufheben](#lift-security-measures) weiter unten.

#### Fall 2 — Unüblicher E-Mail-Versand über PHP

Ihre Website hat eine höhere Anzahl von E-Mails über PHP gesendet. Dies kann **berechtigt** sein (Kampagne, Newsletter-Modul) oder **nicht gewünscht** (abusive Nutzung eines Formulars, falsch konfiguriertes Skript, kompromittierte Erweiterung). Um diese Anomalien zu verstehen und zu beheben, konsultieren Sie unseren Leitfaden [Verfolgen und verwalten Sie automatisierte E-Mails Ihres Webhostings](/pages/web_cloud/web_hosting/mail_function_script_records).

**Nachdem die Situation normalisiert ist**, besuchen Sie den Abschnitt [Sicherheitsmaßnahmen aufheben](#lift-security-measures).

> [!primary]
>
> Diese Maßnahme betrifft **nicht** den Versand von Nachrichten von Ihrer E-Mail-Adresse (über den Webmailer oder einen E-Mail-Client). Sie gilt ausschließlich für **E-Mails, die von Ihren Skripten gesendet werden** (PHP-Funktion `mail()` oder SMTP-Versand durch eine Anwendung von Ihrem Webhosting aus).

#### Fall 3 — Unüblicher Ausgangsverkehr (TCP OUT)

Ihre Website stellt viele externe Verbindungen her (APIs, Updates, HTTP-Aufrufe usw.). Dies kann auf einen Defekt hinweisen. Um diese Anomalien zu verstehen und zu beheben, konsultieren Sie unseren Leitfaden [Fallbeispiel - Tipps nach einem Hackerangriff auf Ihre Website](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked).

**Nachdem die Reinigung abgeschlossen ist**, besuchen Sie den Abschnitt [Sicherheitsmaßnahmen aufheben](#lift-security-measures) weiter unten.

### Sicherheitsmaßnahmen aufheben <a name="lift-security-measures"></a>

> [!warning]
>
> Führen Sie diesen Schritt **erst nach Anwendung der oben genannten Empfehlungen** durch (Diagnose, Korrekturen/Updates, Sicherheitsmaßnahmen). Wenn bei einem nächsten Scan erneut eine ungewöhnliche Aktivität erkannt wird, werden die **Sicherheitsmaßnahmen automatisch erneut aktiviert**. Sie erhalten eine neue Benachrichtigung und die Blockierungen bleiben bestehen, bis die **Situation endgültig gelöst** ist.

1. Melden Sie sich bei Ihrem [OVHcloud Kundencenter](/links/manager) an, gehen Sie zu `Web Cloud`{.action} und klicken Sie auf Ihr Webhosting.
2. Eine **Warnfenster** erscheint: `Ungewöhnliche Aktivität auf Ihrem Webhosting`. Wenn Sie auf den Button `Später`{.action} klicken, erscheint eine **Warnbann** `Ungewöhnliche Aktivität erkannt` oben auf der Seite. Klicken Sie auf `Mehr erfahren`{.action}, um das Warnfenster erneut zu öffnen.
3. **Aktivieren Sie** das Feld: `Ich bestätige, dass ich alle notwendigen Maßnahmen ergriffen habe, um das Problem zu beheben`.
4. Klicken Sie auf `Sicherheitsmaßnahmen aufheben`{.action}.
5. Eine **Bestätigungs-Bann** erscheint oben auf der Seite: `Ihr Webhosting wird analysiert, um die Sicherheitsmaßnahmen aufzuheben.` Verfolgen Sie den Fortschritt durch Klicken auf den Link `Laufende Aufgaben ansehen`{.action} oder direkt über den Tab `Laufende Aufgaben`{.action}.

> [!warning]
>
> Stellen Sie sicher, dass Ihr Dienst **für die automatische Entsperrung berechtigt ist** (einige Zustände erlauben nicht, die Maßnahmen sofort aufzuheben).

## Weiterführende Informationen <a name="go-further"></a>

[Wie sichert man eine Website?](/pages/web_cloud/web_hosting/secure_your_website)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.