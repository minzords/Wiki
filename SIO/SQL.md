---
title: SQL
description: 
published: true
date: 2022-09-20T14:44:54.241Z
tags: 
editor: markdown
dateCreated: 2022-09-20T14:44:54.241Z
---

# USER

> CREATE USER 'etudiant'@'%' IDENTIFIED BY 'Btssio2017';
{.is-success}

> GRANT ALL PRIVILEGES ON *.* TO 'etudiant'@'%' WITH GRANT OPTION;
{.is-success}

> FLUSH PRIVILEGES;
{.is-success}

# UPDATE

> UPDATE Visiteur SET mdp = 'toto' WHERE login = 'agest';
{.is-success}
