---
title: "Comment résoudre une activité anormale détectée sur votre hébergement web"
excerpt: "Découvrez comment résoudre une activité inhabituelle sur votre hébergement OVHcloud"
updated: 2025-09-25
---

## Objectif

Ce guide vous explique pourquoi une **activité anormale** peut être détectée sur votre hébergement, quelles en sont les **conséquences temporaires** (blocages de sécurité) et **comment rétablir** les fonctionnalités une fois le problème résolu.

## Prérequis

- Disposer d’une offre d’[hébergement web OVHcloud](/links/web/hosting).
- Être connecté à votre [espace client OVHcloud](/links/manager).

## En pratique

> [!primary]
> Selon la situation, votre site **n’a pas forcément été piraté**. Les mécanismes de protection peuvent se déclencher sur des comportements inhabituels **non malveillants** (mauvaise configuration, script tiers, extension défaillante, etc.).

### Pourquoi ce message s’affiche-t-il ?

Nous avons détecté une activité inhabituelle pouvant nuire à votre service :

- Cas 1 – **Malwares détectés** : présence probable de **fichiers malveillants**.
- Cas 2 – **Volume inhabituel d’envois d’e-mails** depuis vos scripts.
- Cas 3 – **Volume inhabituel de requêtes sortantes** (connexions vers l’extérieur).

Par mesure de sécurité, certaines fonctionnalités sont temporairement bloquées :

- **Envoi d’e-mails via PHP** (cas 1 et cas 2).
- **Requêtes sortantes (TCP OUT)** (cas 1 et cas 3).

### Quelles conséquences pour mon site web ?

- Votre **site web reste en ligne** et accessible aux visiteurs.  
- Les **envois d’e-mails** (formulaires, notifications, etc.) et/ou les **connexions sortantes** (API externes, webhooks, mises à jour via HTTP, etc.) peuvent être **temporairement désactivés**, selon le cas.

### Étapes à suivre pour résoudre le problème

#### Cas 1 — Malwares détectés

Votre hébergement contient très probablement des fichiers malveillants. Pour comprendre et résoudre ces anomalies, suivez notre guide « [Cas d'usage - Conseils suite au piratage de votre site Web](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked) ».

**Une fois le nettoyage terminé**, dirigez-vous vers la section « [lever les mesures de sécurité](#lift-security-measures) ».

#### Cas 2 — Volume inhabituel d’envois d’e-mails

Votre site web a émis un nombre d’e-mails supérieur à la normale. Cela peut être **légitime** (campagne, module newsletter) ou **non désiré** (formulaire abusé, script mal configuré, extension compromise). Pour comprendre et résoudre ces anomalies, suivez notre guide « [Suivre et gérer les e-mails automatisés de son hébergement web](/pages/web_cloud/web_hosting/mail_function_script_records) ».

**Une fois la situation normalisée**, dirigez-vous vers la section « [lever les mesures de sécurité](#lift-security-measures) ».

#### Cas 3 — Volume inhabituel de requêtes sortantes (TCP OUT)

Votre site effectue de nombreuses connexions externes (API, mises à jour, appels HTTP, etc.). Cela peut être révélateur d’un dysfonctionnement. Pour comprendre et résoudre ces anomalies, suivez notre guide « [Cas d'usage - Conseils suite au piratage de votre site Web](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked) ».

**Une fois le nettoyage terminé**, dirigez-vous vers la section « [lever les mesures de sécurité](#lift-security-measures) ».

### Lever les mesures de sécurité <a name="lift-security-measures"></a>

> [!warning]
>
> Ne procédez à cette étape **qu’après** avoir :
>
> - supprimé les fichiers malveillants détectés.
> - mis à jour votre CMS, ses extensions et thèmes.
> - changé les mots de passe concernés (FTP/SSH, base de données, back-office, etc.).
>
> Tant que le nettoyage n’est pas terminé, lever les mesures de sécurité risquerait une **recontamination immédiate**.

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), rendez-vous dans `Web Cloud`{.action} puis cliquez sur votre hébergement.
2. Une **fenêtre d’alerte** s’affiche : `« Activité anormale sur votre hébergement »`. Si vous la fermez en cliquant sur `Plus tard`{.action}, une **bannière d’alerte** `« Activité anormale détectée »` apparaît en haut de la page. Cliquez sur **En savoir plus** pour rouvrir la fenêtre d’alerte.
3. **Cochez** la case : `Je confirme avoir effectué toutes les actions nécessaires pour résoudre le problème`.
4. Cliquez sur **Lever les mesures de sécurité**.
5. Une **bannière de confirmation** s’affiche en haut de la page : `Votre hébergement est en cours d’analyse afin de lever les mesures de sécurité.` Suivez la progression en cliquant sur le lien `Voir les tâches en cours`{.action} ou directement depuis l’onglet `Tâches en cours`{.action}.

> [!warning]
>
> Assurez-vous que votre service est **éligible au déblocage automatique** (certains états ne permettent pas de lever immédiatement les mesures).

## Aller plus loin

[Comment sécuriser un site Web ?](/pages/web_cloud/web_hosting/secure_your_website)

Échangez avec notre [communauté d'utilisateurs](/links/community).

