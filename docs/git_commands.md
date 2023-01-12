# Git

## Commandes Git

- `git init name`: initialiser git
- `git clone url`: télécharge un projet
- `git status`: liste l'état de git et des nouveux fichiers'
- `git diff`: montre les modifs de fichier entre le unstage et le stage area
- `git add`: ajoute à git
- `git commit -am ""`: commiter 
- `git branch`: liste les branches locales
- `git branch nom`: créer une branche
- `git checkout nom`: change de branche
- `git checkout -b nom`: crée une branche et switch dessus
- `git merge nom`: fusionne la branche avec celle actuelle
- `git branch -d`: supprime la branche
- `git rm`: supprime le fichier
- `git mv`: renomme le fichier
- `git log`: montre l'historique des commits
- `git reset commit`: annule les commits après commit
- `git fetch`: recupere l'historique du dépot
- `git push`: envoie les commits
- `git config --global user.name "username"`
- `git config --global user.email "email"`
- `git config --global --list`: voir les infos
- `git clone 'url'`
- `git rebase`: permet de mettre à jour une branche par rapport à une autre
- `git stash`: permet de sauvegarder un projet sans le commiter et retravailler dessus quand on veut
- `git tag -a`: annoter un commit avec un tag (Ex: V1.1)

## Installer git

<https://git-scm.com>

## Configurer Git

### New project

1. `git init new project`
2. `git add file`

### Existing project

1. `git init`
2. `git add .`

### Join existing project

1. `git clone 'url'`

## Recupérer un repo

`git pull origin master`

## Déposer sur un repo

`git push origin master`

## Annuler l'ajout d'un fichier

`git reset HEAD file`

## Annuler les modifications d'un fichier

`git checkout -- file`

## Créer un alias

`git config --global alias.name "command`

## Ignorer des fichiers

Créer un fichier .gitignore et écrire le nom des fichiers à ignorer

## Merging

Il faut être sur la branche vers laquelle on veut fusionner. Préciser --no-ff pour éviter le fast forward (merge qui merge tous les commits de la branche).

## Stash vers une nouvelle branche

`git stash branch name`

Permet de prendre les modifications dans une branche et de les envoyer vers une autre.

## Git tag

Permet de donner un tag à des commits en particulier