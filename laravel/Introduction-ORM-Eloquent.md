---
title: Introduction à l'ORM Eloquent
description: 
published: true
date: 2023-04-17T14:12:13.725Z
tags: 
editor: markdown
dateCreated: 2023-04-17T14:07:15.455Z
---

# Introduction
Omnis voluptatem quam dignissimos voluptatem cumque nemo.

# Debug
Laravel fournie une fonction pour debug, elle va afficher toutes les informations sur une variable, tableau... Cette fonction est ***dd***.

(DD = die and dump)
```php
	dd($posts);
```

# Récupération de toutes données d'un modèle
```php
	$posts = Post::all();
  dd($posts);
```

## Exemple d'un affichage dans la vue
```php
	@foreach ($posts as $post)
		<h2>{{ $post->title }}</h2>
	@endforeach
```
