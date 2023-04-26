# Installer un container

1. `dnf install container-tools`
2. `mkdir -p /home/user/.config/containers`
3. `vim /home/user/.config/containers/registries.conf`:
```
unqualified-search-registries = ['registry.lab.example.com']

[[registry]]
location = "registry.lab.example.com"
insecure = true
blocked = false
```
4. `podman login registry`
5. `podman info`: permet de vérifier les registres de recherche
6. `podman search python-38`
7. `podman pull registry.access.redhat.com/ubi8/python-38`
8. `podman images`

## Commandes podman
- `podman-build`: créer un container avec un fichier container
- `podman-run -d --name name cmd`: lancer une commande dans un nouveau container détaché
- `podman-images`: lister les images locales
- `podman-ps`: afficher les infos d'un container
- `podman-inspect`: affiche la configuration d'un container
- `podman-pull`: télécharge une image
- `podman-cp`: copie des fichiers entre le local et le container
- `podman-exec`: executer une commande dans un container en service
- `podman-rm`: retirer un ou plusieurs containers
- `podman-rmi`: retirer une ou plusieurs images locales
- `podman-search`: cherche une image

`skopeo inspect image` permet de donner des informatiions sur une image, et notamment "usage" qui donne un example de commandes

## Variables d'environnement

On peut spécifier des variables d'environnement qui peuvent être nécessaires à l'exécution du container

## Analyse de logs

`podman container logs db01`

## Stockage persistant

Option -v 

`-v /home/user/db_data:/var/lib/mysql:Z`: gérer le stockage permanent + :Z pour ajouter le contexte selinux

## Port mapping

Option -p

`-p 13306:3306`
`podman port -a`

## Réseau

`podman network create`

## Systemd

create /home/"user"/.config/systemd/user

`podman generate systemd --name --new`
`systemctl --user start service`
`loginctl enable-linger`: pour démarrer le service au démarrage