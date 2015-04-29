# Installer RVM

RVM est un gestionnaire de version de Ruby. Il permet de passer rapidement d'une version à l'autre de Ruby sans désintaller et réinstaller Ruby.

**Avant d'installer RVM sur l'ordinateur, il faut vérifier qu'il n'y a pas déjà Ruby d'installé sur votre ordinateur !**


### Vérifier la présence de Ruby sur l'ordinateur

Dans le terminal, taper la commande

`ruby -v`

Si la console retourne `ruby X.X.XpXXXX (2015-02-26 revision 49769) [x86_64-linux]` où "X" un chiffre entre 1 et 9, alors Ruby est déjà installé sur votre ordinateur. Il faut donc le désinstaller avant de pouvoir installer RVM (si vous n'avez pas de ruby d'installé alors passez à la section installer RVM).

La console retourne `Le programme "Ruby" peut être trouvé dans les paquets suivants: ...`, aucune version de Ruby n'est donc présente sur l'ordinateur. Vous pouvez passer directement la section "Installer RVM"

### Désinstaller Ruby

Pour supprimer Ruby de l'ordinateur, entrer dans la console:

`sudo apt-get purge ruby`

### Installer RVM

Commencer par installer les dépendances de Ruby:

`sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev`


Installer la clé de sécurité nécéssaire au téléchargement de rvm via la ligne de commande :

`gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3`


Télécharger RVM, et installer Ruby:

`\curl -sSL https://get.rvm.io | bash -s stable --ruby`

	
Réactualiser les scripts du shell, pour que les modifictations soient prises en compte

`source ~/.rvm/scripts/rvm`


**Une fois toute ces étapes terminées, il faut relancer la console** : fermer puis en rouvrir une nouvelle


Vérifier que Ruby est bien trouvé par la console

`type rvm`

félicitation !! rvm est correctement installé sur l'ordinateur.


si la console retourne un chemin vers un dossier:

1. Clic droit sur la console
2. Profil > Préférences ou Préférences onglet Profil (terminator)
3. Onglet Commande
4. Cocher "Lancer la console en tant que shell de connexion" (Run command as login shell)


**Relancer une nouvelle fois la console**
