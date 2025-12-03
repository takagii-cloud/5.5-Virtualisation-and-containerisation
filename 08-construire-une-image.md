# Construire une image

### Challenge 1

- Construisez un conteneur `nettools:latest` basé sur la dernière image de    Debian, et qui comprend les commandes `ping`, `traceroute` et `curl`. Le    *shell* Bash devra être lancé au démarrage du conteneur.

On crée un répertoire `nettools` et un fichier `Dockerfile` avec le contenu suivant :

```dockerfile
FROM debian:latest
LABEL maintener="takagii <takagiizushii@takagii.fr>"
RUN apt-get update \
	&& apt-get -y install iputils-ping curl traceroute \
	&& apt-get clean
CMD ["/bin/bash"]
```

Avec `docker build -t takagii67/debian:latest .` on construit l'image.

`docker login -u takagii67` pour se connecter à Docker Hub.

`docker push takagii67/nettools:latest` pour push l'image sur Docker Hub.

L'image est bien disponible : https://hub.docker.com/r/takagii67/nettools

---

- Lancez le conteneur `nettools` et invoquez successivement les commandes `ping -c 3 google.fr`, `curl google.fr` et `traceroute google.fr`.

`docker run -it takagii67/nettools:latest`

L'ensemble des commandes fonctionne.

---

- Quittez le conteneur et faîtes un brin de ménage.

`exit` pour quitter le conteneur, ce qui l'arrêtera par la même occasion.

`docker rm -f takagii67/nettools`

---

### Challenge 2

- Lancez un conteneur nommé `rockyvim` basé sur Rocky Linux 8 et connectez-vous au *shell* Bash de ce conteneur

`docker run -dit --name rockyvim  rockylinux:8 bash`

---

- Installez l'éditeur de texte Vim de manière interactive.

`dnf update -y` pour mettre à jour le système.

`dnf search vim` pour chercher le nom exact du paquet.

---

- Lancez Vim pour vérifier que tout va bien.

`vim`

---

- Quittez le conteneur

`exit`

---

- Construisez une image personnalisée `rockyvim:8` basée sur Rocky Linux 8 et    qui contient l'éditeur Vim.

On crée un répertoire `rockyvim` et un Dockerfile avec le contenu suivant :

```dockerfile
FROM rockylinux:8
LABEL maintener="takagii <takagiizushii@takagii.fr>"
RUN dnf update -y \
	&& dnf install -y vim
CMD ["/bin/bash"]
```

On construit l'image avec `docker build -t takagii67/rockyvim:8 .`

Puis on se connecter à Docker Hub, et l'on finit par pousser l'image.

L'image est bien disponible : https://hub.docker.com/r/takagii67/rockyvim

---

