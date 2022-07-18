---
title: Configurer l'IPv6
description: 
published: true
date: 2022-07-18T16:07:36.524Z
tags: 
editor: markdown
dateCreated: 2022-03-03T08:26:16.265Z
---

# Activer l'IPv6
> R1(config)# ipv6 unicast-routing

# Ajouter une adresse local
> R1(config)# interface serial0/0/0
> R1(config-if)# ipv6 address fe80::1 link-local

# Ajouter une adresse
> R1(config)# interface serial0/0/1
> R1(config-if)# ipv6 address 2001:470:1d35::1/64