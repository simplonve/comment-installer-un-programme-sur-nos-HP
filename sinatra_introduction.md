## Débuter avec Sinatra

Comment créer un petit site internet léger pour afficher vos page html.

### Prérequis
Vérifier que vous avez bien RVM et ruby s'installé sur votre OS.

Dans le terminal

```
rvm -v
ruby -v
```
Sinon référez-vous aux tutoriels 'Installer RVM' (https://github.com/simplonve/comment-installer-un-programme-sur-nos-HP)

### Installer Sinatra
Installer une librairie (appelé gem en ruby)

```
sudo gem install sinatra
```

Sinatra est désormais installé sur votre OS. 
Ruby va pouvoir appeler votre librairie sinatra

### Installer shotgun
Shotgun est un autre librarie ruby qui permet de ne pas relancer son serveur local à chaque fois qu'on enregistre son fichier dans son éditeur de texte (insérer lien Github sur shotgun)

Dans le terminal:

```
sudo gem install shotgun
```

### Créer son fichier ruby 
Créer un fichier dans votre éditeur de texte appelé

```
simple.rb
```

Enregistrer le fichier vide dans l'éditeur de texte.

### Lancer le serveur

Vous pouvez désormais lancer votre permier serveur local sinatra !

```
shotgun simple.rb
```

#### Pourquoi utiliser shotgun plutot que sinatra ?

` sinatra simple.rb ` pourrait faire la même opération que shotgun (lancer un serveur local)

Mais ensuite à chaque changement sur vos fichiers (HTML CSS ou ruby) vous devrez 'tuer' le serveur (avec `Ctrl` + ` c `) et recommencer... donc utilisez shotgun 

(note pour plus tard, Rails inclus un programme 'comme shotgun' qui se relance tout seul)

### Apprécier le résultat

Votre site est accessible sur votre navigateur (en local)

A cette adresse : 

```
http://localhost:9393
```

### En route pour afficher votre page HTML

Avant d'afficher votre HTML cherement acquis ces dernières semaines, il faut passer par quelques 'petites' étapes.

#### Les types de requete HTTP
Comme Sinatra est un serveur, il répond aux demandes que fait votre navigateur (le client). 
Globalement ces demandes sont des **requetes** envoyés par votre navigateur au serveur web (sinatra dans ce tutoriel). 

Les requetes HTTP sont au nombre de 4 :
 - GET
 - POST
 - PUT
 - DELETE

(Insérer une ressource sur les requetes HTTP)

#### Donc en ruby

Dans l'éditeur de texte, insérer dans vote fichier vide :

**simple.rb**
```
require 'rubygems'
require 'sinatra'

get '/' do
  'Hello world'
end
```

Actualiser votre navigateur, à l'adresse 
```
http://localhost:9393/
```

Ca s'affiche !
Car quand le serveur Sinatra reçoit une requete `get` sur l'adresse root ou '/' (le dernier caratère de l'URL ci-dessus). 
Alors il répond, matérialisé dans le code ci-dessus par `do` et `end` 
il excute ensuite le code ruby 'Hello World' qui affiche juste cette string.

### Interpretation de sinatra pour afficher du HTML

Au lieu d'appeler son fichier index.html habituel, sinatra à besoin d'appeler une extension de language d'interpretation appelé erb.

Vous pouvez donc prendre n'importe quel fichier HTML existant, et le renommer avec erb à la fin

Par exemple :
index.html => à renommer => **index.html.erb**
index.html => à renommer => index.erb (fonctionne pareil)

(insérer lien sur une ressource/doc erb)

### Son fichier HTML interprété par Sinatra

#### Afficher son fichier .erb

**simple.rb**
```
require 'rubygems'
require 'sinatra'

get '/' do
  erb :index
end
```

Attention sans écrire le .erb à la fin de la ligne, juste le nom du fichier

### Faire un formulaire 

**simple.rb**
```
get '/' do
  erb :form
end
```

**form.erb**
```
<html>
    <head>
    </head>
    <body>
        <form action="/" method="post">
          <p>First name: <input type="text" name="post[first_name]" size="20"/></p>
          <p>Last name: <input type="text" name="post[last_name]" size="20"/></p>
          <input type="submit" value="Say hi!">
        </form>
    </body>
</html>
```


### Accepter la requete POST

Ajouter à la suite :
**simple.rb**
```
post '/' do
  @name = "#{params[:post][:first_name]} #{params[:post][:last_name]}"
  @title = "Hello #{@name}"
  erb :hello
end
```


Référence : vidéo de Peepcode sur Sinatra
