# Conteneurs et réseaux

### Challenge n°1

- Arrêtez et supprimez le conteneur `web`.





- Rafraîchissez la page de votre blog. Vous constatez que WordPress ne s'affiche plus.



- Écrivez un `Dockerfile` simple pour construire une image PHP qui intègre l'extension `mysqli`.



- Construisez l'image `<votre_identifiant>/php:mysqli` à partir de ce`Dockerfile`.



- Publiez cette image sur Docker Hub.



- Utilisez l'image `<votre_identifiant>/php:mysqli` pour relancer votre blog WordPress.



- Arrêtez et supprimez tous les conteneurs.



- Faites le ménage dans les volumes et les réseaux personnalisés.

---

### Challenge n°2

- Dans cet atelier pratique, vous allez installer le système de gestion de    contenu Drupal comme vous l'avez fait avec WordPress.



- Créez un réseau isolé `drupal`.



- Créez un volume `db` qui contiendra les données du serveur de bases de données.



- Récupérez la dernière image de PostgreSQL.



- Ouvrez la documentation de l'image PostgreSQL sur Docker Hub et repérez les variables d'environnement pour le mot de passe, l'utilisateur et le nom de la base de données.



- Lancez un conteneur nommé `db` et basé sur PostgreSQL. Intégrez-le au    réseau `drupal`. Montez le volume `db` sur le répertoire `/var/lib/postgresql` du conteneur. Créez une base de données `drupal`    exploitée par l'utilisateur `drupal` avec le mot de passe `password123`.



- Inspectez le réseau `drupal` pour vous assurer que le conteneur `db` y est bien connecté.



- Récupérez la dernière image de l'application Drupal.



- Lancez un conteneur nommé `drupal` et basé sur Drupal. Intégrez-le au    réseau `drupal`. Publiez le port 80 du conteneur et mappez-le vers le port 80 du système hôte.



- Inspectez le réseau `drupal` et repérez vos deux conteneurs `db` et`drupal`.



- Ouvrez un navigateur web à l'adresse http://localhost.



- Lancez l'installation de Drupal. Sélectionnez le profil d'installation *Standard* et la langue anglaise. Renseignez les paramètres de connexion à votre base PostgreSQL. Affichez les options avancées pour renseigner l'hôte PostgreSQL.



- L'application Drupal met quelques minutes à s'installer.



- Si le tableau de bord de Drupal s'affiche, vous pouvez considérer que vous avez réussi le *challenge*.