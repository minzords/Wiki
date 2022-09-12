---
title: Création de l'Autorité de certification + HTTPS
description: 
published: true
date: 2022-09-12T09:16:19.725Z
tags: ca, https
editor: markdown
dateCreated: 2022-09-12T08:39:44.219Z
---

# Serveur CA

 ## Config d'OpenSSL
   > vi /etc/openssl/openssl.cnf
  
   `dir /etc/ssl`
 
   ### Création des dossiers
  > mkdir /etc/ssl/newcerts
  > touch /etc/ssl/index.txt
  > echo "01" > /etc/ssl/serial
  
## Création de la clé RSA privée
> openssl genrsa -des3 -out /etc/ssl/private/cakey.pem 4096

## Création du Certificat d'Autorité
> openssl req -new -x509 -days 365 -key /etc/ssl/cakey.pem -out /etc/ssl/cacert.pem

## Serveur Web
  ### Création de la clé RSA privée
  > openssl genrsa -out /etc/ssl/private/webkey.pem 4096
  ### Demandé le certificat
  > openssl req -new -key /etc/ssl/private/webkey.pem -out /etc/ssl/web_dem.pem
  
  ### Envoi du certificat
  > scp web_dem.pem root@172.16.0.20:/root
  
## Server CA
   ### Signer le certificat
   > openssl ca -policy policy_anything -out /etc/ssl/certs/servwebcert.pem -infiles /root/web_dem.pem