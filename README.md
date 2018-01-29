# NOTES BASES RAILS
Dans ce README nous allons voir les principes de base pour ruby on RAILS.
</br>
</br>

## Sommaire
</br>

* [Sites Statiques / Sites Dynamiques](#stat_dyn)
* [MVC](#mvc)
* [Les routes](#routes)
* [Les Bases de Données](#bases_de_données)
* [GET / POST](#get_post)
* [Le concept de migration](#migrations)
* [Les relations entre les models des BDD](#relations_models_bdd)
* [Les fonctions du CRUD](#crud)
</br>

## <a name="stat_dyn">Sites Statiques / Sites Dynamiques</a>

Un site statique, est composé de pages dites statiques, visibles telles qu’elles ont été conçues. Cela ne signifie pas qu’elles sont sans mouvement ou sans animation. La ou les pages accessibles ne seront donc pas différentes en fonction de l'utilisateur qui les consultes ou différentes pour un même utilisateur en fonction d'une visite à l'autre.

Au contraire, dans un site dynamique les informations seront présentées de façon différente selon l’interaction avec le visiteur. En effet si les informations affichées seront différentes d'un utilisateur à l'autre. En fonction de la personne qui est connectée, les serveurs vont faire tourner le code et renvoyer des pages HTML/CSS différentes. Ce sont donc des sites sur lesquels il faut se connecter avec un identifiant personnel. Ce sont des sites qui ont des bases de donnée utilisateur (c'est là qu Rails va être intéressant).
</br>
</br>




## <a name="mvc">MVC (Model View Controller)</a>

![Image Archi](/image/schema_MVC.png) </br>
</br>
Le Router vérifie une première fois quelle est la route et si elle est bonne.

Le **MVC** est un système de communication entre la "**View**", le "**Controller**" et le "**Model**".

Le Router vérifie une première fois quelle est la route et si elle est bonne.

La **View** est l'interface Homme/Machine, en l'occurrence ici, la page Web, donc le code HTML, CSS... Mais c'est également l'interface graphique d'une application ou d'un jeu.

Le **Controller** gères (contrôle) les données et les transmet entre la *View* et le *Model* lorsque l'utilisateur effectue une action. Il est aussi là pour informer l'utilisateur qu'un fichier ou une page a bien été chargé et qu'il peut faire une nouvelle action, comme cliquer sur un bouton ou autre.
Il vérifie que la commande envoyé par l'utilisateur est valide (notamment la route).

Le **Model**, reçoit les requête du *Controller* et va chercher la correspondance dans la base de donnée et la renvoie au *Controller*.
</br>
</br>


### Analogie restaurant

Pour faire une analogie avec un restaurant, le "*Routeur*" est le serveur, il vérifie une première fois que le client a choisit un plat qui est sur le menu.
Le "*Controller*" est le cuisinier que reçoit la commande, il revérifie que la recette est bien dans le menu.
Si c'est le cas, il va chercher dans son livre qui est en réalité le "*Model*" la recette correspondant au plat B18 dans le menu et la récupère.
Enfin il exécute le plat qui correspond au "*View*", pour le renvoyer vers le client.
</br>
</br>


## <a name="routes">Les Routes</a>

Les routes c'est exactement comme son nom l'indique, le chemin qui mène jusqu'à l'action que l'on veut exécuter.
C'est dans un URL, le fait qu'on va lui demander, dans le site de Facebook, c'est ce qui va dire que l'on va dans la rubrique de "Groupe", puis le nom du groupe...

Dans une application, ce serait demander d'ouvrir le dossier compte de tel utilisateur pour aller chercher dans ses dossier l'album "Summer" dans lequel il choisira d'afficher la photo 53.
</br>
</br>


## <a name="bases_de_données">Les Bases de Données</a>

C'est comme un énorme tableau "Excel" dans lequel il y a des plusieurs tables.
La première colonne est "l'id" qui va permettre par exemple d'identifier un utilisateur, ou dans l'exemple de Félix, un article. La deuxième est généralement le nom ou le titre et les colonnes qui suivent les données qu'ils contiennent.
</br>
</br>


### Analogie Restaurant

Pour reprendre notre analogie sur le restaurant, la base de donnée c'est le livre de recette.
On a tout d'abord le numéro de la recette qui correspond à celui qui est reporté sur le menu.
En deuxième colonne on a son nom, puis on pourrait avoir une colonne chaud/froid, une colonne ustensiles à utiliser, temps de préparation et un ingrédients.
</br>
</br>


## <a name="get_post">GET/POST</a>

**GET** et **POST** sont deux fonctions de requête-réponse entre le client et le server dans le protocole *HTTP*.

**GET**: permet de lire des données contenu dans la base de données.
**POST**: permet permet d'y écrire des donnée à la demande de l'utilisateur.

*HTTP*(Hypertext Transfer Protocol) à été crée pour permettre la communication entre un client et le serveur. Un navigateur peut être le client et une application sur un ordinateur qui héberge un site web, le server.
</br>
</br>


## <a name="migrations">Les Migrations</a>

Une migration va permettre de définir les mutations, les modification à faire au niveau de la base de données.
Ce qui est intéressant c'est qu'en travaillant à plusieurs, ça permet de n'avoir à récupérer que les migration pour que le projet se mette à jour, plutôt que d'avoir à modifier la base de donnée directement dans le "dur".
Les migrations permettent d'apporter des modifications structurées dans la base de données sans avoir à toucher à SQL.

Elles doivent être placées dans le dossier DB.
Lorsque l'on les cré, dans leur nom il y a l'heure à laquelle on effectué cette migration.
Encore une fois si on travaille à plusieurs et qu'un autre développeur effectue une migration, on saura alors dans quel ordre il faut les exécuter.
</br>
</br>


## <a name="relations_models_bdd">Les relations entre Models et BDD</a>

Un model a pour but, comme nous l'avons vu, de communiquer avec la **BDD**(Base De Données), il est nécessaire de structurer les **Models** pour bien définir les interactions avec la BDD.

Il est possible créer une relation, un lien entre deux tables de **BDD**, qui associe leurs données entre elles.
Des informations de type différents d'un même utilisateur peuvent par exemple être contenues dans 2 tables différents d'une même **BDD**.
Ou encore il est possible d'en lier un à plusieurs autres.
Ou plusieurs ensemble.


Les **Models** sont des classes de Ruby. Mais encore faut-il les associer. 
</br>
</br>


## <a name="crud">Les fonctions du CRUD</a>

**CRUD**: Create, Read, Update, Delete
Pour ces 4 actions principales, ont a créé 4 fonctions "principales" qui vont couvrir l'ensemble des besoins du **CRUD**.

Aujourd’hui, il y a différentes actions possibles, mais les 4 fonctions les plus utilisées sont les suivantes :
* **GET** : qui fait comme un "return" de la ressource suivant le path demandé. elle va la chercher et en fait ce que tu lui demandes de faire
* **POST** : crée une nouvelle ressource
* **PUT** : met à jour une ressource existante
* **DELETE** : supprimer une ressource existante

Par ressource, on entendra dans notre cas par exemple la base de données qui est derrière le "*Model*".
