---
title: Batch
description: 
published: true
date: 2022-01-18T15:00:38.485Z
tags: 
editor: markdown
dateCreated: 2022-01-18T15:00:38.485Z
---

# Exemple:
> @echo off
> if "%1"=="" goto usage
> if "%1"=="/?" goto usage
> if exist %1\NUL (
> 	echo le repertoire %1 existe !
> ) else (
> 	if exist %1 (
> 		echo le fichier %1 est présent
> 	) else echo %1 est absent
> )
> goto fin
> :usage
> echo usage : testFic nomfichier
> :fin

# Adduser
> net user totos azerty /add /homedir:"C:\Users\toto"

# Exemple
> @echo off
>
> if "%1"=="" goto help
> if "%1"=="/?" goto help
>
> if exist "C:\Users\%1\" (
>        echo le repertoire existe et le compte existe déjà.
> ) else (
>        net user %1 %2 /add /homedir:"C:\Users\%1"
> )
>
> goto fin
>
> :help
> echo fichier nom de l'utilisateur mot de passe
> :fin


Prompt
> dir /q

> del "C:\truc\truc"

> mkdir toto toto /add

> net user

> set localgroup administrateur /add toto