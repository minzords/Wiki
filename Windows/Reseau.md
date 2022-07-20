---
title: Commandes Réseau
description: 
published: true
date: 2021-12-16T08:51:42.948Z
tags: 
editor: markdown
dateCreated: 2021-12-16T08:49:22.074Z
---

# Afficher la configuration complète des cartes réseau
> ipconfig /all

# Libèrer l'IP
> ipconfig /release

# Renouveler l'adresse IP
> ipconfig /renew

# Afficher le cache DNS
> ipconfig /displaydns

# Vider le cache DNS
> ipconfig /flushdns

# Afficher les adresses mac
> getmac /v

# Afficher la configuration réseau
> netsh interface show interface


# Config l'IP en DHCP
> netsh interface ip set address "Connexion au réseau local" dhcp

# Config l'IP en manuel
## IPv4
> netsh interface ip set address name="Connexion au réseau local" static 10.1.2.220 255.255.255.0 10.1.2.254
> IP: 10.1.2.220 Masque: 255.255.255.0 Passerelle: 10.1.2.254
{.is-info}

## IPv6
> netsh interface ipv6 add address "Connexion au réseau local" 2001:db8:290c:1291::1

# Config DNS
## DNS Primaire
### IPv4
> netsh interface ip set dns name="Connexion au réseau local" static 207.164.234.129
### IPv6
> netsh interface ip set dns name="Connexion au réseau local" static 2620:10A:80BB::10
## DNS Secondaire
> netsh interface ip add dns name="Connexion au réseau local" 149.112.121.10 index=2
### IPv6
> netsh interface ip set dns name="Connexion au réseau local" static 2620:10A:80BC::10 index=2

# Avoir l'ip et l'adresse MAC (ARP)
> arp -a

# Tester le DNS
> nslookup videotron.com



