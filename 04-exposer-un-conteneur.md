# Exposer un conteneur

### Challenge

- Téléchargez la dernière version de l'image officielle du serveur Web Apache

`docker pull httpd`

---

- Lancez un conteneur `apache_bienvenue` publiquement accessible sur le port 9900 du système hôte.

`docker run -dit --name apache_bienvenue -p 9900:80 httpd`

- `-p 9900:80` pour rediriger le trafic du port 9900 du système hôte vers le port 80.

---

- Vérifier si le conteneur tourne correctement

`docker ps -a`

---

- Jetez un œil à la configuration de la redirections de ports

`docker ps` et on regarde la section des `PORTS`

---

- Utilisez la commande `curl` en ligne de commande pour afficher la page par défaut du serveur web.

`curl http://localhost:9900`

---

- Affichez cette page avec un navigateur web sur la machine hôte
  - Si l'on utilise Docker sur une VM :
    - Rediriger le port 9900 de la machine virtuelle vers un port > 1024 de sa machine hôte.
    - http://localhost:9900
  - Si l'on utilise Docker sur sa machine :
    - http://localhost:9900

---

- Créer un répertoire `~/mapage` sur le système hôte, contenant un fichier `index.html` avec le contenu `<h1>Coucou ! </h1>`

`mkdir ~/mapage && echo "<h1>Coucou ! </h1> > ~/mapage/index.html"`

---

- Lancez un conteneur `apache_coucou` publiquement accessible sur le port 9901 du système hôte, et qui utilise votre page `index.html` personnalisée comme page par défaut dans un volume partagé en lecture seule. Reportez-vous à la section *How to use this image* sur Docker Hub pour en savoir plus sur la configuration du serveur Apache, notamment l'emplacement  de la page web par défaut.

`docker run -dit --name apache_coucou -p 9901:80 -v ~/mapage:/usr/local/apache2/htdocs:ro httpd`

- `-v` permet de faire un montage de volume. On mappe le volume local `~/mapage` vers `/usr/local/apache2/htdocs` le dossier web d'Apache dans le conteneur
- `ro` pour dire lecture seule (read only)

---

- Vérifiez si le conteneur tourne correctement et jetez un œil sur la    configuration de la redirection des ports.

`docker ps` pour vérifier que le conteneur tourne correctement et l'on regarde la section `PORTS`.

---

- Là encore, affichez votre page personnalisée sur le système hôte en  utilisant successivement `curl` et un navigateur web.

De la même manière si l'on est sur une VM on effectue une redirection de ports. Sinon http://localhost:9901

