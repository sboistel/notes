# firewalld

## Zones

- block: refuse toutes les connexions entrantes
- dmz: seulements les connexions selectionnées sont acceptées
- drop: tout packet entrant est recupéré et aucune reponse envoyée
- external: utilisé sur les routeurs (NAT)
- home: pour les réseaux domestiques
- internal: pareil que home
- public: les autres ordinateurs du réseau ne sont pas acceptés.
- trusted: toutes les connexions sont acceptes
- work: comme home et internal mais au travail

## Commande

`firewall-cmd`