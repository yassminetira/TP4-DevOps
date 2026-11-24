# TP4 – Docker et Docker Compose

## 1. Présentation du projet

Ce projet consiste à conteneuriser une application MERN en utilisant Docker et Docker Compose.

L'application est composée de trois services :

- **Client :** interface utilisateur développée avec React.
- **Server :** API REST développée avec Node.js et Express.
- **MongoDB :** base de données NoSQL.

## 2. Prérequis

- Docker Desktop
- Docker Compose
- Git

## 3. Clonage du projet

```bash
git clone https://github.com/wiem-kb/MyAppReact.git
cd MyAppReact
```

## 4. Construction des images Docker

```bash
docker build -t mern-server ./Server
docker build -t mern-client ./Client
```

## 5. Création du réseau Docker

```bash
docker network create mern-network
```

Ce réseau permet la communication entre les trois conteneurs.

## 6. Lancement de l'application avec Docker Compose

```bash
docker compose up --build
```

Cette commande permet de construire les images, de créer le réseau et de démarrer automatiquement les trois services.

## 7. Connexion à MongoDB

Le serveur Express utilise la bibliothèque officielle MongoDB et la variable d'environnement `MONGO_URI`.

```text
mongodb://mongodb:27017/mern
```

## 8. Accès à l'application

| Service | Adresse |
|---|---|
| Client React | http://localhost:3000 |
| API Express | http://localhost:9000/api/health |
| MongoDB (réseau interne) | mongodb:27017 |

## 9. Vérification du fonctionnement

Vérifier l'état des conteneurs :

```bash
docker compose ps
```

Vérifier les logs du serveur :

```bash
docker compose logs server
```

Résultats obtenus :

```text
Server running on port 9000
MongoDB connected successfully
```

L'interface React affiche le message `API is running`, confirmant la communication avec le serveur Express.

## 10. Arrêt de l'application

```bash
docker compose down
```

## 11. Conclusion

Ce TP a permis de conteneuriser une application MERN, de configurer la communication entre les services et d'automatiser leur déploiement grâce à Docker Compose.