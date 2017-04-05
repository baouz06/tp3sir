# TP 3 de Systèmes d'informations répartis					
											
## Objectifs du TP	

1. Comprendre les bénéfices et les limites des bases nosql
2. Comprendre les différents types de bases nosql
3. Réaliser une application en utilisant une API comme Morphia proche de JPA en se plaçant dans un cadre classique de développement au dessus d’une base orientée document comme Mongo.
4. Comparer avec une base de données clé valeur haute performance comme Redis
							
							
## Sujet
Création d’une application simple qui utilise une base de données MongoDB

## Installation de la base de données MongoDB

Une fois que nous avons décompresser le fichier de mongo-db qui se trouve sur le share de l'istic, on crée une repertoire comme au-dessous

c:\mongodb\data
c:\mongodb\data\db

Après qu'on a precisé le chemin \data\db avec dbpath paramètres,nous utilisons deux terminales pour lancer mongo.exe et mongod.exe pour la connexion de la base de donnée.

## Utilisation de morphia pour la connexion à la base de données

### Le modèle métier de projet

![model2](https://cloud.githubusercontent.com/assets/15005875/24712328/d87d8b80-1a22-11e7-9e3a-654f5166ef4e.png)

#### La classe Person.java

La classe Person.java contient 3 variables du type String pour les informations personnelles avec son numéro id identique et 3 variables du type Collection puisque chaque person reste dans une ou plusieurs résidences et qu'il a une ou plusieurs amis et des équipements électroniques personnelles.


							partie1: MongoDB

1)Quelles sont les limites d’une base données orientées document ?
MongoDB,est une bases de donnée NoSQl utilisée généralement pour traiter les gros volumes de données.
Elle a des limites qui sont les suivantes:

	*la disparition des jointures.
	**L'intégrité des données n'est plus garantie.
	***les requêtes qu'on peut effectuer sur cette base sont moins riches qu'en SQL classique ce qui limite les requêtes complexes par rapport à un SGBDR. 
	
							partie2: Redis
1)Quelles sont les types de données stockés dans Redis, que peut on faire comme types de requêtes ?

	Redis est une base de données open source de type clefs-valeurs. Il permet de manipuler des types de données simples : chaînes de caractères, tableaux associatifs, listes, ensembles et ensembles ordonnés.
	
	 On peut faire des requêtes en lecture/ écriture avec des temps de réponse très rapide car une des principales caractéristiques de Redis est de conserver l'intégralité des données en RAM . Il est possible d'insérer, mettre à jour des clés-valeur mais aussi de les filtrer et de donner une durée de vie à une clé.							
