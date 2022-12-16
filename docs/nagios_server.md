# Installer Nagios Core

## Installer python3
`dnf install python3`

## Installer apache

Voir Configurer apache

`firewall-cmd --add-port=80/tcp --permanent`

## Installation nagios

### Repository codeready-builder RHEL
`subscription-manager repos --enable codeready-builder-for-rhel-8-x86_64-rpms`

### Repository EPEL
`dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm`

### Configurer nagios
```
dnf install nagios
dnf install python3-passlib
htpasswd -c /etc/nagios/htpasswd.users user
```

Remplacer les lignes AuthUserFile.* dans /etc/httpd/conf.d/nagios.conf par AuthUserFile /etc/nagios/htpasswd.users
