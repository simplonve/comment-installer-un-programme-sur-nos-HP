# Trouvez ici quelques bonnes pratiques sur GIT et GITHUB #

## Le fichier .gitignore

Suivre (versionner) tous les fichiers d'un projet n'est pas forcément une bonne idée. 
Par exemple, quand vous créez une application avec une base de donnée, le contenu de cette dernière n'est pas indispensable à suivre sur git (et vous ne souhaitez pas donner accès aux données de votre application en ligne).

Pour demander à git d'ignorer certains fichiers de version, un fichier nommé `.gitignore` à la racine de votre repertoire (à côté du dossier `.git`).

Ce fichier contiendra ce type d'information :

`# Ignorer tous les fichiers nommés text.txt`
`*text.txt`
`# Ignorer tous les fichiers de type .db`
`*.db`

Taper ensuite `git status` ; vous ne verrez plus les fichiers inscrit dans le par `.gitignore`
