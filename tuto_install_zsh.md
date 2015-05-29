##Installer oh-my-zsh sur Ubuntu

- Programme pour mettre de la couleur dans le Terminal et différents plugins

#### Prérequis : 

```sudo apt-get install zsh```


```sudo apt-get install git-core```
	

####Installer oh-my-zsh

```wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh```

###Changer le shell vers zsh

```chsh -s `which zsh` ```

####Redémarrer

```sudo shutdown -r 0```

##Installer zsh sur Linux Mint

```sudo apt-get update```
```sudo apt-get install git-core zsh```

####Verifiez l'install :

`zsh`

- Puis `ps`

- (Si vous avez un long message tapez 0 pour créer le .zshrc, sinon `exit` pour sortir)

####Changer le shell par défaut

`chsh -s /bin/zsh`

###Installer oh-my zsh

`wget --no-check-certificate http://install.ohmyz.sh -O - | sh`


##Installer le plugin syntax-highlighting 

`cd ~/.oh-my-zsh/custom/plugins`

`git clone git://github.com/zsh-users/zsh-syntax-highlighting.git`

####Activer le plugin dans ~/.zshrc (en dernière position)

`plugins=(zsh-syntax-highlighting)`

####Recharger ~/.zshrc

`source ~/.zshrc`

###Pour Linux Mint

- Même procédure puis:

####Editer le .zshrc:

- Remplacer `export PATH="/home/nom/rvm...` par `export PATH="$PATH:$HOME/rvm....`

- Et voilà, si tout c'est bien passé, vous avez des couleurs dans votre `Terminal`

####Faire marcher RVM sous Arch/Manjaro
Après avoir installé ZSH, lorsque vous lancez `ruby -v`, un message d'erreur peut s'afficher `RVM is not a function`.

Dans ce cas ajoutez, à votre `~/zshrc`

`source $HOME/.rvm/scripts/rvm`
