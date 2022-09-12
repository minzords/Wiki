---
title: Autorité de certification
description: 
published: true
date: 2022-09-12T08:39:44.219Z
tags: 
editor: markdown
dateCreated: 2022-09-12T08:39:44.219Z
---

# Config d'OpenSSL
  > vi /etc/openssl/openssl.cnf
  
 `dir /etc/ssl`
 
 ## Création des dossiers
  > mkdir /etc/ssl/newcerts
  > touch /etc/ssl/index.txt
  > echo "01" > /etc/ssl/serial
  
# Création de la clé RSA privée
> openssl genrsa -des3 -out private/cakey.pem 4096

# Création du Certificat d'Autorité
> openssl req -new -x509 -days 365 -key /etc/ssl/cakey.pem -out /etc/ssl/certs/cacert.pem