---
title: NAT & PAT
description: 
published: true
date: 2022-03-24T07:21:05.182Z
tags: 
editor: markdown
dateCreated: 2022-03-03T14:26:14.583Z
---

# Cours
## Fonctionnement
- NAT statique : 1 adresse interne ↔ 1 adresse externe
- NAT dynamique : n adresses internes ↔ m adresses externes
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

# Mettre le NAT en inside
> R1(config)# interface fa0/0
> R1(config-if)# ip nat inside

# Mettre le NAT en outside
> R1(config)# interface fa0/1
> R1(config-if)# ip nat outside

# Configurer du NAT statique
> R1(config)# ip nat inside source static 192.168.1.100 201.49.10.30

# Créer une Pool d'adresse
> R1(config)# ip nat pool POOL-NAT-LAN2 201.49.10.17 201.49.10.30 netmask 255.255.255.240

# Crée une ACL
> R1(config)# access-list 1 deny 192.168.1.100
> R1(config)#access-list 1 permit 192.168.1.0 0.0.0.255

# Configuration du NAT
> R1(config)#ip nat inside source list 1 pool POOL-NAT-LAN2

>R1(config)#ip nat inside source list 1 pool POOL-NAT-LAN2 overload

> **overload**: si il y a plus de machines dans le réseau privé que d’adresses publiques disponibles il fait du PAT
{.is-info}

# Voir les translations NAT
> R1(config)# show ip nat translations