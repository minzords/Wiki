---
title: Fiche Controle
description: 
published: true
date: 2022-01-21T11:35:55.490Z
tags: 
editor: markdown
dateCreated: 2022-01-21T11:35:55.490Z
---

# Securité
## La bannière
> switch(config)#banner motd !ACCES RESERVE !

## Changer le Hostname
> switch(config)#hostname switch_Minz

## Créer un utilisateur
> switch(config)#username admin privilege 15 secret Mdpsecu

## Mettre un mots de passe
> enable password Mdpsecu

## Configurer un utilisateur et un mot de passe pour la console
> switch(config)#line con 0
> switch(config-line)# speed 9600
> switch(config-line)#password Mdpsecu
> switch(config-line)#login local

## Configurer un domaine
> Switch(config)#ip domain-name minz.local

## SSH
### Creation de clé RSA SSH
> crypto key generate rsa general-keys modulus 1024
### Activer SSH
> ip ssh version 2
### Config SSH
> Switch(config)#ip ssh time-out 60
> Switch(config)#ip ssh authentication-retries 3

## Désactiver Telnet
> Switch(config)#line vty 0 2
> Switch(config-line)#access-class SSH_ACCESS in
> Switch(config-line)#login local
> Switch(config-line)#transport input ssh
> Switch(config-line)#transport output ssh

## Chiffrement ses mots de passe
> switch(config)# service password-encryption



## DHCP snooping
### Mettre le DHCP snooping sur tout les ports
> Switch(config)# ip dhcp snooping

### Pour un VLAN
> Switch(config)# ip dhcp snooping vlan 3

## Mettre le Truck 
> Switch(config)# interface fastethernet0/0
> Switch(config-if)# ip dhcp snooping trust
mettre un rate limit
>  Switch(config-if)# ip dhcp snooping limit rate 5

### Definir une limite d'adresse mac
>  Switch(config-if)# switchport port-security maximum 3

### Association d'adresse MAC en statique
> (config-if)#switchport port-security mac-address <mac>

### Association d'adresse MAC en dynamique
> (config-if)#switchport port-security

### Mettre des adresses remanente
> (config-if)#switchport port-security mac-address sticky

### Enlever les adresses remanentes
> (config-if)#no switchport port-security mac-address sticky

### Mettre des adresses remanente tout en enregistrant une adresse statique
> (config-if)#switchport port-security mac-address sticky <adresse MAC>

### En cas de detection de violation de securité
switchport port-security violation protect | restrict [ shutdown
> switchport port-security violation restrict

## DHCP SPOOFING
### Activation du DHCP Snooping sur tout les ports
> Switch(config)#ip dhcp snooping

### Activation du DHCP Snooping sur un VLAN
> Switch(config)#ip dhcp snooping vlan 10

### Configurer le truck
Switch(config)#interface GigabitEthernet0/1
Switch(config-if)#ip dhcp snooping trust

### Activer l'option DHCP 82
> Switch(config)#ip dhcp snooping information option

## Spanning-Tree
### Activer le Spanning-Tree
> Switch(config)#spanning-tree mode rapid-pvst

