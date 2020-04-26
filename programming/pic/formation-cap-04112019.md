# Intégration continue avec Maven, Nexus, Jenkins, Sonar

## Jour 1 (04/11/2019)

- Sur la machine 10.65.32.38, le dossier **/home/bob/docs** contient les procédures (à récupérer avant la fin de la formation)
- Récupérer et intégrer la machine virtuelle (changer les configurations interface reseau et l'USB sur VirtualBox)
- Changer le nom de la machine virtuelle :

      echo 'git' > /etc/hostname

- Autoriser les connexions root à distance

      echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config
      
      service ssh restart
      
- Récupére l'adresse IP de la machine virtuelle

      ip addr
      
- Configuration réseau 

    - A mettre dans /etc/network/interfaces
   
            iface enp3s0 inet static
            address 10.65.32.120
            netmask 255.255.254.0
            gateway 10.65.32.1
      
    - Puis dans /etc/resolv.conf
      
          domain corp.capgemini.com
          search corp.capgemini.com
          nameserver 66.28.0.45
          nameserver 66.28.0.61
      
    - Rédemarrer 
    
          service networking restart
     
- Installation Gitlab

        apt-get -y install curl openssh-server ca-certificates postfix

        curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

        apt-get -y install gitlab-ce
        
        gitlab-ctl reconfigure
        
### Subversion

- Créer un repo : svn admin create /data/svn/dessin

- Arborescence
    - conf : fichiers de configuration
    - format
    - db : 
    - hooks : déclencher une procédure automatique après un évènement (avant/après commit, lock, etc.)
    - locks
    
- Ajouter des fichiers dans le dépôt :

      svn import /tmp/dessin file:///data/svn/dessin
    
- Récupérer le contenu d'un dépot

      svn checkout file:///data/svn/dessin newdessin
      
- Mettre à jour la copie de travail

      svn update
      
- Ajouter un fichier dans le dossier

      svn add Carre.java
    
- Statut sur l'état des fichiers

      svn status
    
- Supprimer le fichier/dossier pour ne 

       svn delete Carre.java
       
- Propriétés

       svn propset copyright 'blabla' Figures.java
       svn propget copyright Figures.java
       
       
### Git

- Systeme gestion des versions décentralisé
- Libre et open source
- Petit et rapide
- Aucun risque de perdre des données

- Trois états de Git
    
    - Modified (modifié mais pas encore référencé)
    - Staged (référencé, pret pour être commit)
    - Commited (modifié et commit en local)

- Installer Git

      apt-get -y install git
     
- Récupérer

      git clone [url]
    
- Désactiver la récupération du certificat

      git config --global hhtp.sslVerify "false"
      
- Créer un dépot

        git init
        
- Ignorer des fichiers : créer un fichier .gitignore à la racine du dépôt

        *.log #ignorer tous les fichiers qui terminent par .log
        !localhost.log
        /README.txt #ignorer uniquement le fichier README.txt à la racine du dépôt
        build/ #ignorer tous les fichers dans build
        doc/*.txt #igorer doc/notes.txt mais pas doc/server/arch.txt
        doc/**/*.txt #tous les fichiers .txt sous le répertoire doc
        
- git add *
- git config --global user.email ""
- git config --global user.name ""
- git commit -m "Initialisation du dépôt"
        
Sur Gitlab
- Créer un autre utilisateur
- Créer un groupe
- Créer un projet sous le groupe

- git remote add origin [url]
- Lister les commits : git log -v


- Créer une branche : git branch [name]
- Lister les branches : git branch
- Changer de branche en local : git checkout [name]

- Fusionner (se positionner sur la branche cible) : git merge work
- Annuler un commit : git reset -hard [numeroducommit]


- Pousser les modifs d'une branche vers une autre (se positionner sur la branche source) : git rebase master

origin = mot clé pour le dépôt distant



        
## Jour 2 (05/11/2019)

### Jenkins

- Logiciel open source d'intégration continue, développé en Java

- Dupliquer VM Git
- Supprimer Gitlab
        
        service gitlab-runsvdir stop
        
- Supprimer Gitlab CE

        apt-get remove gitlab-ce
        
- Récupérer et installer le JDK

        mkdir -p /usr/java
        cd /usr/java
        scp bob@10.65.32.168:/tmp/jdk* .
        scp bob@10.65.32.168:/tmp/openjdk* .       
        tar xfz [jdk]
        tar xfz [openjdk]

- Créer un lien sur le JDK

        ln -s ./jdk-11 ./current_jdk

- Dans le fichier ~/.bashrc, ajouter :

        export JAVA_home=/usr/java/current8jdk
        export PATH=${JAVA_HOME}/bin:${PATH}

- Sourcer et tester l'installation

        . ~/.bashrc
        java -version
        
- Changer le JDK

       cd /usr/java
       rm -f ./current_jdk     
       ln -s ./jdk1.8.0_91 ./current_jdk
        
- Modifier le fichier /etc/host pour configurer la résolution de nom
       
        echo [ip nommachine] >> /etc/hosts
        echo 192.168.56.102 devops >> /etc/hosts

- Lancer Jenkins

        java -jar jenkins.war --httpPort=8080

- Créer un utilisateur (IHM)

- Créer un projet free-style

- Arreter jenkins

    kill xxx
    
- Créer un utilisateur

        adduser user   
        cp ~/.bashrc /home/user/
        cp jenkins.war /home/user/jenkins.war
        chown user.user /home/user/.bashrc
        chown user.user /home/user/jenkins.war
        
        (changer user)

#### Créer un build maven avec jenkins

- Installez docker sous debian

        apt-get update

        apt-get -y install \
           apt-transport-https \
           ca-certificates \
           curl \
           gnupg2 \
           software-properties-common


- Ajoutez la clé de docker 

        curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -


- Vérifiez la clé 
        
        apt-key fingerprint 0EBFCD88

- Configurez le dépot stable 

        add-apt-repository \
          "deb [arch=amd64] https://download.docker.com/linux/debian \
          $(lsb_release -cs) \
          stable" 

- Ajouter les dépendances du nouveau dépot 

        apt-get update

- Installez docker 

        apt-get install docker-ce docker-ce-cli containerd.io

- Testez le fonctionnement de docker 

        docker run hello-world

- Récupérer le projet Ecosysyem

        scp bob@10.65.32.168/home/bob/ecosystem-master.tar.gz
        
- Intégrer le projet dans gitlab

- 

    curl -I -X GET http://


- Création de pipeline
    - A partir d'un script " en dur dans Jenkins"
    - A partir d'un fichier versionné dans Git
        
- Brancher Jenkins avec Nexus 
## Jour 3 (06/11/2019)

- Configurer Nexus comme proxy pour maven central

    - Prenez l'URL d'accès
    - Ajoutez la dans la balise <mirror> dans le settings.xml sur la machine de dev
    
- Utilisez un dépôt

## Maven

- TP : création d'un projet Maven avec archetype




echo "alias ll='ls -l'" >> ~/.bashrc
