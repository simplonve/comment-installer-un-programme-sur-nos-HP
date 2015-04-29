# Installer Rails

**IMPORTANT** Pour installer Rails sur l'ordinateur, vous devez d'abord avoir installer RVM sur l'ordinateur! Si ce n'est pas fait, allez voir rvm-install.md

### Installer RubyOnRails et ses dépendances grâce aux Gems Ruby

Dans le terminal :

`gem install rails`


Ensuite, installer la librairie dont rails a besoin pour tourner sur Linux
Pour Ubuntu/Debian :

`sudo apt-get install libpq-dev`

Facultatif

Installer le programme de base de données Postgres grâce aux Gems Ruby

`gem install pg -v '0.18.1'`
