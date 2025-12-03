# Compiler CMatrix

### Téléchargement de l'image Alpine Linux

Dans un premier temps on pull l'image `alpine:latest` avec la commande `docker pull alpine:latest`.

---

### Création du Dockerfile

On crée un Dockerfile dans un répertoire `cmatrix` avec le contenu suivant pour débuter.

```dockerfile
FROM alpine
LABEL org.opencontainers.image.authors="Adam"
LABEL org.opencontainers.image.description="Container Image for CMatrix"
```

---

### Construction de la première image

On construit notre première image : `docker build -t takagii67/cmatrix .`

---

### Démarrage du conteneur

On démarre notre conteneur : `docker run --rm -it takagii67/cmatrix sh`

`--rm` : pour le supprimer une fois fini.

`-it` : pour démarrer directement dessus.

`sh` : pour démarrer le shell minimal *sh*

---

### Compilation de CMatrix

### Installation de Git

On essaie d'installer le code source de CMatrix depuis Github mais la commande `git` n'est pas encore installé sur le système. Il nous faut l'installer :

```bash
apk update
apk add git
```

On essaie à nouveau d'installer CMatrix : `git clone https://github.com/abishekvashok/cmatrix.git` 

---

#### Installation d'Autoreconf et Automake

On se place ensuite sur le répertoire `cmatrix` créé automatiquement.

Pour compiler le code on utise `autoreconf`. Par défaut il n'est pas installé, alors on l'installe :

```bash
apk add autoconf
autoreconf -i
```

En essayant de compiler le code cette fois-ci nous avons une nouvelle erreur car `automake` n'est pas installé. Alors on l'installe également puis l'on compile le code.

```
apk add automake
autoreconf -i
```

It works ! On vérifie le code d'erreur avec `echo $?`. Si 0 est retourné alors il n'y a pas d'erreur.

---

#### Compilation

On peut enfin essayer de compiler l'application avec `./configure LDFLAGS="-static"`. On compile avec des liens statiques, toutes les bibliothèques utilisées sot intégrées dans le binaire final. Ainsi le binaire est indépendant.

Nouvelle erreur ! Il faut installer un compilateur : `apk add alpine-sdk`

En relançant la compilation nous avons une nouvelle erreur car des répertoires sont manquants. Il suffit de les créer :

```bash
mkdir /usr/lib/kbd/consolefonts
mkdir /usr/share/consolefonts
```

On finit par installer les dépendances NCurses : `apk add ncurses-dev ncurses-static`

---

### Final

On peut enfin relancer la commande `./configure`. On finit par utiliser `make` puis on lance cmatrix :  `cmatrix.`