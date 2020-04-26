- Spring : the Big Picture

## C'est quoi ?

- Spring Framework : faciliter le développement des applications Java (Spring Web, Data, AOP, Core)
- Spring Projects : Spring LDAP, Security, Batch, Data, etc.)
- Spring Boot : permet de créer rapidement et facilement une application Java, moins de configuration, simplifie le déploiement
- Spring Cloud : architecture distribuée, micro-services

## Pourquoi ?

- Complémentaire à Java EE
- Facilite la création d'applications web
- Flexible, compatible, modulaire
- Grande communauté
- Continue d'innover et d'évoluer

## Spring Boot

- Auto-configuration
    - Configure l'application en fonction des dépendances ajoutés
    - Annotation @EnableAutoConfiguration
- Standalone 
    - pas besoin de serveur web
    - "just run" (package + run => java -jar my-application.jar)
- Opinionated (in a good way)
    - Choix pre-déterminés
    - Permet de démarrer rapidement
    - Spring initializr (permet de générer rapidement un projet)

## Spring Framework

- Modulaire (composant qui peuvent être assemblés)
- Six clés : Core, Web, AOP, Data Access, Integration, Testing

### Spring Core

- Injection de dépendances
    - Crée et maintient les objets et leurs dépendances
- i18n
- Validation
- Data binding
- Type conversion
- etc.

### Spring Web

- Gère les requêtes

#### Spring Web MVC

- Servlet : object qui recoit les requêtes et qui génère une réponse basé sur la requête
- Servlet API : bas niveau, complexe, code sur à maintenir
- Spring MVC : haut niveau, facile, plus productif, bonnes pratiques de code

#### Spring Webflux

- Reactive programming : moyen de programmation qui se concentre sur les flux de données et comment ils changent
- Asynchrone
- Ne bloque pas, meilleure utilisations des ressources

### Spring AOP

- AOP : aspect-oriented programming
- moyen de programmer qui augmente la modularité en permettant la séparation de l'application en plusieurs couches
- Evite la duplication
- Exemple : @PreAuthorize("hasRole('admin')"), exécute la méthode seulement si l'utilisateur est admin. Eviter de gérer les if

### Spring Data Access

- JDBC : verbeux, beaucoup de code
- Moins de codes
- exception translation (ex: code Oracle -> exception compréhensible)

### Spring Integration

- Intégration : Faire fonctionner différents systèmes/applications ensemble
- Exposer des opérations : web services (@RestController, @GetMapping, @PathVariable)
- RestTemplate pour appeller son webservice

### Spring Testing

- Support pour les tests unitaires grâce à l'injection de dépendances
- On teste le code, pas les dépendances qui sont mockés
- Support pour les tests d'intégrations
- Tests avec données
- Nettoyage après tests (reverse modifications)

## Spring Projects

### Spring Data

- Eténd Spring Data Access
- Supporte beaucoup de datastore

### Sprint Cloud

- Pour les systèmes distribuées, c'est à dire différentes applications assemblés ensemble par un réseau (ex: microservice)
- Microservice : petite application dédié à un seul but
- Service discovery : @EnableDiscoveryClient

### Spring Security

- Gère Autentification et autorisation
- Protège contre les attaques (cross site scripting, click jacking)

## Avantages de Spring

- Bien conçu
- Fiable, présent depuis longtemps
- Grosse communauté
- Populaire (dans le top des meilleurs frameworks)
- Demandé sur le marché
- Beaucoup de livres, documentations
- Supporté par beaucoup d'IDE
- En constante évolution
- Scalable : supporte la charge

## Inconvénients de Spring

- "Magique", pas toujours intuitif sur ce qu'il se passe derrière
- Compliqué de tout connaitre
- Augmente la taille des livrables
- Difficile à débuguer
- Consommateur en mémoire
- Complexité augmente avec le temps (c'est pourquoi Spring Boot est né)