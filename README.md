# Déploiement d'un site web conteneurisé — FreeFun

<p align="center">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white"/>
  <img src="https://img.shields.io/badge/Linux-Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
</p>

<p align="center">
  <em>Projet réalisé dans le cadre de la formation TSSR (RNCP niveau 5)</em>
</p>

---

## Contexte

La société FreeFun souhaite héberger son site web dans un environnement conteneurisé.
Ce projet simule ce déploiement sur une machine virtuelle Linux, en se rapprochant
des pratiques utilisées en entreprise.

---

## Stack technique et justifications

| Composant | Rôle | Justification |
|---|---|---|
| **Ubuntu Server minimal** | OS de la VM hôte | Système léger, proche d'un serveur réel, maîtrise totale des services installés |
| **Docker** | Conteneurisation | Isolation, portabilité, reproductibilité — standard entreprise |
| **Dockerfile** | Construction de l'image | Intègre le site directement dans l'image, indépendant du système hôte |
| **Docker Compose** | Orchestration | Automatise le déploiement en une commande, configuration déclarative |
| **Nginx** | Serveur web | Léger, performant, adapté aux sites statiques, très utilisé en production |

---

## Structure du projet
freefun-docker/
├── site/                  # Fichiers sources du site web
├── Dockerfile             # Construction de l'image personnalisée
├── docker-compose.yml     # Définition et orchestration du service
└── README.md

---

## Déploiement

**1. Cloner le dépôt**

```bash
git clone https://github.com/TON_USER/freefun-docker.git
cd freefun-docker
```

**2. Construire et lancer le service**

```bash
docker-compose up -d --build
```

**3. Accéder au site**
http://IP_DE_LA_VM

---

## Preuves de fonctionnement

### Site accessible

![Site en ligne](images/site.png)

### Conteneur actif (`docker ps`)

![Docker ps](images/docker-ps.png)

### Démarrage Docker Compose

![Docker Compose up](images/compose.png)

---

## Problèmes rencontrés et résolutions

| Problème | Cause | Solution appliquée |
|---|---|---|
| Résolution DNS absente | Configuration réseau manquante sur Ubuntu minimal | Ajout manuel des DNS dans `/etc/resolv.conf` |
| Outils absents (`ping`, `nano`) | Image Ubuntu minimale sans paquets additionnels | Installation via `apt install` après résolution DNS |
| Commande `docker-compose` inconnue | Docker v2 utilise `docker compose` (plugin intégré) | Identification de la version installée, adaptation de la syntaxe |

---

## Bilan

Ce projet m'a permis de déployer une application web conteneurisée de bout en bout :
configuration de la VM, construction d'une image Docker personnalisée, serveur Nginx,
et automatisation via Docker Compose.

Les difficultés rencontrées — résolution DNS, environnement minimal, gestion des versions
de Docker — m'ont conduit à diagnostiquer et résoudre des problèmes concrets
d'infrastructure, directement transférables en situation professionnelle.

---

## Auteur

**Projet réalisé dans le cadre de la formation TSSR (RNCP niveau 5)**