# Crontab

`at`: planifier des tâches dans la journée ou le lendemain

`atq`: voir les taches des différents users

`atrm 5`: retirer le job 5

`crontab -e`
```
# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed
```

`/etc/crontab, /etc/cron.d`: utiliser pour éditer des jobs système

# Anacron

Permet de planifier des jobs qui seront exécutés même si le système a été éteint*

# Systemd Timer

Programmer un service