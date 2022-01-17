Role Name
=========

Ce role a pour but de créer un conteneur pgadmin qui est relié à une bdd (il faudra bien sur s'assurer que le conteneur de la bdd est up). \
Deux fichiers sont très importants dans ce rôle, le fichier de création du conteneur du pgadmin et le fichier servers.json qui nous permettra de nous connecter à la bdd. 

Requirements
------------

Pour tester ce rôle il faudra utiliser un autre rôle qui installera un docker-compose (le rôle se créer à partir d'un fichier template qui est un docker-compose). 

Role Variables
--------------
- variables servers.json :\
**host_db:** ip de la bdd \
**port_db:** port de la bdd \
**maintenanceDB:** represente la bdd initiale où se connecte notre pgadmin (une fois connecté à cette bdd, nous avons accès à toutes les autres qui sont dans le même serveur) \
**username_db:** nom d'utilsateur de la bdd

- variables de pgadmin : \
**pgadmin_email:** email de pgadmin \
**pgadmin_pass:** mot de passe de pgadmin \
**pgadmin_port:** port de pgadmin 

Dependencies
------------

Ce role a besoin d'un autre role pour installer docker-compose, ici, j'utilise le role de : lianhuahayu.docker_role

Example Playbook
----------------

Un exemple de playbook de test est disponible dans le dossier test, voici un petit aperçu : 

    - hosts: localhost
      connection: local
      become: yes
      roles:
         - lianhuahayu.docker_role
         - pgadmin_role
         
License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
