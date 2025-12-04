# Combiner les conteneurs

### Challenge

- Créez un réseau Docker `blognet`.



---

- Lancez un conteneur basé sur l'image officielle de MariaDB (`mariadb`). Nommez-le `db` avec un nom d'hôte identique. Rattachez-le au réseau`blognet`.  Créez une base de données `blog` accessible à l'utilisateur    `bloguser` identifié par le mot de passe `pass123`. Le mot de passe `root`    MySQL sera créé au hasard. Les données persistantes du serveur MariaDB    seront stockées dans un volume `dbvol`.



---

- Lancez un deuxième conteneur basé sur l'image de PHPMyAdmin (`phpmyadmin`). Nommez-le `dbadmin` avec un nom d'hôte identique. Rattachez-le au réseau    `blognet`. Il devra accéder à la base `blog` stockée dans le conteneur`db`. L'interface web devra être accessible sur le port 9090 de l'hôte.



---

- Lancez un troisième conteneur basé sur l'image officielle de WordPress    (`wordpress`). Nommez-le `web` avec un nom d'hôte identique. Rattachez-le    au réseau `blognet`. Utilisez la base de données `blog` disponible dans le    conteneur `db`. Le contenu de WordPress comme les images et les plug-ins    seront stockées dans un volume persistant `webvol`. Le blog devra être accessible sur le port 9000 de l'hôte.