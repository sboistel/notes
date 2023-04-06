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

## Journalctl

Voir des logs

Editer le fichier /etc/systemd/journald.conf:

- persistent: Stores journals in the /var/log/journal directory, which persists across reboots. If the /var/log/journal directory does not exist, then the systemd-journald service creates it.

- volatile: Stores journals in the volatile /run/log/journal directory. As the /run file system is temporary and exists only in the runtime memory, the data in it, including system journals, does not persist across a reboot.

- auto: If the /var/log/journal directory exists, then the systemd-journald service uses persistent storage; otherwise it uses volatile storage. This action is the default if you do not set the Storage parameter.

- none: Do not use any storage. The system drops all logs, but you can still forward the logs.