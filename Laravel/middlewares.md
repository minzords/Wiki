---
title: Les Middleware
description: 
published: true
date: 2023-06-05T09:38:03.147Z
tags: 
editor: markdown
dateCreated: 2023-06-05T09:36:32.956Z
---

# Utilisation d'un Middleware avec un groupe de route
```php
Route::middleware('auth')->group(function () {
    Route::get('/foo', 'HomeController@foo')->name('foo');
    Route::get('/bar', 'HomeController@bar')->name('bar');
});

# routes/web.php
```

Dans cet exemple, /foo et /bar vont utiliser le middleware auth, ce qui va permettre que ses routes soient uniquement accessibles à un compte connecté.

# Pour une route simple
```php
	Route::get('/foo', 'HomeController@foo')->name('foo')->middleware('auth');
```