# SELinux

`semanage fcontext` permet de gérer les contextes de fichier

Exemple: `semanage fcontext -a -t httpd_sys_content_t '/virtual(/.*)?'`

`restorecon` applique les modification au répertoire et à tous les fichiers à l'intérieur

`getsebool`

`setsebool`

`sealert -a /var/log/audit/audit.log` liste les incidents selinux 

# SELinux avec firewall

SELinux attribut à certains services l'utilisation de ports autorisés (EX: ssh 22/tcp)

`semanage port -l`

Pour modifier le context d'un port:
`semanage port -a -t port_label -p tcp|udp PORTNUMBER`

