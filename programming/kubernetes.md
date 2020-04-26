# Kubernetes

## Qu'est ce que Kubernetes ?

### D'ou vient Kubernetes ?

- Crée par Google
- Donné à la Cloud Native Computing Foundation en 2014 (open source)
- Ecrit en Go
- Kubernetes = timonier en grec (personne qui tient la barre du gouvernail)
- K8s en abrégé

### Que fait Kubernetes et pourquoi ?

- Orchestrateur pour les applications microservices pour qu'elles fonctionnent ensemble

## Architecture

### Vue d'ensemble

- Master = dirige
- Nodes = font le travail
- Deployment = manifest qui dit au master à quoi l'application doit ressembler (images, ports, réseau etc.)

### Masters

- kube-apiserver
    - expose l'API RESTful
    - consomme du JSON (via manifest files)
    - $kubectl
- cluster store
    - stockage
    - état du cluster et configuration
    - utilise etcd (= key value store, NoSQL database)
- kube-controller-manager
    - controleur des controleurs (node controller, endpoints controller, namespace controller...)
    - écoute et attendent les changements
    - aide à maintenant l'état désiré
- kube-scheduler
    - écoute apiserver pour les nouveaux pods
    - assigne des tâches aux noeuds (contraintes, resources...)

### Nodes (minions)

- kubelet
    - agent principal
    - enregistre le noeud dans le cluster
    - surveille apiserver du master
    - instancie les pods
    - reporte l'état au master
    - expose endpoint sur le port 10255
- container engine
    - gestion des conteneurs
        - pulling images
        - démarrer/stopper conteneurs
        - pluggable avec Docker ou rkt
- kube-proxy
    - gestion du réseau
        - s'assurer que chaque pod à une adresse IP unique
        - load balancing au travers les pods dans un service

## Declarative model and desired state

- Declarative model : on décrit à l'apiserver du master à quoi doit ressembler le cluster via un manifest file (yaml ou json)
- Kubernetes fait le nécessaire pour que l'état désiré corresponde à l'état actuel (si un noeud tombe par exemple)

### Pods

- Les conteneurs s'executent à l'intérieur de pods
- Pods peuvent avoir plusieurs conteneurs
- C'est un environnement délimité :
    - network stack
    - kernel namespaces
    - n containers (qui partage le même environnement et la même IP)
- Scalabilité se fait avec l'ajout/supression de pods (et non de conteneurs à l'intérieur de pods)
- Les pods sont atomiques : soit ils sont disponibles ou pas (pas d'entre deux)
- Cycle de vie : pending -> running -> succeeded/failed
- Un pod "ne revient pas à la vie", si il meurt il est remplacé par un nouveau pod similaire (cela peut etre dans sur un autre noeud)
- Les pods sont généralement déployés indirectement en déployant des objets de plus haut niveau


### Replication controllers

- scale pods, desired state etc.

### Déploiements

- Rolling updates, rollbacks etc.
- Objets REST
- Décrits via des manifests YAML ou JSON
- Déployés via l'apiserver

### Services

- Problématique : l'IP des pods peut être amené à changer (scalabilité, réplication, etc.)
- Solution : utiliser les services qui ont une IP et un DNS stables pour jouer le rôle d'intermédiaire entre les pods 
- Un service va rediriger sur les pods qui ont les mêmes labels que lui

## Installation


