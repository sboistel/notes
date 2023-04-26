# Network File System

## Installation

`dnf install nfs-utils`

## Config

Ajouter à /etc/fstab:
```
server.lab.example.com:/shares/public  /public  nfs  rw,sync  0 0
```

# Autofs

Service qui monte et remonte automatiquement les FS si besoin

## Installation

`sudo dnf install autofs nfs-utils`

## Configuration

`systemctl enable --now autofs`

### Master Map

`vim /etc/auto.master.d/demo.autofs`:

- Pour une Indirect Map:


```
/shares /etc/auto.demo
```

- Pour une Direct Map (permet de monter un FS à un endroit précis et qui ne changera pas):
```
/- /etc/auto.direct
```

### Indirect Map

`sudo vim /etc/auto.demo`:

```
work -rw,sync serverb:/shares/work
```

### Direct Map

Permet de donner le chemin précis à monter

`sudo vim /etc/auto.direct`:

```
/mnt/docs  -rw,sync  serverb:/shares/docs
```


