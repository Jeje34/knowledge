# Data lake

## Définition et principe 

- méthode de stockage des données utilisée par le big data
- dépôt de données brutes accessible en lecture seule
- les données sont gardées dans leurs formats originaux : la structure est alors créée au moment de l’analyse
- source de données de référence utilisée par les autres applications de traitement de données
- le principe est d'avoir dans un lieu des données de natures différentes, toutes les données de l’entreprise sont stockées : les données brutes côtoient les données transformées
- regroupe :
    - les données structurées en provenance de bases de données relationnelles
    - les données semi-structurées telles que les CSV, les logs, les XML, les JSON
    - les données non structurées telles que les emails, les documents et les PDF
    - on y trouve même des données binaires telles que des images, des fichiers audio ou des vidéos.
- ces données sont ensuite utilisées pour établir des rapports, pour visualiser les données, pour l’analyse de données ou pour le Machine Learning.
- Hadoop et Amazon Web Services S3 sont des plateformes utilisées pour les mettre en place
- Hadoop = framework Java open source qui prend en charge le traitement des données volumineuses
- Chaque donnée d'un lac se voit attribuer un identifiant unique et est marquée au moyen d'un jeu de balises de métadonnées

## Avantages

-  convient très bien aux données dont on décide de conserver l’historique sans forcément savoir par avance quelles analyses leur seront appliquées. 

## Inconvénients

- Sans capacité à catégoriser ou établir une hiérarchie entre les données, le désordre s’installe rapidement
ne permet pas aux entreprises de prioriser leurs données : le principal défi n’est pas de créer un Data Lake, mais de tirer profit des opportunités qu’il représente
- Si les Data Lakes sont physiquement très éloignés, il peut être très long de récupérer une donnée spécifique
- risque pour la confidentialité des données

## Data lake vs data warehouse

- Data Warehouse permet d’entreposer des données dans des fichiers ou des dossiers, un Data Lake repose sur une architecture de type flat
- Au sein d’une Data Warehouse, on trouve uniquement des données traitées et structurées.
- Data Warehouse est très cher pour les grands volumes de données, Data Lake comme Hadoop est conçu pour un stockage low-cost (Hadoop est open source donc licence et support communautaire gratuitset concu pour du hardware bon marché)
- Warehouse est moins agile, sa configuration est figée. Il est possible de modifier sa structure, mais cela nécessite du temps. Lake est très agile et peut être configuré ou reconfiguré à volonté. 
- Principaux utilisateurs du Data Lake sont des Data Scientists, tandis que la Data Warehouse est ouverte à tous les membres de l’entreprise.


## Sources

-- http://www.lebigdata.fr/data-lake-definition