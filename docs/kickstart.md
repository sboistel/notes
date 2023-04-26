# Kickstart

## Présentation

Un fichier kickstart démarre avec une liste de commandes.

On peut rajouter des sections en utilisant `%...` et `%end`:

- `%packages`: installer les packages en donnant leurs noms (rajouter - devant un package pour le retirer). @..... donne un groupe de packages, @^...... un environnement group
- `%pre` & `%post`: scripts à utiliser avant et après l'installation 

## Commandes

- `url --url="http://classroom.example.com/content/rhel9.0/x86_64/dvd/"`: url du média d'installation
- `repo --name="appstream" --baseurl=http://classroom.example.com/content/rhel9.0/x86_64/dvd/AppStream/`: ajouter un repo
- text: installation en mode text
- vnc
- `clearpart --all --drives=vda,vdb`: retire les partitions des disques
- `part /home --fstype=ext4 --label=homes --size=4096 --maxsize=8192 --grow`: crée une partition
- autopart: partitionnement automatique
- `ignoredisk --drives=sdc`: empeche anaconda de modifier les disques
- `bootloader --location=mbr --boot-drive=sda`: où installer le bootloader. REQUIS  
- Créer LVM:
```
part pv.01 --size=8192
volgroup myvg pv.01
logvol / --vgname=myvg --fstype=xfs --size=2048 --name=rootvol --grow
logvol /var --vgname=myvg --fstype=xfs --size=4096 --name=varvol
``` 
- `network --device=eth0 --bootproto=dhcp`: informations réseau
- `firewall --enabled --service=ssh,http`: firewall
- `lang en_US`
- `keyboard --vckeymap=us`
- `timezone --utc Europe/Amsterdam`
- `timesource --ntp-server classroom.example.com`  
- `authselect`: voir authselect(8)
- `rootpw --plaintext redhat`
- `selinux --enforcing`
- `services --disabled=network,iptables,ip6tables --enabled=NetworkManager,firewalld` 
- Groupes et users:
```
group --name=admins --gid=10001
user --name=jdoe --gecos="John Doe" --groups=admins --password=changeme --plaintext
```


## Exemple

```
#version=RHEL9

# Define system bootloader options
bootloader --append="console=ttyS0 console=ttyS0,115200n8 no_timer_check net.ifnames=0  crashkernel=auto" --location=mbr --timeout=1 --boot-drive=vda

# Clear and partition disks
clearpart --all --initlabel
ignoredisk --only-use=vda
zerombr
part / --fstype="xfs" --ondisk=vda --size=10000

# Define installation options
text
repo --name="appstream" --baseurl="http://classroom.example.com/content/rhel9.0/x86_64/dvd/AppStream/"
url --url="http://classroom.example.com/content/rhel9.0/x86_64/dvd/"

# Configure keyboard and language settings
keyboard --vckeymap=us
lang en_US

# Set a root password, authselect profile, and selinux policy
rootpw --plaintext redhat
authselect select sssd
selinux --enforcing
firstboot --disable

# Enable and disable system services
services --disabled="kdump,rhsmcertd" --enabled="sshd,rngd,chronyd"

# Configure the system timezone and NTP server
timezone America/New_York --utc
timesource --ntp-server classroom.example.com
```

```
%packages

@core
chrony
cloud-init
dracut-config-generic
dracut-norescue
firewalld
grub2
kernel
rsync
tar
-plymouth

%end
```

```
%post

echo "This system was deployed using Kickstart on $(date)" > /etc/motd

%end
```

```
%post --interpreter="/usr/libexec/platform-python"

print("This this a line of text printed with python")

%end
```

https://access.redhat.com/labs/kickstartconfig%60

Utiliser ksvalidator pour tester le fichier kickstart

## Installer

Il faut rendre le fichier disponible:

- serveur réseau
- clé usb ou dvd
- disque dur local

Dans l'installer de RHEL, il faut préciser dans les instructions en bas de l'écran la localisation:

- inst.ks=http://server/dir/file
- inst.ks=ftp://server/dir/file
- inst.ks=nfs:server:/dir/file
- inst.ks=hd:device:/dir/file
- inst.ks=cdrom:device