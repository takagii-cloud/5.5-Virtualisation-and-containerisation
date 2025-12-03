# Conteneuriser CMatrix

### Dockerfile brut

Pour conteneuriser CMatrix il nous faut créer un Dockerfile avec le contenu suivant :

```dockerfile
FROM alpine

LABEL org.opencontainers.image.authors="takagii"
LABEL org.opencontainers.image.description="Container image for CMatrix"

git clone https://github.com/abishekvashok/cmatrix
apk update
apk add git
git clone https://github.com/abishekvashok/cmatrix
cd cmatrix/
ls -l
autoreconf -i
apk add autoconf
autoreconf -i
apk add automake
autoreconf -i
echo $?
./configure LDFLAGS="-static"
apk add alpine-sdk
./configure LDFLAGS="-static"
mkdir -pv /usr/lib/kbd/consolefonts
mkdir -pv /usr/share/consolefonts
apk add ncurses-dev ncurses-static
./configure LDFLAGS="-static"
make
ls -lh ./cmatrix
./cmatrix
history

```

En essayant de construire notre image, on rencontre une première erreur sur la ligne 6 car git n'est pas encore installé.

---

### Installation des paquets nécessaires

De ce fait il faudrait installer dans un premier temps tout les paquets nécessaires.

```dockerfile
FROM alpine

LABEL org.opencontainers.image.authors="takagii"
LABEL org.opencontainers.image.description="Container image for CMatrix"

WORKDIR /cmatrix

RUN apk update
RUN apk add git

RUN git clone https://github.com/abishekvashok/cmatrix .

RUN apk add autoconf
RUN apk add automake

RUN autoreconf -i

RUN apk add alpine-sdk

RUN mkdir -pv /usr/lib/kbd/consolefonts
RUN mkdir -pv /usr/share/consolefonts

RUN apk add ncurses-dev ncurses-static
RUN ./configure LDFLAGS="-static"

RUN make
CMD ["./cmatrix"]

```

`WORKDIR` : définit le répertoire de travail.

`RUN` : ajoute à chaque fois un layer à notre image.

Cette version est actuellement fonctionnelle.

---

#### Optimisation

On peut optimiser notre contenu afin de réduire au maximum la taille de l'image. Par exemple en précisant   tout les paquets à installer en une seule ligne avec `\` ce qui réduit le nombre de commandes `RUN`.

```dockerfile
FROM alpine

LABEL org.opencontainers.image.authors="takagii" \
      org.opencontainers.image.description="Container image for CMatrix"

WORKDIR /cmatrix

RUN apk update && \
    apk add git autoconf automake alpine-sdk ncurses-dev ncurses-static && \
    git clone https://github.com/abishekvashok/cmatrix . && \
    autoreconf -i && \
    mkdir -pv /usr/lib/kbd/consolefonts && \
    mkdir -pv /usr/share/consolefonts && \
    ./configure LDFLAGS="-static" && \
    make

CMD ["./cmatrix"]
```

