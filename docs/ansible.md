#Installer ansible

```
pip index versions ansible
pip install ansible==version
```

#Configurer ansible
```
touch ansible.cfg
vim ansible.cfg
```

Contenu de ansible.cfg:

```
{
[defaults]
inventory=./inventory
}
```

```
touch inventory
vim inventory
```

Contenu de inventory:

```
{
hostname ansible_host=0.0.0.0 ansible_user=user ansible_private_key_file=/path

[group]
hostname
}
```

#Installer sshpass
`dnf install sshpass`