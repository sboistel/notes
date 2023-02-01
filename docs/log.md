# How to configure log

## Rsyslog

`/etc/rsyslog.d/*.conf`
`/etc/rsyslog.conf`

Utiliser local0 à local7 pour des logs personnalisés

`logger -p facility.level message`

Facility:


Priority level:

1. debug
2. info
3. notice
4. warning, warn (same as warning)
5. err, error (same as err)
6. crit
7. alert
8. emerg, panic (same as emerg)

`/var/log` dossier de logs

## Logrotate

Conf de logrotate dans /etc/logrotate.d/*:

```
/var/log/http_check {
    daily
    compress
    dateext
    rotate 30
    missingok
}
```

`logrotate -f /etc/logrotate.d/*` force le logrotate