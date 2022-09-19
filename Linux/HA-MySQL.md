---
title: HA sur MySQL
description: 
published: true
date: 2022-09-19T12:23:24.405Z
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

## Arrêté l'esclave
`STOP SLAVE;`

# Définition de l'esclave sur Mysql
`mysql -p`

`CHANGE MASTER TO MASTER_HOST='172.16.0.10', MASTER_USER='ha', MASTER_PASSWORD='qwerty123', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=328;`

`START SLAVE;`
`EXIT;`

# Réactiver l'écriture sur le maître
`mysql -p`
`UNLOCK TABLES;`
`EXIT;`

# Vérification
`SHOW MASTER STATUS;`
Sur le maître.