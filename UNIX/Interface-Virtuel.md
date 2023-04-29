---
title: Créer une interface réseau virtuel sur BSD
description: 
published: true
date: 2023-04-29T15:19:35.634Z
tags: 
editor: markdown
dateCreated: 2023-04-29T15:19:35.634Z
---

# Introduction
Cette manière de créer une interface réseau virtuel est la même sur tout les BSD (OpenBSD,NetBSD,FreeBSD)

Dans cet exemple, je vais créer une interface avec l'IP 10.0.3.254/24 sans passerelle.

# Création de l'interface
```bash
	ifconfig vether0 create
	ifconfig vether0 inet 10.0.3.254 netmask 255.255.255.0
```

