---
title: EIGRP
description: 
published: true
date: 2022-01-27T15:35:05.054Z
tags: 
editor: markdown
dateCreated: 2022-01-27T15:31:10.997Z
---

# Mettre en place EIGRP
> Router(config)# router eigrp 1
> Router(config-router)# network 192.168.0.0 0.0.0.255

> On met 0.0.0.255 pour avoir le masque 255.255.255.0, c'est le masque inversé.
{.is-warning}

> Router(config-router)# network 192.168.1.0 0.0.0.255
> Router(config-router)# network 192.168.2.252 0.0.0.3

> Router(config-router)# no auto-summary

> no auto-summary pert de désactivé le résumé automatique des routes dans la table de routage de l’équipement.
{.is-info}

> Router(config-router)## redistribute static

> Il redistribue la route static
{.is-info}

# Route statique
> Router(config)# ip route 0.0.0.0 0.0.0.0 209.165.200.225

# Voir les Routes
> Router# show ip route
