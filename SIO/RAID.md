---
title: RAID
description: 
published: true
date: 2022-02-04T07:25:14.744Z
tags: 
editor: markdown
dateCreated: 2022-02-04T07:25:14.744Z
---

# RAID 0
![raid0.png](/linux/raid/raid0.png)
- Avantages : cumuler la capacité de plusieurs disques physiques sur un même lecteur logique, augmenter les performances en lecture/ écriture.
- Inconvénient : pas plus de sécurité. Au contraire : si un des disques crashe, on perd toutes les données.

Les entreprises utilisent RAID 0 principalement pour les tâches nécessitant un accès rapide à une grande capacité de stockage temporaire sur disques.

# RAID 1
![raid1.png](/linux/raid/raid1.png)
- Avantages : sécurité (si un des disques crashe, on conserve toutes les données), performances en lecture (mais pas en écriture). 
- Inconvénient : gaspillage de 50% de l'espace disque.

Garantie de protection des données et la redondance. Le coût par gigaoctet de capacité utilisable est un élément secondaire.

# RAID 3 et 4



