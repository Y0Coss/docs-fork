---
title: "Facturation"
excerpt: "Facturation du produit Backup Agent"
updated: 2026-01-07
---
 
## Objectif

Vous avez le produit Backup Agent et vous souhaitez connaître les modalités de facturation du produit.

## En pratique

Le produit se base sur deux éléments pour proposer son service :

* Le Veeam Agent installé sur vos serveurs Baremetal.
* L'OVHcloud Object Storage.

Nous ne facturons pas l'agent sur vos serveurs, c'est-à-dire que vous pouvez en déployer sur un ou plusieurs serveurs Baremetal, cela ne vous coûtera rien.

Cependant, l'utilisation de l'OVHcloud Object Storage vous est facturé, à l'échelle du GB par mois. Vous serez donc facturé au début de chaque mois pour votre utilisation du mois précédent.

Vous retrouverez le prix du GB par mois sur notre site web.

Vous avez à votre disposition un dashboard "Facturation" dans votre Manager pour visualiser votre consommation actuelle, et ainsi prédire la facture finale en fin de mois.

Exemple 1 : Vous avez déployé l'agent sur 3 serveurs Baremetal, et ceux-ci envoient leurs données vers leurs Vault respectifs. La totalité des capacités utilisés par vos données de sauvegarde sur les Vault est de 600GB. Vous serez donc facturé à la fin du mois pour 600GB.

Exemple 2 : Vous avez déployé l'agent sur 10 serveurs Baremetal, et ceux-ci envoient leurs données vers leurs Vault respectifs. La totalité des capacités utilisés par vos données de sauvegarde sur les Vault est de 600GB. Après quelques sauvegardes, vous retirez l'agent de 4 serveurs, supprimant les données après 14 jours. L'utilisation totale des Vault tombe à 400GB. Vous serez facturé à la fin du mois pour 600GB.