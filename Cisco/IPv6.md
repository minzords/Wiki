---
title: Configurer Ipv6
description: 
published: true
date: 2022-03-03T09:09:33.438Z
tags: 
editor: markdown
dateCreated: 2022-03-03T08:26:16.265Z
---

# Activer IPv6
> R1(config)# interface serial0/0/0

# Ajouter une adresse local
> R1(config)# interface serial0/0/0
> R1(config-if)# ipv6 address fe80::1 link-local

# Ajouter une adresse
> R1(config)# interface serial0/0/0
> R1(config-if)# ipv6 address 2001:470:1d35::1/56