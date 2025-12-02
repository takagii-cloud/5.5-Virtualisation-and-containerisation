# Se connecter à un conteneur

### Challenge

- Lancez un conteneur basé sur l'image `redis` de manière à vous connecter  directement au *shell* Bash du conteneur. Nommez le conteneur `shell_redis`.

`docker run -it --name shell_redis redis /bin/bash`

---

- Quelle est la version du *shell* Bash fourni par le conteneur ?

`bash --version`

----

- Quittez le *shell* du conteneur.

`exit` ou `CTRL+D`

___

- Vérifiez s'il est bien arrêté.

`docker ps -a`

---

- Supprimez-le

`docker rm ID`

---

- Lancez un autre conteneur `exec_redis` basé sur cette même image. Cette fois-ci, le conteneur devra tourner en arrière-plan.

`docker run -dit --name exec_redis redis`

---

-  Vérifiez si le conteneur tourne en arrière-plan comme prévu.

`docker ps`

---

- Connectez-vous au *shell* Bash du conteneur en état d'exécution.

`docker exec -it exec_redis /bin/bash`

---

- Affichez la version du *shell* Bash.

`bash --version`

---

- Quittez le conteneur

`exit`

---

- Reconnectez-vous sans spécifier le chemin complet vers le *shell* Bash.

`docker exec -it exec_redis bash`

---

- Quittez le conteneur en utilisant une autre manière que celle que vous  venez d'utiliser.

`CTRL+D`

___

- Vérifiez si le conteneur tourne toujours

`docker ps`

---

- Reconnectez-vous une dernière fois au conteneur. Cette fois-ci, utilisez le  *shell* rudimentaire `sh` plutôt que Bash

`docker exec -it exec_redis sh`

---

- Quittez le conteneur

`exit` ou `CTRL+D`

---

- Arrêtez le et supprimez-le

`docker stop exec_redis`

`docker rm exec_redis`