# Boot

## Targets

- graphical.target
- multi-user.target
- rescue.target
- emergency.target

`systemctl list-dependencies graphical.target`: liste les dependances de cette target

`systemctl isolate multi-user.target`: selectionner une target à isoler pendant le fonctionnement

`systemctl get-default`: target par defaut

`systemctl set-default`

## Target at boot

Changer la valeur de systemd.unit=....... dans grub