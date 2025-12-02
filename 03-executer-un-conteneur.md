# Exécuter un conteneur

### Challenge

- Arrêtez tous les conteneurs en marche et faites un peu de ménage.

`docker rm -rf $(docker ps -qa)`

-----

- Lancez un conteneur basé sur l'image officielle du serveur Redis

`docker run -dit redis`

---

- Vérifiez si le conteneur est en état d'exécution.

`docker ps` puis l'on regarde si le conteneur est bien en cours d'exécution.

---

- Notez l'identifiant et le nom humainement lisible du conteneur.

`docker ps` et l'on récupère l'identifiant et le nom humainement lisible.

---

- Lancez un deuxième conteneur basé sur l'image officielle de Redis et nommez le `conteneur_redis`

`docker run -dit --name conteneur_redis redis`

- `--name` pour préciser un nom à notre conteneur.

---

- Vérifiez s'il tourne comme prévu.

`docker ps` puis l'on vérifie s'il tourne.

---

- Arrêtez le conteneur `conteneur_redis`

`docker stop conteneur_redis`

---

- Affichez le ou les conteneurs en cours d'exécution

`docker ps`

---

- Lancez un conteneur basé sur l'image `hello-world` de manière à ce qu'il s'autodétruise juste après son exécution

`docker run --rm hello-world`

- `--rm` pour supprimer le conteneur dès lors qu'il a terminé sa mission.

---

- Vérifie s'il ne reste aucune trace du conteneur que vous venez de lancer

`docker ps -a` on vérifie qu'il a bien été supprimé et pas simplement éteint.

---

- Lancez un autre conteneur basé sur l'image `hello-world`, mais sans qu'il soit supprimé après son exécution

`docker run -dit hello-world`

---

- Vérifier la présence du conteneur à l'arrêt.

`docker ps -a` on vérifie qu'il est bien présent

---

- Lancez un troisième conteneur basé sur l'image `hello-world`, mais en arrière plan.

`docker run -d hello-world` 

- `-d` pour détacher le conteneur

---

- Vérifiez si le conteneur est en état d'exécution

`docker ps -a`

Il est à l'arrêt car il a fini sa mission à savoir vérifier l'installation de Docker en affichant du texte sur le terminal.

---

- Le conteneur que vous venez de lancer a produit une sortie. Pouvez-vous la récupérer, et si oui,
  comment 

Oui on peut récupérer la sortie avec `docker logs NOM`

- `logs` permet d'obtenir la sortie du conteneur.

---

- Pouvez-vous savoir à quelle heure exacte le conteneur a produit cette sortie ?

`docker logs -t NOM`

- `-t` permet de connaître la date exacte

