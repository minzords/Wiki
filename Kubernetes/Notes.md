---
title: Note - Commande Kubernetes
description: 
published: true
date: 2023-10-18T11:40:53.386Z
tags: 
editor: markdown
dateCreated: 2023-10-18T11:27:43.910Z
---

# Créer un déploiement
```bash
	kubectl create deployment serveur-nginx --image nginx
```
Dans cet exemple, on crée le déploiement serveur-nginx qui utilise l'image docker nginx.

# Afficher les métadonnées d'un déploiement
```bash
	kubectl describe deploy serveur-nginx
```