---
title: Protections aux attaques
description: 
published: true
date: 2022-02-21T16:30:24.413Z
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

# Spanning-Tree
## Activer le Spanning-Tree
> Switch(config)#spanning-tree mode rapid-pvst

# SSH
## Creation de clé RSA SSH
> crypto key generate rsa general-keys modulus 1024
## Activer SSH
>ip ssh version 2
## Config SSH
> Switch(config)#ip ssh time-out 60
Switch(config)#ip ssh authentication-retries 3 
