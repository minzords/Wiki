---
title: Creation et mises en place d'une clé SSH
description: 
published: true
date: 2022-11-04T13:37:11.294Z
tags: 
editor: markdown
dateCreated: 2021-10-15T18:22:47.009Z
---

# Creation de la clé en ed25519 :
> ssh-keygen -t ed25519
> 
# Installation de la clé sur le serveur :
> ssh-copy-id -i ~/.ssh/id_ecdsa user@host
> 