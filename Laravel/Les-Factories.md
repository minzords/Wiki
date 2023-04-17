---
title: Introduction au factories sur Laravel
description: 
published: true
date: 2023-04-17T13:18:09.258Z
tags: 
editor: markdown
dateCreated: 2023-04-17T13:18:09.258Z
---

# Introduction
Les facteurs vont servir à peupler la base de donnée, nous allons la peupler avec des données aléatoires.

# Créer un factory
```bash
	php artisan make:factory PostFactory --model=Post
```
Ici, on génère un factory qui se nomme PostFactory et qui utilise le modèle Post qui existe déjà.

