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

La classe Person.java contient 3 variables, de type ObjectId avec une id identique pour chaque personne,une variable de type String pour le nom de la personne et une variable de type  Collection pour l'adresse de la personne.

```
	@Id
	private ObjectId id;
	private  String name;
	@Embedded
	private Collection<Address> addresses;
```

Nous faisons l'implementation des fonctions getter et setter.
```
public ObjectId getId() {
		return id;
	}
	public void setId(ObjectId id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public Collection<Address> getAddresses() {
		return addresses;
	}
	public void setAddresses(Collection<Address> addresses) {
		this.addresses = addresses;
	}
```
#### La classe Article.java

La classe Article.java contient 3 variables, de type ObjectId avec une id identique pour chaque article,une variable de type String pour le nom de l'article et une variable de type  Collection pour le propriétaire de l'article

```							
	private int stars;
	@Id
	private ObjectId id;
	private  String name;
	@Embedded
	private Collection<Person> personnes;						
```							
Nous faisons l'implementation des fonctions getter et setter.				
```
	public int getStars() {
		return stars;
	}
	public void setStars(int stars) {
		this.stars = stars;
	}
	public ObjectId getId() {
		return id;
	}
	public void setId(ObjectId id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
```							
#### La classe Address.java

La classe Adress.java contient 1 variable de type ObjectId avec une id identique pour chaque adresse,4 variables de type String pour le nom de la rue,de la ville,du code postale et du pays.
```
	@Id
private ObjectId id;	
private String street;
private String city;
private String postCode;
private String country;
```							
Nous faisons l'implementation des fonctions getter et setter.							
```						
public String getStreet() {
	return street;
}
public void setStreet(String street) {
	this.street = street;
}
public String getCity() {
	return city;
}
public void setCity(String city) {
	this.city = city;
}
public String getPostCode() {
	return postCode;
}
public void setPostCode(String postCode) {
	this.postCode = postCode;
}
public String getCountry() {
	return country;
}
public void setCountry(String country) {
	this.country = country;
}						
```						
#### La classe Snippet.java	
Pour la manipulation des données de la base nous utilisons la librarie Morphia et ça nous permet de faciliter notre travail au niveau de sécurité des données avec une interface de développement d'applications de requêtes courantes.

Pour ce tp on utilise la base de donnée qui s'appelle "my_database".
```
 Morphia morphia = new Morphia();    
 MongoClient mongo = new MongoClient();
 morphia.map(Person.class).map(Address.class);
 Datastore ds = morphia.createDatastore(mongo, "my_database");
```
##### Les chargement des données sur la base

En utilisant les fonctions de setter que nous avons défini sur les fichiers de Person.java on crée un personne et le nomme et on met les autres informations et on le garde avec la fonctions "save" sur la base de données.

```
Person p = new Person();
p.setName("Tintin");	
Address address = new Address();
address.setStreet("123 Some street");
address.setCity("Some city");
address.setPostCode("123 456");
address.setCountry("Some country");	   
ArrayList addresses = new ArrayList();
üaddresses.add(address);
p.setAddresses(addresses);
ds.save(p);
```
						
						
						
## Question 1
Quelles sont les limites d’une base données orientées document ?

### Réponse 1
MongoDB,est une bases de donnée NoSQl utilisée généralement pour traiter les gros volumes de données.
Elle a des limites qui sont les suivantes:

1. La disparition des jointures.
2. L'intégrité des données n'est plus garantie.
3. Les requêtes qu'on peut effectuer sur cette base sont moins riches qu'en SQL classique ce qui limite les requêtes complexes par rapport à un SGBDR. 

## Question 2
Quelles sont les types de données stockés dans Redis, que peut on faire comme types de requêtes ?
### Réponse 2

	
Redis est une base de données open source de type clefs-valeurs. Il permet de manipuler des types de données simples : chaînes de caractères, tableaux associatifs, listes, ensembles et ensembles ordonnés.
	
On peut faire des requêtes en lecture/ écriture avec des temps de réponse très rapide car une des principales caractéristiques de Redis est de conserver l'intégralité des données en RAM . Il est possible d'insérer, mettre à jour des clés-valeur mais aussi de les filtrer et de donner une durée de vie à une clé.							
