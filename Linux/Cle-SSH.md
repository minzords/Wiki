---
title: Creation et mises en place d'une clé SSH
description: 
published: true
date: 2021-10-15T18:22:49.696Z
tags: 
editor: markdown
dateCreated: 2021-10-15T18:22:47.009Z
---

# Creation de la clé en RSA 4096 :
> ssh-keygen -t rsa -b 4096
> 
# Installation de la clé sur le serveur :
> ssh-copy-id -i ~/.ssh/id_rsa user@host
> 