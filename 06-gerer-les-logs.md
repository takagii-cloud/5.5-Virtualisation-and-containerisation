# Gérer les logs

### Challenge

- Lancez un conteneur Apache basé sur l'image `httpd:latest`, nommé `apache_logs` et qui écoute sur le port 8080.

`docker run -dit --name apache_logs -p 8080:80 httpd:latest`

---

- Faites la même chose avec le serveur Nginx. Vous utiliserez l'image `nginx:latest`, le conteneur sera nommé `nginx_logs` et il écoutera sur le port 8081.

`docker run -dit --name nginx_logs -p 8081:80 nginx:latest`