---
title: NAT-PAT Cours
description: 
published: true
date: 2022-03-24T07:41:31.368Z
tags: 
editor: markdown
dateCreated: 2022-03-24T07:41:31.368Z
---

# Cours
## Fonctionnement
- NAT statique : 1 adresse interne ↔ 1 adresse externe
- NAT dynamique : n adresses internes ↔ m adresses externes
## Définitions
- NAT: Transfère d'adresse.
- PAT: Transfère de Ports
## Avantages
- Économie des adresses publiques
- augmente la souplesse des connexions au réseau public
- permet un adressage du réseau local indépendant du FAI
-  sécurité : adresses internes non divulguée à l’extérieur
## Inconvénients
- dégradation des performances : le routeur doit examiner chaque paquet
- perte de l’adressage de bout en bout → ex : problème en FTP
- perte de traçabilité → dépannage plus difficile
# IP Publique
![ip_priver.png](/cours/ip_priver.png)
# Vocabulaire
- Inside address : adresse privée.
- Outside address : adresse publique.