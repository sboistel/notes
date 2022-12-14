# Installer ansible

```bash
pip index versions ansible
pip install ansible==version
```

# Configurer ansible
```bash
touch ansible.cfg
vim ansible.cfg
```

Contenu de ansible.cfg:

```bash
{
[defaults]
inventory=./inventory
}
```

```bash
touch inventory
vim inventory
```

Contenu de inventory:

```bash
{
hostname ansible_host=0.0.0.0 ansible_user=user ansible_private_key_file=/path

[group]
hostname
}
```

# Installer sshpass
`dnf install sshpass`