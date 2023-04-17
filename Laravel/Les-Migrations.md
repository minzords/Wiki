---
title: Les migrations sur Laravel
description: 
published: true
date: 2023-04-17T12:39:21.465Z
tags: 
editor: markdown
dateCreated: 2023-04-17T12:37:22.397Z
---

# Création d'une Migration + Model
```bash
	php artisan make:model Post -m
```
Nous venons de créer une migration et un model qui se nomme Post.

Le chemin du model est: **app/Models/Post.php** et la migration: **database/migrations/2023_04_17_123859_create_posts_table.php**