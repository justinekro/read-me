![Le saviez-vous?](https://github.com/justinekro/read-me/idea.png "Light bulb")

# Ce que vous n'avez jamais osé demander sur... __le MVC__ !

## Commençons par le commencement : le site statique vs le site dynamique

Contrairement à un site statique qui s'affiche exactement comme il est hébergé, le contenu d'un site dynamique change en fonction des visiteurs et de leurs requêtes.

Prenons pour exemple deux sites extrêmement populaires.
[Motherfuckingwebsite](http://motherfuckingwebsite.com/) vs... une page facebook [Une page Facebook](https://www.facebook.com/)!

Dans le cas de Motherfuckingwebsite.



## Vous avez dit MVC ?

Model : en relation avec les bases de données
View : détient toutes les méthodes de chaque 
Controller

## On the road again : les routes !

Les routes indiquent où le visiteur se trouve dans l'architecture d'un site.
où tu te trouves dans l'architecture du site. 
URL

## Les Bases de Données

stocker informations
organiser les informations


## La différence entre GET et POST

get = l'utilisateur veut récupérer un article dans la BDD
post = push > l'utilisateur écrit qqchose qui va rentrer dans la BDD (crée un nouvel article ou écrit un commentaire)

## Le concept de migration

Initialisation
commande migrate : quand tu crées tes tables et tes commandes

première migration  =créer une base de données 
ensuite, faire une base de données 

## Les relations entre les models des BDD

Si l'on reprend l'exemple du blog, chaque article peut avoir plusieurs commentaires. Ce qui signifie que les articles et les commentaires sont liés entre eux.

Comment ? Grâce à des fonctions !

```ruby
belongs_to
```
Cette fonction indique que les commentaires appartiennent à un article... et un seul !

```ruby
has_many
```
Cette fonction indique qu'un article peut avoir plusieurs commentaires.

## Les fonctions du CRUD

### Create
### Read
### Update
### Delete

