# Azure Services

Le cloud est basé sur un principe de partage de responsabilités

Il existe 3 types de services:

- SaaS: Software as a Service
- PaaS: Platform as a Service
- IaaS: Infrastructure as a Service

Le SaaS est celui où le client a le moins de responsabilité; le IaaS où il en a le plus

4 types de cloud: 

- Private: cloud utilisé par une seule entité
- Public: cloud provider utilisable par tout le monde
- Hybrid
- multi-cloud

Les services peuvent être managés en GUI ou CLI

# CLI

Installable sous Windows, Linux ou MacOS, ou directement sur Azure Cloud Shell. Possibilité d'utiliser Azure Az Powershell.

az command:
- az vm create

# Azure ARM template  

Fichier texte en JSON pour déployer des ressources sur le cloud (infra as code)

# Managements groups

Permet d'organiser les subscriptions pour facilier l'application de polices Azure par exemple

# Policy and lock

Les policy peuvent etre appliquées à un management group, a un resource group, à une subscriptions. Pareil pour les locks, mais ils prennent le dessus. Il y en a deux: read-only et delete

# Storage account

Contient:
- blobs: fichier classique
- file shares: dossier partagé avec SMB
- queues: 
- tables: nosql

Principe de versioning, soft delete.

Accès fréquent et rapide (hot), moins fréquent (cool) et archive. Peut etre défini de maniére globale ou pour un blob

Pour accéder à un storage account, on peut se connecter, mais surtout utiliser l'une des deux clés pour avoir accès aux données dans le compte, ou un SAS qui donne accès à une partie des ressources sélectionnées.

# Mots-clés

- Azure AD: active directory
- Private: cloud utilisé par une seule entité
- Public: cloud provider utilisable par tout le monde
- Hybrid
- multi-cloud
- SaaS: Software as a Service
- PaaS: Platform as a Service
- IaaS: Infrastructure as a Service
- Azure Arc
- Azre CLI
- Azure Az Powershell module
- Azure ARM
- Subscriptions: abonnement Azure(1 subscriptions par AD mais un AD peut avoir plusieurs subscriptions)