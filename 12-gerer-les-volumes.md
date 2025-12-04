# Gérer les volumes

### Challenge n°1

- Créez un volume nommé `volumelocal`.

`docker volume create volumelocal`

- Inspectez le volume et déterminez l'emplacement exact où seront stockées les données du volume sur le système hôte.

`docker volume inspect volumelocal`

Les données sont stockées dans `var/lib/docker/volumes/volumelocal/_data`

---

- Créez un fichier texte `fichier.txt` dans le volume, avec le contenu `Ce fichier existe`.

`echo "Ce fichier existe" > /var/lib/docker/volumes/volumelocal/_data/fichier.txt`

---

- Démarrez un conteneur détaché nommé `montagevolume` basé sur l'image du    serveur web Apache `httpd`. Montez le volume `volumelocal` dans le    répertoire `/data` du conteneur.

`docker run -d --name montagevolume --mount src=volumelocal,dst=/data httpd:latest`

`--mount` : pour monter un volume dans le conteneur.

`dst=/data` : chemin dans le conteneur où le volume sera monté.

Tout ce qui sera écrit dans `/data` à l'intérieur du conteneur sera sauvegardé dans le volume et persistera même à la suppression.

---

- Connectez-vous au conteneur `montagevolume` avec un *shell* Bash.

`docker exec -it montagevolume bash`

---

- Vérifiez si le volume est disponible à l'intérieur du conteneur.

`ls /data` pour voir si le fichier à l'intérieur existe.

---

- Depuis le conteneur, créez un fichier texte `conteneur.txt` avec le contenu `Coucou depuis le conteneur`.

`echo "Coucou depuis le conteneur" > /data/conteneur.txt`

---

- Détachez-vous du conteneur

`exit`

---

- Vérifiez l'existence et le contenu du fichier `conteneur.txt` depuis le système hôte.

`ls /var/lib/docker/volumes/volumelocal/_data/`

---

### Challenge n°2

- Lancez un conteneur détaché nommé `ephemere` et basé sur l'image du serveur Web Apache `httpd`. Attachez un volume éphémère d'une taille de 128 Mo au  répertoire `/tempdata` du conteneur.

`docker run -d --name ephemere --tmpfs /tempdata:size=128m httpd`

`--tmpfs /tempdata:size=128m` : capacité limitée à  **128 Mo**. Volume **volatile** qui disparaît à l'arrêt du conteneur. `/tempdata` sera utilisable immédiatement dans le conteneur.

---

- Inspectez le conteneur en affichant les caractéristiques du volume éphémère.

`docker inspect ephemere`

---

- Connectez-vous au conteneur et affichez la taille de `/tempdata`.

`docker exec -it ephemere bash`

