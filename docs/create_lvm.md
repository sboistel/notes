# Créer un LVM

`parted set lvm on`: à utiliser sur la partition où on souhaite faire du LVM

Possibilité de le faire sur un disque entier sans partitionner

```
pvcreate /dev/sdb
vgcreate vgdata /dev/sdb
lvcreate: -n lvdata -L 15G vgdata
mkfs -t ext4 /dev/vgdata/lvdata
```
Edit fstab pour qu'il se monte automatiquement où on veut

# LVM VDO

Installer vdo et kmod-kvdo

`lvcreate --type vdo --name vdo-lv01 --size 5G vg01`: préciser le type

# Inspecter LVM

- `pvdisplay`
- `vgdisplay`
- `lvdisplay`

# Resize LVM
```
umount /dev/vgdata/lvdata
e2fsck /dev/vgdata/lvdata
lvreduce -r -L size /dev/vgdata/lvdata
```

ATTENTION: le FS ne doit pas être utilisé.

- `vgextend`
- `lvextend` 

## XFS

- `xfs_growfs`: permet d'adapter la taille du FS au nouveau volume (XFS)

## EXT4

`resize2fs`: même chose pour ext4 

## SWAP

Ajouter du stockage au lv et reformater en swap avec mkswap

# Reduce LVM

## Reduce VG

`pvmove`: retirer un PV

- `vgreduce`

## Remove

- `lvremove`
- `vgremove`
- `pvremove`