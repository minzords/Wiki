---
title: EIGRP
description: 
published: true
date: 2022-01-27T15:31:10.997Z
tags: 
editor: markdown
dateCreated: 2022-01-27T15:31:10.997Z
---

# Mettre en place EIGRP
> R1(config)# router eigrp 1
> network 192.168.0.0 0.0.0.255

> On met 0.0.0.255 pour avoir le masque 255.255.255.0, c'est le masque inversé.
{.is-warning}

> network 192.168.1.0 0.0.0.255
> network 192.168.2.252 0.0.0.3
> no auto-summary

> R2(config-router)# redistribute static

> Il redistribue la route static
{.is-info}

# Route statique
> R2(config)# ip route 0.0.0.0 0.0.0.0 209.165.200.225

# Voir les Routes
> show ip route
