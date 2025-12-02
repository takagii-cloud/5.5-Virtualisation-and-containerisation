# Gérer les images

### Challenge

- Téléchargez la dernière image Docker officielle du magasin de données en  mémoire Memcached.

`docker pull memcached`

---

- Téléchargez l'image Docker officielle du serveur web Apache dans sa mouture `2-alpine`.

`docker pull httpd:2-alpine`

---

- Affichez les images que vous venez de télécharger.

`docker images` ou `docker image ls`

---

- Affichez l'espace disque total occupé par ces images.

`docker system df`

---

- Supprimez l'image de Memcached.

`docker rmi memcached`

---

- Supprimez l'image d'Apache

`docker rmi httpd:2-alpine`

---

- Vérifiez que vous n'avez plus aucune image Docker locale sur votre système.

`docker images` ou `docker image ls`