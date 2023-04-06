# Stockage

## Créer partition

`parted`:

- unit (s, B, MiB, MB): préciser l'unité
- mklabel(msdos, gpt): créer un label
- mkpart(primary, extended, logical): créer une partition
- help: aide

`udevadm settle`: toujours executer à la fin

## Créer FS

`mkfs.xfs/mkfs.ext4 /dev/vdb1`