---
title: Bash
description: 
published: true
date: 2021-11-24T18:49:40.172Z
tags: 
editor: markdown
dateCreated: 2021-10-15T07:41:06.191Z
---

# Le Shebang

> #!/usr/bin/sh

> Vous pouvez aussi mettre directement le shell (Bash, ZSH...), sh est un lien symbolique vers le shell de la distribution.

# Déclaration de variable:

> var="Variable 1"  
> var2=2

# Afficher une variable

> echo $var  
> echo $var2

# Les fonctions

## Déclaration de la fonction

> help(){  
> echo "Utilisation:"  
> echo "\\t -m Melody"  
> echo "\\t -l LCN"  
> exit 1  
> }

## Appel de la fonction

> help

# If

> nom="Bruno"
> 
> if \[ $nom = "Bruno" \]  
> then  
> echo "Salut Bruno !"  
> else  
> echo "J'te connais pas, ouste !"  
> fi

# Les Boucles

## La boucle for

> for i in \`seq 1 10\`  
> do  
> ping -c 1 172.17.0.$i  
> done

## La boucle while

> x=1  
> while \[ $x -le 10 \]  
> do  
> echo "$x"  
> x=$((x + 1))  
> done

**Execution :**  
![capture_d’écran_du_2021-10-15_10-11-52.png](/capture_d%E2%80%99%C3%A9cran_du_2021-10-15_10-11-52.png)

# Les tableaux

## Déclaration de tableau

tab1=(a b c d e)

## Afficher un élement du tableau

`${tab1[0]}`  
![capture_d’écran_du_2021-10-15_10-39-58.png](/capture_d%E2%80%99%C3%A9cran_du_2021-10-15_10-39-58.png)

# Test de fichiers
Si le fichier existe et... :
-r : est lisible
-w : l’écriture est possible
-x : exécutable

Exemple: $
> if [ -r $2 ];

# Tests possibles sur les fichiers
-f : est un fichier ordinaire
-d : est un répertoire
-e : existe
-p : est une représentation interne d’un dispositif de communication
-c : est un pseudo-fichier du type accès caractère par caractère
-b : est un pseudo-fichier du type accès par bloc
-L : est un lien symbolique
-u : son Set UID=1
-g : son Set GID=1
-k : son Sticky Bit=1
-S : est non-vide
-z chaîne : vraie si chaîne est une chaîne vide
-w chaîne : vraie si chaîne est une chaîne non-vide

# Tests binaires
chaine1 = chaine2 : vraie si chaine1 est égale à chaine2
chaine1 != chaine2 : vraie si chaine1 n'est pas égale à chaine2
n1 -eq n2 : vraie si n1 est égal à n2
n1 -ne n2 : vraie si n1 est différent de n2
n1 -gt n2 : vraie si n1 est plus grand strictement à n2
n1 -ge n2 : vraie si n1 est plus grand ou égal à n2
n1 -lt n2 : vraie si n1 est plus petit strictement à n2
n1 -le n2 : vraie si n1 est plus petit ou égal à n2
n1 && n2 : vrai si n1 et n2 vrai
n1 || n2 : vrai si n1 ou n2 vrai

# Test d'un fichier (types, permissions...)
> test

![commande-test.png](/commande-test.png)

# Afficher des zones spécifiques d'un fichier
> cut

![exemple-cut.png](/exemple-cut.png)

# Trier le contenu
> sort

![exemple-sort.png](/exemple-sort.png)

# Memo

-   **$#** : Le Nombre de variable
-   **$0** : Le nom du Script
-   **$1** : La variable 1
-   **$2** : La variable 2
-   **$x** : La variable X
-   **$@** : Liste des paramètres
-   read -p "Votre nom ? " NAME : Lire le clavier

# Gestion des droits
## /etc/shadow
root:$6$2j8Hkor7$l7zky06VWwKaB6tO3P2kxVFAIJm8NTk96nZ5nUIn5JTyRBLuJZOMb8
Q0vAAicaRH6mgZiFofafEgOoxZKLR0B/:17442:0:99999:7:::
Daemon:*:17442:0:99999:7:::

➢ le nom de login (cf passwd)
➢ Mot de passe. Une entrée nulle ( :: )  indique qu'un mot de passe n'est pas demandé
pour entrer dans le système (une mauvaise idée en général), et une entrée *
indique que le compte a été désactivé.
➢Le nombre de jours (depuis le 1er Janvier 1970) depuis le dernier changement du mot
de passe.
➢Le nombre de jours avant que le mot de passe ne puisse être changé (un 0 indique qu'il
peut être changé à n'importe quel moment).
➢Le nombre de jours après lesquels le mot de passe doit être changé (99999 indique que
l'utilisateur peut garder son mot de passe inchangé pendant beaucoup, beaucoup d'années)
➢Le nombre de jours pour avertir l'utilisateur qu'un mot de passe ne va plus être valable
(7 pour une semaine entière)
➢ Le nombre de jours avant de désactiver le compte après expiration du mot de passe
➢ Le nombre de jours depuis le 1er Janvier 1970 pendant lesquels un compte a été
désactivé
➢ Un champ réservé pour une utilisation future possible

![permission-binaire.png](/linux/permission-binaire.png)