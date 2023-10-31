---
title: Installation de Kubernetes avec MiniKube
description: 
published: true
date: 2023-10-31T09:20:34.558Z
tags: 
editor: markdown
dateCreated: 2023-09-13T19:13:39.758Z
---

# Installation de Podman
```bash
	apt install podman
```

# Installation de l'outil
```bash
	wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
	install minikube-linux-amd64 /usr/local/bin/minikube
```

# Creation de l'utilisateur kube
```bash
	adduser podman
```

# Passer sur l'utilisation standard
```bash
	su - podman
```

# Activer l'autocompletion
```bash
		echo 'alias kubectl="minikube kubectl --"' >> ~/.bashrc && source .bashrc
```

# Installer minikube
```bash
	minikube config set rootless true
  minikube start
```


# Activer le Panneau de configuration web
```
	minikube dashboard
```