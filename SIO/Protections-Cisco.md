---
title: Protection aux attaques
description: 
published: true
date: 2022-01-20T20:37:29.158Z
tags: 
editor: markdown
dateCreated: 2022-01-20T20:37:29.158Z
---

# DHCP snooping
## Mettre le DHCP snooping sur tout les ports
> Switch(config)# ip dhcp snooping

## Pour un VLAN
> Switch(config)# ip dhcp snooping vlan 3

## Mettre le Truck 
> Switch(config)# interface fastethernet0/0
> Switch(config-if)# ip dhcp snooping trust
mettre un rate limit
>  Switch(config-if)# ip dhcp snooping limit rate 5

## Definir une limite d'adresse mac
>  Switch(config-if)# switchport port-security maximum 3

## Association d'adresse MAC en statique
> (config-if)#switchport port-security mac-address <mac>

## Association d'adresse MAC en dynamique
> (config-if)#switchport port-security

Mettre des adresses remanente
> (config-if)#switchport port-security mac-address sticky

Enlever les adresses remanentes
> (config-if)#no switchport port-security mac-address sticky

Mettre des adresses remanente tout en enregistrant une adresse statique
> (config-if)#switchport port-security mac-address sticky <adresse MAC>

En cas de detection de violation de securité
config-if)#switchport port-security violation protect | restrict [ shutdown
> switchport port-security violation restrict

# DHCP SPOOFING
## Activation du DHCP Snooping sur tout les ports
> Switch(config)#ip dhcp snooping

## Activation du DHCP Snooping sur un VLAN
> Switch(config)#ip dhcp snooping vlan 10

## Configurer le truck
Switch(config)#interface GigabitEthernet0/1
Switch(config-if)#ip dhcp snooping trust

## Activer l'option DHCP 82
> Switch(config)#ip dhcp snooping information option

# Spanning-Tree
## Activer le Spanning-Tree
> Switch(config)#spanning-tree mode rapid-pvst


