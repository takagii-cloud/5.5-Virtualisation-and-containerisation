# Les commandes de bases

### Challenge n°1

- Lancez deux conteneurs avec les images officielles d'Arch Linux et Alma Linux.

`docker run -dit archlinux` pour **Arch Linux**

`docker run -dit almalinux` pour **Alma Linux**

- `-d` pour *detach* qui permet de faire fonctionner un conteneur en arrière plan.
- `-i` pour *interactive* ce qui permet d'éventuellement se connecter directement au conteneur.
- `-t` pour *terminal* ce qui permet d'allouer à Docker un terminal pour se connecter au conteneur.

---

- Arrêtez et relancez chacun des deux conteneurs en utilisant successivement l'ID complet, l'ID abrégé à trois ou quatre caractères et le nom humainement lisible.

`docker ps` pour lister les conteneurs ce qui affiche leurs IDs.

`docker stop ID` pour stopper les conteneurs avec l'identifiant ID en entier.

`docker start ID` pour relancer les conteneurs.

On peut faire de même sans écrire l'ID au complet.

---

- Inspectez successivement les caractéristiques de chaque conteneur en état d'exécution.

`docker inspect NOM`

---

- Arrêtez tous les conteneurs.

`docker stop $(docker ps -qa)`

- `-q` pour n'afficher que les ID des conteneurs.
- `-a` pour afficher tout les conteneurs.

---

### Challenge n°2

- Essayez de lancer deux conteneurs en utilisant les images Rocky Linux et Oracle Linux.

`docker run -dit rockylinux` pour **Rocky Linux**

`docker run -dit oraclelinux` pour **Oracle Linux**

---

Lisez le message d'erreur que vous renvoie le terminal.

`"latest not found"` : Cela signifie que nous devons préciser un tag de version.

---

### Challenge n°3

- Lancez un conteneur Alpine Linux en invoquant `docker run -it alpine`.

---

- Regardez votre invite de commandes et essayez de deviner ce qui se passe.

Nous sommes directement sur le shell du conteneur car nous n'avons pas mis l'option `-d` lors de la création du conteneur.

---

- Ouvrez un deuxième terminal et affichez les conteneurs en état d'exécution.

On voit que notre conteneur alpine est en cours d'éxécution

---

- Revenez dans le premier terminal et quittez le *shell* en tapant `exit`.

---

- Affichez les conteneurs en état d'exécution. Que constatez-vous ?

`docker ps` pour afficher les conteneurs en cours d'exécution

Le conteneur alpine n'est plus en cours d'exécution.

---

- Essayez d'expliquer avec vos mots ce qui s'est passé.

Le conteneur a fini sa mission lorsque nous nous sommes déconnecté.

---

### Challenge n°4

Faites l'inventaire de toutes les images dont vous disposez localement en    utilisant deux syntaxes différentes.

`docker image ls`

`docker images`