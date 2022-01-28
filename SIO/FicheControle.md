---
title: Fiche Controle
description: 
published: true
date: 2022-01-28T15:40:01.844Z
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

> En cas de problème testé avec: login authentication default
{.is-warning}


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
> Switch(config)#line vty 0 15
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
> Switch(config)#interface GigabitEthernet0/1
> Switch(config-if)#ip dhcp snooping trust

### Activer l'option DHCP 82
> Switch(config)#ip dhcp snooping information option

## Spanning-Tree
### Activer le Spanning-Tree
> Switch(config)#spanning-tree mode rapid-pvst

# VLAN
## Creation du VLAN
> switch(conf)# vlan 2
> Switch(config-vlan)# name Production

## Affectation
> switch(conf)# interface fa0/1
> Switch(config-if)# switchport mode access
> Switch(config-if)# switchport access vlan 2

## Avec un range
> switch(conf)# interface range fa0/1-6
> Switch(config-if)# switchport mode access
> Switch(config-if)# switchport access vlan 2

## Définir le VLAN 2 (Production)
> switch(conf)# vlan 2
> switch(conf-vlan)# name Production
> switch(conf-vlan)# exit

## Attribution d'une IP sur le VLAN
> switch(config)#int vlan 2
> switch(config-if)#ip address 10.0.0.2 255.0.0.0
> switch(config-if)#no shutdown

## Rattacher le port fa0/1 au vlan 2
> switch(conf)# interface fa0/1
> switch(conf-if)# switchport mode access
> switch(conf-if)# switchport access vlan 2

## Rattacher le port fa0/5 à fa0/10 au vlan 2
> switch(conf)# interface range fa0/5
> switch(conf-if-range)# switchport mode access
> switch(conf-if-range)# switchport access vlan 2
  
# Routage inter-VLAN
## Autorisé certains VLANS et changement du VLAN par défaut
> Switch(config)#interface fa0/1
> Switch(config-if)#switchport mode trunk
> Switch(config-if)#switchport trunk allowed vlan 20,30,99
> Switch(config-if)# switchport trunk native vlan 99
> Switch(config-if)#no shutdown

## Allocation du VLAN
> Switch(config)#interface fa0/2 ( dépend du câblage bien
> sur )
> Switch(config-if)#switchport access vlan 20
> Switch(config-if)#no shutdown
> Switch(config-if)#exit
> Switch(config)#interface fa0/3
> Switch(config-if)#switchport access vlan 30
> Switch(config-if)#no shutdown

## Config du Routeur
> Router#configuration terminal
> Router(config)#interface fa0/0
> Router(config-if)#no shutdown

***Pour le VLAN 20***
> Router(config)#interface fa0/0.20
> Router(config-subif)#encapsulation dot1Q 20
> Router(config-subif)#ip address 192.168.20.254 255.255.255.0
> Router(config-subif)#no shutdown

## Encapsulation dot1q
> Switch(config)#interface fa0/3
> Switch(config-if)#switchport mode trunk
> Switch(config-if)#switchport trunk allowed vlan 20,30,99
> Switch(config-if)# switchport trunk native vlan 99
> Switch(config-if)#no shutdown

# VTP
## Mode serveur
***Le domaine:***
> server(config)# vtp domain testVTP

***Definir le mode:***
> server(config)# vtp mode server

***Mettre un mots de passe (optionnel)***
> server(config)# VTP password azerty

## Mode client
***Le domaine:***
> server(config)# vtp domain testVTP

***Definir le mode:***
> client (config)# vtp mode client
> client (config)# vtp mode transparent

***Mettre un mots de passe (optionnel)***
> client (config)#vtp password azerty

## Verification de la configuration
> server# show vtp status

## Changement de la version
> vtp version 2

## Configuration du Protocole DTP
> Switch_A(config)# interface fastethernet 0/1
> Switch_A(config-if)# shutdown
> Switch_A(config-if)# switchport mode trunk
> Switch_A(config-if)# switchport nonegotiate
> Switch_A(config-if)# no shutdown