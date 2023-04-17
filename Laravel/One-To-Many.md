---
title: La relation One to Many
description: 
published: true
date: 2023-04-17T18:31:37.562Z
tags: 
editor: markdown
dateCreated: 2023-04-17T18:31:37.562Z
---

# Créer le modèle et la migration
```php
	php artisan make:model -m Comment
```

# Configurer la base de donnée
```php
	public function up(): void
  {
  		Schema::create('comments', function (Blueprint $table) {
      		$table->id();
          $table->mediumText('content');
          $table->timestamps();

					// post_id est lié à la clé primaire de la table posts
          $table->unsignedBigInteger("post_id");
          $table->foreign("post_id")->references("id")->on("posts");
        });
    }
```
## Version simplifiée
```php
	public function up(): void
  {
  		Schema::create('comments', function (Blueprint $table) {
      		// post_id est lié à la clé primaire de la table posts
          $table->foreignId('post_id')->constrained();
        });
    }
```