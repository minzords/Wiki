---
title: Configurer l'IPv6
description: 
published: true
date: 2022-07-18T16:14:59.462Z
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

# Avoir l'IPv6 via un tunnel GRE
**address** est le bloc fourni par le fournisseur, 
**source** est notre IPv4,
**destination**  est l'IPv4 du routeur du fournisseur.

> interface Tunnel0
>   no ip address
>   ipv6 enable
>   ipv6 address 2001:470:b259::2/48
>   tunnel source 192.99.123.50
>   tunnel destination 70.22.35.32
>   tunnel mode ipv6ip
> ipv6 route ::/0 Tunnel0
{.is-info}
