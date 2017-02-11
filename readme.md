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