---
title: SQL
description: 
published: true
date: 2021-12-15T14:24:57.073Z
tags: 
editor: markdown
dateCreated: 2021-12-15T14:24:57.073Z
---

# Creation d'une Base de Donnée
> CREATE DATABASE nom ;


# Creation de table
> CREATE TABLE nom (
id SERIAL PRIMARY KEY,
nom_genre VARCHAR(8),
nom_regime VARCHAR(20) DEFAULT ‘INTERNE’,
nom_2 VARCHAR(20) NOT NULL,
email VARCHAR(200) UNIQUE
);

# Select
> SELECT * FROM candidat WHERE nomCandidat= ‘PADIRAC';

## pas de doublons
> SELECT DISTINCT NomCandidat FROM candidat ORDER BY NomCandidat;
                   



