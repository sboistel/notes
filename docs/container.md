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



# Créer un container

1. `podman build -t python36:1.0 .`
2. `podman create --name python36 <id>`
3. `podman start python36`

## Commandes podman
- `podman-build`: créer un container avec un fichier container
- `podman-run`: lancer une commande dans un nouveau container
- `podman-images`: lister les images locales
- `podman-ps`: afficher les infos d'un container
- `podman-inspect`: affiche la configuration d'un container
- `podman-pull`: télécharge une image
- `podman-cp`: copie des fichiers entre le local et le container
- `podman-exec`: executer une commande dans un container en service
- `podman-rm`: retirer un ou plusieurs containers
- `podman-rmi`: retirer une ou plusieurs images locales
- `podman-search`: cherche une image