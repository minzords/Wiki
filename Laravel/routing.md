---
title: Le Routing sur Laravel
description: 
published: true
date: 2023-04-17T17:46:26.033Z
tags: 
editor: markdown
dateCreated: 2023-04-17T09:20:00.244Z
---

# Fonctionnement
La configuration des routes pour une application web ce trouve dans **routes/web.php**.

# Mises en place d'une route
Voici comment créer une **route "/"** qui va utiliser la **fonction index** du **controller** HomeController (qui est dans app/Http/Controllers/HomeController.php)

```php
	Route::get('/', [HomeController::class, 'index']);
```

## Definir un nom à la route

```php
	return view('accueil', ['title' => $title])->name("accueil");
```

# Mises en place d'une route qui renvoie une vue (non recommandé)

```php
	Route::get('/', function () {
    return view('accueil');
});
```
Cette route va renvoyer la vue accueil sans utiliser un controller. 

> Cette pratique ne respecte pas la méthode MVC.
{.is-warning}
