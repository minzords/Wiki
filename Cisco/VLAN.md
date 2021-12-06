---
title: Les VLAN
description: 
published: true
date: 2021-12-03T10:28:52.033Z
tags: 
editor: markdown
dateCreated: 2021-12-03T10:28:49.796Z
---

# Creation du VLAN
> switch(conf)# vlan 2
> Switch(config-vlan)# name Production

# Affectation
> switch(conf)# interface fa0/1
> Switch(config-if)# switchport mode access
> Switch(config-if)# switchport access vlan 2

# Avec un range
> switch(conf)# interface range fa0/1-6
> Switch(config-if)# switchport mode access
> Switch(config-if)# switchport access vlan 2

# Définir le VLAN 2 (Production)

> switch(conf)# vlan 2
> switch(conf-vlan)# name Production
> switch(conf-vlan)# exit

# Rattacher le port fa0/1 au vlan 2
> switch(conf)# interface fa0/1
> switch(conf-if)# switchport mode access
> switch(conf-if)# switchport access vlan 2

# Rattacher le port fa0/5 à fa0/10 au vlan 2
> switch(conf)# interface range fa0/5
> switch(conf-if-range)# switchport mode access
> switch(conf-if-range)# switchport access vlan 2