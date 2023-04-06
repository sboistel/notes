# Stratis

## Installer

Installer `stratis-cli` et `stratisd`

- stratisd: service
- stratis-cli: contient les commandes stratis

## Créer

- `stratis pool create name /dev/*`: créer un pool
- `stratis pool add-data name /dev/*`: ajouter à un pool
- `stratis filesystem create poolname name`: ajouter FS à un pool

Ajouter dans fstab:
`UUID=c7b57190-8fba-463e-8ec8-29c80703d45e /dir1 xfs defaults,x-systemd.requires=stratisd.service 0 0`