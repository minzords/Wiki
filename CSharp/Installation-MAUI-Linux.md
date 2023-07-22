---
title: Installer MAUI sur Linux
description: 
published: true
date: 2023-07-22T14:01:58.685Z
tags: 
editor: markdown
dateCreated: 2023-07-22T14:01:58.685Z
---

# Installation de C# (Dotnet)
- [Documentation Officiel](https://learn.microsoft.com/en-us/dotnet/core/install/linux)
{.links-list}

# Installation de MAUI
```bash
	sudo dotnet workload install maui-android --temp-dir=~/.tmp
```

# Verification
```bash
	dotnet workload list
```
Résultat:
```
[florianb@Archlinux Bureau]$ dotnet workload list

ID de la charge de travail installée      Version de manifeste      Source de l’installation
--------------------------------------------------------------------------------------------
maui-android                              7.0.92/7.0.100            SDK 7.0.100             

Utilisez « recherche de la charge de travail dotnet » pour rechercher d’autres charges de travail à installer.

```
