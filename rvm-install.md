# Installer RVM #


**Avant d'installer RVM sur l'ordinateur, il faut vérifier qu'il n'y a pas déjà Ruby d'installer sur l'ordinateur!**



### Vérifier la présence de Ruby sur l'ordinateur ###


Taper la commande:

`ruby -v`

La console retourne `Le programme "Ruby" peut etre trouvé dans les paquets suivants: ...`, aucune version de Ruby n'est donc présente sur l'ordinateur. Vous pouvez donc directement passer à l'installation de RVM.


La console retourne `ruby X.X.XpXXXX (2015-02-26 revision 49769) [x86_64-linux]`, Ruby est déjà installé sur votre ordinateur. Il faut le désinstaller avant de pouvoir installer RVM (voir partie Désinstaller Ruby).



### Désinstaller Ruby ###


Pour supprimer Ruby de l'ordinateur, entrer dans la console:

`sudo apt-get purge ruby`



### Installer RVM ###


Commencer par installer les dépendances de Ruby:

`sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev`


Installer la clé de sécurité:

`gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3`


Télécharger RVM, et installer Ruby:

`\curl -sSL https://get.rvm.io | bash -s stable --ruby`


Reactualiser les scripts du shell:

`source ~/.rvm/scripts/rvm`


**Une fois toute ces étapes terminées il faut relancer la console et la fermant et en ouvrant une nouvelle**


Vérifier que Ruby est bien trouvé par la console: 

`type rvm | head -1`


si la console retourne `rvm is a function` félicitation, rvm est correctement installé sur l'ordinateur.


si la console retourne un chemin vers un dossier:

1. Faire clic droit sur la console

2. Profil > Préférences ou Préférences onglet Profil (terminator)

3. Onglet Commande

4. Cocher "Lancer la console en tant que shell de connexion" (Run command as login shell)


**Relancer une nouvelle fois la console**