---
title: RIP
description: 
published: true
date: 2022-02-03T15:44:23.209Z
tags: 
editor: markdown
dateCreated: 2022-01-27T15:37:45.175Z
---

# Activer le protocol RIP
> Router(config-router)# router rip
> Router(config-router)# version 2
> Router(config-router)# no auto-summary

# Ajouter les réseaux connus
> Router(config-router)# network 192.168.10.0
> Router(config-router)# network 192.168.20.0

# Changer la distance
> Router(config)# router rip
> Router(config-router)# distance 89

# Activé le DEBUG
> Router# debug ip rip

# Rappel sur les routes statiques
> Router(config)# ip route 192.168.5.0 255.255.255.0 10.1.4.2