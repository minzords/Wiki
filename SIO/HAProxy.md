---
title: HAProxy
description: 
published: true
date: 2022-10-03T14:23:54.352Z
tags: 
editor: markdown
dateCreated: 2022-10-03T14:23:54.352Z
---

# Configuration des sites
`vi /etc/haproxy/haproxy.cfg`

> listen httpProxy
> bind 172.16.0.13:80
> balance roundrobin
> option httpclose
> option httpchk HEAD / HTTP/1.0
> server serv1 10.0.1.1:80 check
> server serv2 10.0.1.2:80 check
{.is-success}

# Mise en place des statistiques
`vi /etc/haproxy/haproxy.cfg`
> stats uri /statsHaproxy
> stats auth root:Qwerty123
> stats refresh 30s
{.is-success}

# Utilisation du frontend/backend
> frontend proxypublic
> bind 172.16.0.13:80
> default_backend fermeweb
> backend fermeweb
> alance roundrobin
> option httpclose
> option httpchk HEAD / HTTP/1.0
> server web1 10.0.1.1:80 check
> server web2 10.0.1.2:80 check
> stats uri /statsHaproxy
> stats auth root:Qwerty123
> stats refresh 30s
{.is-success}
