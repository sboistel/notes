#Créer un LVM
```
pvcreate /dev/sdb
vgcreate vgdata /dev/sdb
lvcreate: -n lvdata -L 15G vgdata
mkfs -t ext4 /dev/vgdata/lvdata
```
Edit fstab pour qu'il se monte automatiquement où on veut

#Resize LVM
```
umount /dev/vgdata/lvdata
e2fsck /dev/vgdata/lvdata
lvreduce -r -L size /dev/vgdata/lvdata
```

ATTENTION: le FS ne doit pas être utilisé.