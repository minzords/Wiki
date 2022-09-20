---
title: Installation d'un DNS Avec Bind
description: 
published: true
date: 2022-09-20T08:19:29.440Z
tags: 
editor: markdown
dateCreated: 2022-09-20T08:04:33.388Z
---

# Déclaration des zones:
`vi /etc/bind/named.conf.local`

> // Domaine mandriva.com
>zone "mandriva.com" {
>	type master;
>	file "db.mandriva.com";
>};
>
> // Zone inverser du réseau 10.0.1.0
>zone "1.0.10.in-addr.arpa" {
>	type master;
>	file "db.10.0.1.0.rev"
>};
{.is-success}

# Création des zones:
`vi /var/cache/bind/db.gentoo.fr`
> $TTL    86400
>@       IN      SOA     ns1.mandriva.com. ns2.mandriva.com. (
>                   2022092001           ; Serial
>                         3600           ; Refresh [1h]
>                          600           ; Retry   [10m]
>                        86400           ; Expire  [1d]
>                          600 )         ; Negative Cache TTL [1h]
>
>@       	IN      NS      ns1.mandriva.com.
>@				IN			NS			ns2.mandriva.com.
>
>@ 		IN 	A 		10.0.1.1
>ns2	IN	A 		10.0.1.2
>ns2	IN	A			10.0.1.3
>www	IN	CNAME	mandriva.com.
{.is-success}

## Zone inverser
`vi /var/cache/bind/db.10.0.1.0.rev`

>$TTL    86400
>@       IN      SOA     ns1.mandriva.com. ns2.mandriva.com. (
>                   2022092001           ; Serial
>                         3600           ; Refresh [1h]
>                          600           ; Retry   [10m]
>                        86400           ; Expire  [1d]
>                          600 )         ; Negative Cache TTL [1h]
>
>@       	IN      NS      ns1.mandriva.com.
>@				IN			NS			ns2.mandriva.com.
>
>1	 		IN 	PTR 	mandriva.com.
>2			IN	PTR		ns1.mandriva.com.
>3			IN	PTR		ns2.mandriva.com.
{.is-success}

# Mises en place du Forward
`vi /etc/bind/named.conf.options`

>options {
>	directory "/var/cache/bind";
>
> // Forward sur le DNS 8.8.8.8
>	forwarders {
>	 	8.8.8.8;
>	};
>
>	dnssec-validation auto;
>
>	listen-on-v6 { any; };
>};
{.is-success}