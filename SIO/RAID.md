---
title: RAID
description: 
published: true
date: 2022-02-04T07:42:33.448Z
tags: 
editor: markdown
dateCreated: 2022-02-04T07:25:14.744Z
---

# RAID 0

![raid0.png](/linux/raid/raid0.png)

-   Avantages : cumuler la capacité de plusieurs disques physiques sur un même lecteur logique, augmenter les performances en lecture/ écriture.
-   Inconvénient : pas plus de sécurité. Au contraire : si un des disques crashe, on perd toutes les données.

Les entreprises utilisent RAID 0 principalement pour les tâches nécessitant un accès rapide à une grande capacité de stockage temporaire sur disques.

# RAID 1

![raid1.png](/linux/raid/raid1.png)

-   Avantages : sécurité (si un des disques crashe, on conserve toutes les données), performances en lecture (mais pas en écriture).
-   Inconvénient : gaspillage de 50% de l'espace disque.

Garantie de protection des données et la redondance. Le coût par gigaoctet de capacité utilisable est un élément secondaire.

# RAID 3 et 4

![raid3.png](/linux/raid/raid3.png)

-   Avantages : sécurité, résiste à la panne d’un disque, augmentation des performances en lecture et en écriture.
-   Inconvénient : le disque qui stocke la parité est beaucoup plus sollicité que les autres, et a donc une durée de vie plus courte.

Les RAID 3 et 4 sont remplacés par les RAID 5 ou 6

# RAID 5

![raid5.png](/linux/raid/raid5.png)

-   Avantages : sécurité (si un des disques crashe, on conserve toutes les données), performances en lecture.
-   Inconvénient : les écritures sont pénalisées (temps de calcul des parités)

RAID 5 est le plus utilisé, car il gère mieux les pannes.

# RAID 10

![raid10.png](/linux/raid/raid10.png)

-   Rassemble le RAID 0 et 1 (deux disques durs assemblés en RAID 1 + deux autres disques sont assemblés de la même façon)
-   Il faut donc un minimum de quatre disques et toujours en nombre pair.

Meilleure redondance des données dans chaque sous-unité pour une meilleure sécurité, tandis que la répartition des données sur plusieurs unités logiques accélère la lecture et l’écriture.

# Comment choisir les RAID.

![diagramme.png](/linux/raid/diagramme.png)

-   la sécurité : RAID 1 ou 1+0 et 5 offrent tous les deux un niveau de sécurité élevé ;
-   les performances : RAID 1 offre de meilleures performances que RAID 5 en lecture, mais souffre lors d'importantes opérations d'écriture.
-   le coût : le coût est directement lié à la capacité de stockage de la grappe.

![tableau.png](/linux/raid/tableau.png)

# Vocabulaire

-   **Grappe** : unité de stockage créée à partir de plusieurs disques
-   Striping : augmentation des performances grâce à l'accès simultané à plusieurs disques.
-   **Duplexing** : tolérance des pannes des contrôleurs, car chaque disque est branché sur un contrôleur différent.
-   **MTBF** : Middle Time Between Failures (temps moyen de fonctionnement avant panne), environ 500 000 heures.
-   **Mode dégradé** : lorsqu'un disque dur crashe, le système continue à fonctionner dans un mode dit "dégradé", ce qui traduit le fait que la sécurité n'est plus assurée tant que le disque fautif n'est pas remplacé.
-   **Hot swap ou hot plug** : propriété de certains disques à pouvoir être remplacés "à chaud", sans éteindre le système.