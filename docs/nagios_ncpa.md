# Installer ncpa
```
dnf install python3
alternatives --set python /usr/bin/python3
dnf install https://repo.nagios.com/nagios/8/nagios-repo-8-1.el8.noarch.rpm
dnf install ncpa
```

Définir token dans /usr/local/ncpa/etc/ncpa.cfg

```
firewall-cmd --add-port:5693/tcp
cd /usr/lib64/nagios/plugins
wget https://raw.githubusercontent.com/NagiosEnterprises/ncpa/master/client/check_ncpa.py
```

Ajouter:

```
define command {
    command_name    check_ncpa
    command_line    $USER1$/check_ncpa.py -H $HOSTADDRESS$ $ARG1$
}
```

dans /etc/nagios/objects/commands.cfg

Créer:

```
define host {
          host_name               hostname
          address                 ipaddress
          check_command           check_ncpa!-t 'token' -P 5693 -M system/agent_version
          max_check_attempts      5
          check_interval          5
          retry_interval          1
          check_period            24x7
          contacts                nagiosadmin
          notification_interval   60
          notification_period     24x7
          notifications_enabled   1
          icon_image              ncpa.png
          statusmap_image         ncpa.png
          register                1
        }

        define service {
            host_name               hostname
            service_description     CPU Usage
            check_command           check_ncpa!-t 'token' -P 5693 -M cpu/percent -w 20 -c 40 -q 'aggregate=avg'
            max_check_attempts      5
            check_interval          5
            retry_interval          1
            check_period            24x7
            notification_interval   60
            notification_period     24x7
            contacts                nagiosadmin
            register                1
        }
```

dans /etc/nagios/ncpa_hostname.cfg

Ajouter:

```
cfg_file=/etc/nagios/ncpa_hostname.cfg
```

dans /etc/nagios/nagios.cfg