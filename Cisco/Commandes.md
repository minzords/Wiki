---
title: Commandes Cisco
description: 
published: true
date: 2021-12-15T16:59:56.543Z
tags: 
editor: markdown
dateCreated: 2021-12-15T16:58:27.804Z
---

# RESET
> Switch# erase nvram:
Switch# delete flash:vlan.dat
Switch# delete flash:config.text
Switch# reload

# Afficher la version
> Router# show version

# Routage Statique
> Router (config)# ip route 172.18.0.0 255.255.0.0 172.17.3.254

> **172.18.0.0** : le réseau, **172.17.3.254** la passerelle
{.is-info}

# Voir la liste de routage
> Router# show ip route