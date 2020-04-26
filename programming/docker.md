# Docker

## Sources

- Openclassroom : https://openclassrooms.com/fr/courses/2035766-optimisez-votre-deploiement-en-creant-des-conteneurs-avec-docker

## Les containeurs

Historiquement, quand nous avions besoin de serveurs, nous achetions des serveurs physiques avec une quantité définie de CPU, de mémoire RAM ou de stockage sur le disque. Difficulté à faire face aux pics de charge. Solution : la machine virtuelle.

### Machine virtuelle
- Virtualisation des ressources (faire tourner plusieurs serveurs sur un seul serveur physique)
- Optimisation des ressources (pas de gaspillage)
- Possibilité d'installer différents OS
- Mais temps de démarrage élevé
- Ressources réservées/vérouillées même si non utilisées (solution : les conteneurs)
- ==> Virtualisation lourde

### Conteneur
- Isolation des processus
- Repose sur l'OS de la machine hôte (pas besoin d'un OS par instance)
- Légereté
- Réduction des frais d'infrastructures
- Rapidité de démarrage
- Réduction des différences entre la production, et l'environnement local sur le poste des développeurs.
- --> Virtualisation légère

## Gestion des conteneurs en local

- Immutabilité : on ne modifie pas un conteneur, on le reconstruit à partir d'une nouvelle image

### Lancer un nouveau containeur

	    docker run hello-world
	
    1. Client qui contacte le Daemon
    2. Daemon qui télécharge l'image "hello-world" depuis Docker Hub car il ne l'a pas trouvé en local
    3. Le Daemon crée un containeur à partir de l'image et lance l'executable
    4. Le stream est envoyé par le Daemon au client (terminal)
   
	        docker run -d --name web -p 80:8080 nigelpoulton/pluralsight-docker-ci
	    
	- **-d** : detach mode (en fond, pas d'affichage sur le terminal, permet de continuer à utiliser la console)
	- **-p 80:8080** : transférer le trafic du port 8080 vers le port 80 du conteneur

### Lister les containeurs existants

	    docker ps
	    
### Lister l'ensemble des images présentes en local

        docker images -a
	    
### Démarrer, stopper, supprimer containeur

        docker start xxx
        docker stop xxx
        docker rm xxx
        docker stop $(docker ps -aq)      stopper tous les containeurs
        docker rm $(docker ps -aq)      supprimer tous les containeurs
	
### Voir des infos concernant les images

	    docker images
	    
### Récupérer une image (sans pour autant lancer de conteneur)

        docker pull ubuntu
        docker pull ubuntu:14.04 (pour une version en particulier)
	
### Supprimer une image

        docker rmi ubuntu:14.04
        docker rmi $(docker images -q)   supprimer toutes les images
	
## Dockerfile

### Instructions Dockerfile

- Recette décrivant l'image Docker à créer
- Layer = étape de la construction de l'image
- Il faut limiter le nombre de layers pour que l'image soit la plus performante et la plus légère possible

1. Créer un fichier Dockerfile
2. Définir l'image qu'on souhaite utiliser comme base grace à l'instruction **FROM** (utilisable une seule fois)

        FROM debian:9
        
3. Instructions **RUN** pour executer une commande dans le conteneur (à limiter pour réduire la taille de l'image)

        RUN apt-get update -yq \
        && apt-get install curl gnupg -yq \
        && curl -sL https://deb.nodesource.com/setup_10.x | bash \
        && apt-get install nodejs -yq \
        && apt-get clean -y
        
4. Instruction **ADD** afin de copier ou de télécharger des fichiers dans l'image. Dans l'exemple, ajoute les sources de l'application locale dans le dossier /app/ de l'image

        ADD . /app/
        
5. Instruction **WORKDIR** permet de définir le répertoire courant (équivaut à cd en ligne de commande)

        WORKDIR /app
        
6. Permet d'installer le package du projet Node.js :

        RUN npm install

7. Indiquer le port sur lequel votre application écoute

        EXPOSE 2368
        
8. Indiquer quel répertoire vous voulez partager avec votre host

        VOLUME /app/logs

9. Permet à notre conteneur de savoir quelle commande il doit exécuter lors de son démarrage (à mettre en dernier)

        CMD npm run start

### Fichier .dockerignore

 - Permet de ne pas copier certains fichiers et/ou dossiers dans notre conteneur lors de l’exécution de l'instruction ADD
 - A créer à la racine du projet
 
        node_modules
        .git
        
### Lancer le conteneur
    
- Lors d'un docker build, Docker crée un conteneur pour chaque instruction, et le résultat est sauvegardé dans une layer. Le résultat final étant un ensemble de layers qui construisent une image Docker complète.
- Si une layer ne bouge pas entre deux builds, Docker ne la reconstruira pas. Seules les layers situées après une layer qui se reconstruit seront elles aussi reconstruites.

- L'argument -t permet de donner un nom à votre image Docker. 

        docker build -t ocr-docker-build .
        docker run -d -p 2368:2368 ocr-docker-build
        
## Docker Hub

- https://hub.docker.com/
- Deux types d'images sur le Docker Hub :
    - les images officielles (https://hub.docker.com/search/?type=image&image_filter=official)
    - les images personnelles
- Pour rechercher une image :
    - En ligne de commande : docker search xxx
    - Sur l'interface web
- Partager une image à la communauté
    
    - Create Repository
    - Créer un lien entre notre image ocr-docker-build:latest créée précédemment et l'image que nous voulons envoyer sur le Docker Hub 
    
            docker tag ocr-docker-build:latest YOUR_USERNAME/ocr-docker-build:latest
            
    - Envoyer l'image vers le Docker Hub
    
            docker push YOUR_USERNAME/ocr-docker-build:latest
        
        
