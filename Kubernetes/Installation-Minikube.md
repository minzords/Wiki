---
title: Installation de Kubernetes avec MiniKube
description: 
published: true
date: 2023-09-13T19:25:54.856Z
tags: 
editor: markdown
dateCreated: 2023-09-13T19:13:39.758Z
---

# Installation de Docker
```bash
	apt install ca-certificates curl gnupg
	install -m 0755 -d /etc/apt/keyrings
	curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
	chmod a+r /etc/apt/keyrings/docker.gpg

	echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
	apt update
  apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

# Installation de l'outil
```bash
	wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
	install minikube-linux-amd64 /usr/local/bin/minikube
```
```bash
	minikube start
	echo 'alias kubectl="minikube kubectl --"' >> ~/.bashrc
```