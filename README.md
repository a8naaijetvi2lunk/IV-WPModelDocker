# WordPress Docker

## Introduction

WPModelDocker est un projet conçu pour simplifier le déploiement et la gestion de sites WordPress en utilisant Docker. Ce projet fournit une configuration Docker Compose qui orchestre plusieurs conteneurs, y compris WordPress, MySQL, PhpMyAdmin et Nginx, pour créer un environnement de développement ou de production robuste et facile à utiliser pour WordPress.

## Prérequis

- Docker
- Docker Compose

Assurez-vous d'avoir Docker et Docker Compose installés sur votre machine. Pour les instructions d'installation, veuillez vous référer à la [documentation officielle de Docker](https://docs.docker.com/get-docker/).

## Installation/Configuration

1. Clonez le dépôt ou téléchargez les fichiers sur votre machine locale.
2. Copiez `env.example` dans un nouveau fichier nommé `.env` et mettez à jour les variables d'environnement selon vos besoins.
3. Naviguez vers le répertoire du projet et lancez les conteneurs Docker :

   ```bash
   docker-compose up -d
   ```

### Configuration de docker-compose.yml
- Définit plusieurs services : `db` (MySQL), `phpmyadmin`, `wp` (WordPress), `wp-cli`, et `nginx`.
- Chaque service est configuré avec des volumes spécifiques, des ports, et des dépendances entre les services.
- Les fichiers de configuration pour PhpMyAdmin et Nginx sont montés à partir du répertoire `config`.
- Les données de WordPress sont persistées dans le répertoire `wp-app`.

## Configuration

### Docker Compose

Le fichier `docker-compose.yml` définit les services, les réseaux et les volumes pour votre site WordPress. Personnalisez ce fichier si vous avez besoin de modifier la configuration des services.

### Fichiers de configuration

Le répertoire `config` contient les fichiers de configuration pour WordPress et les services associés. Modifiez ces fichiers selon vos besoins pour adapter votre configuration.

### Application WordPress

Le répertoire `wp-app` est l'endroit où les fichiers et les données de WordPress seront stockés. Cette configuration permet une gestion et une sauvegarde faciles de votre application WordPress.

## Utilisation

Une fois les conteneurs en fonctionnement, vous pouvez accéder à votre site WordPress à `http://localhost` (ou au port spécifié dans votre fichier `.env`).

## Dépannage/Problèmes communs

- Si vous rencontrez des problèmes avec les conteneurs Docker, consultez les journaux des conteneurs pour détecter d'éventuels messages d'erreur :

  ```bash
  docker-compose logs
  ```

- Assurez-vous que toutes les variables d'environnement dans le fichier `.env` sont correctement définies.

## Contribution

J'encourage les contributions à ce projet. Si vous avez des suggestions ou des améliorations, veuillez forker le dépôt et soumettre une pull request.

## Licence

Licence MIT.

```

## Configuration détaillée

### Variables d'environnement (.env et env.example)
- **WORDPRESS_URL_SITE** : L'URL de votre site WordPress.
- **IP** et **PORT** : L'adresse IP et le port sur lesquels votre site sera accessible.
- **MYSQL_ROOT_PASSWORD**, **MYSQL_DATABASE**, **MYSQL_USER**, **MYSQL_PASSWORD** : Configuration de votre base de données MySQL.
- **PMA_USER**, **PMA_PASSWORD**, **UPLOAD_LIMIT** : Configuration de PhpMyAdmin.
- **WORDPRESS_DB_HOST**, **WORDPRESS_DB_USER**, **WORDPRESS_DB_PASSWORD**, **WORDPRESS_DB_NAME** : Configuration de la base de données WordPress.
- **NGINX_SERVER_NAME**, **NGINX_PORT** : Configuration du serveur Nginx.

## Maintenance et mises à jour
- Pour mettre à jour les images Docker, utilisez `docker-compose pull` suivi de `docker-compose up -d`.
- Gérez les volumes Docker pour la persistance des données, notamment pour la base de données et les fichiers WordPress.

## Sécurité
- Assurez-vous de configurer des mots de passe sécurisés et de gérer correctement les variables d'environnement.
- Suivez les bonnes pratiques de sécurité pour Docker et les applications que vous déployez.

