---
title: HA sur MySQL
description: 
published: true
date: 2022-09-19T10:00:17.762Z
tags: 
editor: markdown
dateCreated: 2022-07-18T15:49:39.714Z
---

Dans cet exemple, la base répliqué sera qwerty.

# Création d'un compte SQL
`CREATE USER 'ha'@'%' IDENTIFIED BY 'qwerty123';`
`GRANT REPLICATION SLAVE ON *.* TO 'ha'@'%';`
`FLUSH PRIVILEGES;`
`EXIT;`

# Configuration de MySQL
`vi /etc/mysql/mariadb.conf.d/50-server.cnf`

> [mysqld]
> user                    = mysql
> pid-file                = /run/mysqld/mysqld.pid
> basedir                 = /usr
> datadir                 = /var/lib/mysql
> tmpdir                  = /tmp
> lc-messages-dir         = /usr/share/mysql
> lc-messages             = en_US
> skip-external-locking
> 
> character-set-server  = utf8mb4
> collation-server      = utf8mb4_general_ci
> 
> log_error		= /var/log/mysql/error.log
> 
> server-id		= 100
> 
> log_bin			= /var/log/mysql/mysql-bin.log
> 
> expire_logs_days	= 10
> max_binlog_size		= 100M
> 
> binlog_do_db		= qwerty
{.is-success}

## Redémarrer Mysql
`/etc/init.d/mariadb restart`

# Bloquer l'écriture
`mysql -p`
`FLUSH TABLES WITH READ LOCK;`



# Configuration de l'esclave
`vi /etc/mysql/mariadb.conf.d/50-server.cnf`

> [mysqld]
> user = mysql
> pid-file = /run/mysqld/mysqld.pid
> basedir = /usr
> datadir = /var/lib/mysql
> tmpdir = /tmp
> lc-messages-dir = /usr/share/mysql
> lc-messages = en_US
> skip-external-locking
> 
> character-set-server = utf8mb4
> collation-server = utf8mb4_general_ci
> 
> log_error = /var/log/mysql/error.log
> 
> server-id = 104
> expire_logs_days = 10
> max_binlog_size = 100M
> 
> master-retry-count = 20
> replicate-do-db = qwerty
{.is-info}

## Redémarrer Mysql
`/etc/init.d/mariadb restart`

# Définition de l'esclave sur Mysql
`mysql -p`

`change master to master_host='10.0.1.1', master_user='ha', master_password='qwerty123', master_log_file='mysql-bin.000001', master_log_pos=3921;`

`start slave;`
`exit;`

# Réactiver l'écriture sur le maître
`mysql -p`
`UNLOCK TABLES;`
`EXIT;`