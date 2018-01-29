# Ce que vous n'avez jamais osé demander sur... __le MVC__ !

## Commençons par le commencement : le site dynamique

Contrairement à un site statique qui s'affiche exactement comme il est hébergé, le contenu d'un site dynamique change en fonction des utilisateurs et de leurs actions. 

Prenons pour exemple deux sites extrêmement populaires ;)

Site | Comportement du serveur | Page affichée | Dynamique ?
--- | --- | --- | ---
[Motherfuckingwebsite](http://motherfuckingwebsite.com/) | Le serveur envoie une page statique | La page affichée ne change pas d'un utilisateur à un autre | Non...
[Une page Facebook](https://www.facebook.com/) |  Le serveur utilise les informations liées à l'utilisateur pour __générer__ une page HTML | La page affichée est dynamique : son contenu est lié à la requête de l'utilisateur | Oui !

> Dans le cas d'un site dynamique, l'utilisateur induit le contenu de la page. Soit de façon consciente (en remplissant un formulaire par exemple), soit inconsciente.

Un site dynamique fonctionne grâce à un langage serveur, qui stocke et réutilise les informations des utilisateurs sur des bases de données.

__Mais comment un site dynamique est-il généré ?__

## Le MVC, qu'est-ce-que c'est ?

MVC signifie Model View Controller. C'est une forme d'architecture qui permet de générer du contenu dynamique, à partir de requêtes utilisateurs. C'est un modèle très populaire, en particulier pour les applications Web. 

Vous l'aurez compris, le MVC est composé de trois briques :

* Model : c'est la brique en relation avec les bases de données. Elle va récupérer l'information pertinente à afficher
* View : c'est la brique qui crée l'interface visuele, en fonction des informations tirées de la base de données
* Controller : c'est la brique qui fait le lien ! Elle donne des ordres à la brique Models sur l'information à récupérer, et s'assure que ces informations sont utilisées par la brique View pour générer le contenu dynamique


## On the road again : les routes !

![Road](https://github.com/justinekro/read-me/blob/master/road.jpg)

Les routes indiquent où le visiteur se trouve dans l'architecture d'un site. 
On peut les identifier dans les URLs. 

Ce sont ces routes qui donneront au Controller des indices sur les actions à effectuer, et sur les informations à aller chercher dans le Model.

## Les Bases de Données

Le Model est lié aux bases de données.

Une base de données permet de stocker les informations en les organisant. Le MVC, et particulièrement la brique Model, est dépendante des Bases de Données pour pouvoir sélectionner les informations et donc rendre le site dynamique !

> Dans les cas d'un blog, nous allons pouvoir stocker dans une base de données
> * des articles : avec leur titre, contenu, date de création 
> * des commentaires : avec leur concepteur, leur contenu, et l'article associé
> * des utilisateurs...

### Et maintenant, une petite mise en application du MVC !

Imaginez que vous êtes sur la page d'accueil d'un blog, et que vous avez accès à plusieurs articles.

En cliquant sur le lien de redirection vers un article, vous changez de référentiel (en fait, de Controller !). Chaque action qui peut être effectuée sur l'article (par exemple : l'afficher, le modifier...) est gérée par le __Controller__. 

Si vous souhaitez afficher l'article, le __Controller__ va indiquer au __Model__ qu'il a besoin des informations concernant le contenu de l'article. Par exemple, il doit récupérer dans des bases de données son titre et son contenu... pour pouvoir l'afficher ! C'est là que le __View__ rentre en action, pour adapter le contenu de la page à ce que désire l'utilisateur.


## La différence entre GET et POST

GET et POST sont des méthodes.
* Get : cette méthode va chercher une information dans la Base de Données pour l'afficher à l'utilisateur. 
..* Exemple : l'utilisateur du blog veut afficher l'article de son choix
* Post : Dans le cas d'un Post, il y a une création de nouvelles données dans la Base de Données. 
..* Exemple : L'utilisateur du blog écrit un nouvel article : celui-ci doit être enregistré dans la Base de Données


## Le concept de migration

La migration permet de __créer__ ou __modifier__ les champs d'une Base de Données.

### Exemple dans Rails

```ruby
class CreateArticles < ActiveRecord::Migration[5.0]
  def change
    create_table :articles do |t|
      t.string :title
      t.text :text
 
      t.timestamps
    end
  end
end
```

Cette methode crée une table Articles avec une colonne "title" et une colonne "text" ainsi qu'une colonne indiquant le moment de création, lorsque "db:migrate" est exécutée sur le terminal.


## Comment sont liés les models des BDD ?

Les différents Models sont liés entre eux par des clés.

Si l'on reprend l'exemple du blog, chaque article peut avoir plusieurs commentaires. Ce qui signifie que les articles et les commentaires sont liés entre eux.

Comment ? Grâce à des fonctions !

### Exemple dans Rails

```ruby
class Comment
	belongs_to :article
end

```
Cette fonction indique que les commentaires appartiennent à un article... et un seul !

```ruby
class Article
	has_many :comments
end
```
Cette fonction indique qu'un article peut avoir plusieurs commentaires.

## Le CRUD

Le CRUD est un ensemble d'actions qui peuvent être appliqués à une Base de Données.

### Create
Elle permet de créer un élément de la BDD. (Elle est associée une méthode Post)

### Read
Elle permet de lire un élément de la BDD. (Elle est associée à une méthode Get)

### Update
Elle permet de mettre à jour un élément de la BDD.

### Delete
Elle permet de supprimer un élément de la BDD

## Vous voulez aller plus loin ?

Pour comprendre le MVC, quoi de mieux que de le mettre en application ? Vous pouvez consulter cette vidéo pour en savoir plus
<a href="https://www.youtube.com/watch?v=deNytSPvAxA&feature=youtu.be
" target="_blank"><img src="https://www.youtube.com/watch?v=deNytSPvAxA&feature=youtu.be/0.jpg" 
alt="Vidéo d'intro à Rails" width="240" height="180" border="10" /></a>
