---
title: Installation de Kubernetes avec MiniKube
description: 
published: true
date: 2023-10-31T10:18:44.905Z
tags: 
editor: markdown
dateCreated: 2023-09-13T19:13:39.758Z
---

# Installation de Podman et runc
```bash
	dnf install podman runc
  systemctl enable --now podman
```

# Installation de l'outil
```bash
	curl https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 -o /usr/local/bin/minikube
	chmod +x /usr/local/bin/minikube
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

# Patch a faire en root
```bash
loginctl enable-linger 1000
```

# Installer minikube
```bash
	minikube config set rootless true
  minikube start --driver=podman --container-runtime=cri-o
```

# (Optionnel) Activer le Panneau de configuration web
```
	minikube dashboard
```