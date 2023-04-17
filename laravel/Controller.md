---
title: Introduction au Controller dans Laravel
description: 
published: true
date: 2023-04-17T10:55:15.361Z
tags: 
editor: markdown
dateCreated: 2023-04-17T10:51:32.312Z
---

# Créer un controller
```bash
	php artisan make:controller HomeController
```
Cette commande va créer un controller nommé HomeController dans **app/Http/Controllers**.

# Exemple

```php
class HomeController extends Controller
{
    public function index()
    {
        $title = 'Accueil';
        // Revoie de la variable title a la vue.
        return view('accueil', compact('title'));
        /***
         *  Ou bien:
         * return view('accueil')->with('title', $title);
         * return view('accueil', ['title' => $title]);
         */
    }
}
```
