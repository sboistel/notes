# SELinux

ATTENTION: policycoreutils et policycoreutils-python-utils doivent être installés

/etc/selinux/config: définir l'état de selinux

`getenforce` & `setenforce` (ATTENTION: TEMPORAIRE)

`chcon`permet de modifier un context de manière temporaire, il disparaitra si on utilise restorecon

`semanage fcontext` permet de gérer les contextes de fichier:

- -l: list
- -a: add
- -d: delete

Exemple: `semanage fcontext -a -t httpd_sys_content_t '/virtual(/.*)?'`

`restorecon /path` applique les modification au répertoire et à tous les fichiers à l'intérieur:

- -R, -r: recursive
- v: verbose

`getsebool`

`setsebool`

`semanage boolean`

`sealert -a /var/log/audit/audit.log` liste les incidents selinux 

`sealert -l id` analyser les alertes selinux

# SELinux avec firewall

SELinux attribut à certains services l'utilisation de ports autorisés (EX: ssh 22/tcp)

`semanage port -l`

Pour modifier le context d'un port:
`semanage port -a -t port_label -p tcp|udp PORTNUMBER`

