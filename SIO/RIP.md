---
title: RIP
description: 
published: true
date: 2022-01-27T15:37:45.175Z
tags: 
editor: markdown
dateCreated: 2022-01-27T15:37:45.175Z
---

# Activer le protocol RIP
> Router(config-router)# router rip
> Router(config-router)# version 2

# Ajouter les réseaux connus
> Router(config-router)# network 192.168.1.10
> Router(config-router)# network 192.168.1.20

# Changer la distance
> Router(config)# router rip
> Router(config-router)# distance 89