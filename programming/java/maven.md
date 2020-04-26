# Maven

## Skip tests

    -Dmaven.test.skip=true
    
    
## Profiles




Maven Fundamentals

Qu'est ce que Maven ?
- Un outil de build :
	- Produit des artefacts
	- Gère les dépendances
- Outil de mangement de projet
	- Gestion des versions/releases
	- Décrit le projet
	- Produit des docs
	
A qui appartient Maven ?
	- Apache Software Fundation
	- Maven est buildé avec Maven
	- Open Source
	
Pourquoi l'utiliser ?
	- Builds répétables
	- Dépendances transitives
	- Fonctionne avec un repo local
	- Marche avec tous les IDE ou en standalone
	- Outil privilégié

Ant VS Maven
	- Ant est très procédural, déclaratif, et verbeux (plus de code à écrire), il faut décrire de manière explicite chaque action
	- Maven repose sur une convention (plutot que sur la configuration)
	- Héritage et dépendances dans Maven
	- Maven : boite noire
	- Maven est basé sur un cycle de vie d'un projet
	
Installation
	- Créer variable systeme MAVEN_HOME
	- Et ajouter dans Path %MAVEN_HOME%/bin
	
Structure d'un projet
	- src/main/java
		- java code
		- package declaration
		- tests
	- target
		- répertoire de compilation
		- tests
		- contenu du package
	- pom.xml 
		- groupId : nom de ton business (com.pluralsight)
		- artifactId : nom de l'application (HelloWorld)
		- versions
		- modelVersion (4.0.0)
		- packaging : comment partager son application (jar etc.)
		
Goals
	- clean : vide le dossier target
	- compile : compile le code source
	- package : lancer compile et package
	- install : lance package, copy les jars dans le repo local
	- deploy : lance install et deposer sur un repo externe
	
Local Repo Structure
~/.m2/repository

Dependances
	- Lister ce dont a besoin
	- Transitives
	- Besoin de : groupId, artifactId, version
	
Versions
	- SNAPSHOT : en cours de développement, image instantanée, mvn deploy produira un war différent
	- Release : version (censé être) stable, peut-etre utilisé hors dévéloppement
	
Packaging types
	- pom, jar, war, ear, maven-plugin
	- Default : jar
	
Transitives Depencencies
	Si on ajoute une dépendance X, les dépendances dont a besoin X sont aussi téléchargés
	
Scopes
	- compile : besoin du jar pour compiler et à l'execution (par défault)
	- provided : besoin du jar pour compiler mais pas à l'exécution car il est déja "provided" par l'environnement donc pas besoin de le packager dans l'app
	- runtime : pas besoin du jar à la compilation mais besoin à la compilation
	- test : besoin pour compilation et execution des tests
	- system : ne jamais utilisé
	- import (dependencies management)
	
Repositories
	http locations definit dans le super pom.xml (se trouve dans l'installation de Maven, ne jamais touché)
	Maven repository : repo.maven.apache.org
	Corporate repository : Nexus, Artifactory...
	Local repository
		Maven storage (Maven regarde en premier dedans)
		~/.m2 par default
	Dependency Repository (releases and/or snapshots)
	Plugin repository (meme fonctionnement que les dependency repository mais pour les plugins)
		

