#Commandes adhoc
`ansible -m ping host`

-m permet d'appeler un module ansible

-k permet de demander le mot de passe pour l'authentification

-bK permet de demander les privilèges

#Commandes playbook

##Taches
```
---
- hosts: linux

  tasks:
  - name: add a group
    group:
      name: exemple
      state: present
```

##Vars
```
vars:
    collegue:
    - titi
    - tata
    - toto
```

##Handlers
```
- name: Add line to conf file
    lineinfile:
      path: /path
      line: new line
      state: present
    delegate_to: hostname
    notify: Restart service

handlers:

- name: Restart service
    systemd:
      name: service
      state: restarted
      enabled: yes
```    
Un handlers est une tache à exécuter uniquement si elle est appelée en utilisant notify.

##Roles
Un rôle est une structure de fichier qui permet de séparer les éléments d'un playbook.

`ansible-galaxy role init name`

Permet de créer un role.

- tasks: permet de stocker les taches
- handler: stocke les handlers
- templates: template de texte
- files: fichier à fournir pour le playbook
- vars: variables qui ne sont pas amenées à changer
- default: variables utilisables en extra vars

Pour lancer un role, on crée un playbook qui appelle ce role:

```
---
- hosts: webservers
  roles:
    - common
    - webservers
```