# Trouvez ici quelques bonnes pratiques sur GIT et GITHUB #

**La commande GIT IGNORE**

Suivre (versionner) tous les fichiers d'un projet n'est pas forcément une bonne idée. 
Par exemple, quand vous créez une application avec une base de donnée, le contenu de cette dernière n'est pas indispensable à suivre sur git (et peut vous créer des conflits ensuite quand vous pushez sur github).

Vous pouvez demander à git d'ignorer certains fichiers en créant un fichier nommé `.gitignore` à la racine de votre repertoire (à côté du `.git` donc).
Ce fichier contiendra ce type d'information :

`# Ignorer tous les fichiers nommés text.txt`
`text.txt`
`# Ignorer tous les fichiers de type db`
`*.db`

à présent, quand vous ferez votre GIT STATUS, vous ne verrez plus les fichiers appelés par `.gitignore`
