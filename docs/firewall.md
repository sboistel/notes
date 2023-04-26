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

- --get-default-zone	Query the current default zone.
- --set-default-zone=ZONE	Set the default zone. This changes both the runtime and the permanent configuration.
- --get-zones	List all available zones.
- --get-active-zones	List all zones currently in use (have an interface or source tied to them), along with their interface and source information.
- --add-source=CIDR [--zone=ZONE]	Route all traffic coming from the IP address or network/netmask to the specified zone. If no --zone= option is provided, then the default zone is used.
- --remove-source=CIDR [--zone=ZONE]	Remove the rule routing all traffic from the zone coming from the IP address or network. If no --zone= option is provided, then the default zone is used.
- --add-interface=INTERFACE [--zone=ZONE]	Route all traffic coming from INTERFACE to the specified zone. If no --zone= option is provided, then the default zone is used.
- --change-interface=INTERFACE [--zone=ZONE]	Associate the interface with ZONE instead of its current zone. If no --zone= option is provided, then the default zone is used.
- --list-all [--zone=ZONE]	List all configured interfaces, sources, services, and ports for ZONE. If no --zone= option is provided, then the default zone is used.
- --list-all-zones	Retrieve all information for all zones (interfaces, sources, ports, services).
- --add-service=SERVICE [--zone=ZONE]	Allow traffic to SERVICE. If no --zone= option is provided, then the default zone is used.
- --add-port=PORT/PROTOCOL [--zone=ZONE]	Allow traffic to the PORT/PROTOCOL port(s). If no --zone= option is provided, then the default zone is used.
- --remove-service=SERVICE [--zone=ZONE]	Remove SERVICE from the allowed list for the zone. If no --zone= option is provided, then the default zone is used.
- --remove-port=PORT/PROTOCOL [--zone=ZONE]	Remove the PORT/PROTOCOL port(s) from the allowed list for the zone. If no --zone= option is provided, then the default zone is used.
- --reload	Drop the runtime configuration and apply the persistent configuration.