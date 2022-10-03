---
title: HAProxy
description: 
published: true
date: 2022-10-03T14:52:44.532Z
tags: 
editor: markdown
dateCreated: 2022-10-03T14:23:54.352Z
---

# Version Simple
## Configuration des sites
`vi /etc/haproxy/haproxy.cfg`

> listen httpProxy
> bind 172.16.0.13:80
> balance roundrobin
> option httpclose
> option httpchk HEAD / HTTP/1.0
> server serv1 10.0.1.1:80 check
> server serv2 10.0.1.2:80 check
{.is-success}

## Mise en place des statistiques
`vi /etc/haproxy/haproxy.cfg`
> stats uri /statsHaproxy
> stats auth root:Qwerty123
> stats refresh 30s
{.is-success}

## Répartition inégalitaire

> server web1 10.0.1.1:80 weight 100 check
> server web2 10.0.1.2:80 weight 50 check
{.is-success}

## HTTPS
> mkdir /etc/haproxy/cert
> cd /etc/haproxy/cert
> openssl genrsa -out privateKey.pem 4096
> openssl req -new -x509 -days 365 -key privateKey.pem -out cert.pem
> cat cert.pem privateKey.pem > sodecaf.pem
{.is-success}

`vi /etc/haproxy/haproxy.cfg`
> frontend https-in
> bind 172.16.0.13:443 ssl crt /etc/haproxy/cert/sodecaf.pem
> default_backend fermeweb
{.is-success}

# Utilisation du frontend/backend
> frontend proxypublic
> bind 172.16.0.13:80
> default_backend fermeweb
> backend fermeweb
> balance roundrobin
> option httpclose
> option httpchk HEAD / HTTP/1.0
> server web1 10.0.1.1:80 check
> server web2 10.0.1.2:80 check
> stats uri /statsHaproxy
> stats auth root:Qwerty123
> stats refresh 30s
{.is-success}
