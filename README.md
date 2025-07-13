# 1. Commandes de base
## Voir la version de Docker installée :
 ```bash
docker --version
 ```
## Vérifier si le  Docker fonctionne :
 ```bash
docker info
```
## Afficher l’aide Docker :
 ```bash
docker help
```

# 2. Dockerfile
## Exemple de Dockerfile :
```bash
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```
## Explication :
- `FROM node:18` : base image Node.js version 18  
- `WORKDIR /app` : répertoire de travail dans le conteneur  
- `COPY package*.json ./` : copie les fichiers de dépendances  
- `RUN npm install` : installe les packages  
- `COPY . .` : copie tous les fichiers dans le conteneur  
- `EXPOSE 3000` : ouvre le port 3000  
- `CMD ["npm", "start"]` : démarre l’application


 # 3. Images Docker
 ## Télécharger une image depuis Docker Hub :
 ```bash
docker pull nom_image
```
## Lister les images téléchargées :
```bash
docker images
```
## Supprimer une image :
```bash
docker rmi nom_image
```
## Construire une image à partir d’un Dockerfile :
```bash
docker build -t mon_image .
 ```

#  4. Conteneurs
## Créer et exécuter un conteneur :
```bash
docker run nom_image
 ```
## Exécuter en arrière-plan (détaché) :
```bash
docker run -d nom_image
 ```
## Exécuter avec un port mappé :
```bash
docker run -d -p 8080:80 nom_image
 ```
## Lister les conteneurs en cours d’exécution :
```bash
docker ps
```
## Lister tous les conteneurs (même arrêtés) :
```bash
docker ps -a
```
## Arrêter un conteneur :
```bash
docker stop id_conteneur
```
## Supprimer un conteneur :
```bash
docker rm id_conteneur
```

#  5. Volumes et données
## Créer un volume :
```bash
docker volume create mon_volume
```
## Lister les volumes :
```bash 
docker volume ls
```
## Monter un volume dans un conteneur :
```bash 
docker run -v mon_volume:/chemin/dans/le/conteneur nom_image
```

# 6. Docker Compose
## Exemple de fichier docker-compose.yml :
```bash
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```
## Commandes utiles :
### Lancer les services :
```bash
docker-compose up
```
### Lancer avec build :
```bash
docker-compose up --build
```
### Arrêter les services :
```bash
docker-compose down
```
### Rebuild seulement :
```bash
docker-compose build
```

#  7. Réseaux Docker
## Lister les réseaux Docker :
```bash
docker network ls
```
## Créer un réseau :
```bash
docker network create mon_reseau
```
## Connecter un conteneur à un réseau :
```bash
docker network connect mon_reseau mon_conteneur
```

#  8. Inspecter & Logs
## Voir les logs d’un conteneur :
```bash
docker logs id_conteneur
```
## Entrer dans un conteneur :
```bash
docker exec -it id_conteneur bash
```
## Inspecter les informations d’un conteneur :
```bash
docker inspect id_conteneur
```

#  9. Nettoyage
## Supprimer tous les conteneurs arrêtés :
```bash
docker container prune
```
## Supprimer toutes les images inutilisées :
```bash
docker image prune
```
## Supprimer tout :
```bash
docker system prune -a
```

# 10. Docker Hub
## Se connecter à Docker Hub :
```bash
docker login
```
## Taguer une image avant de la pousser :
```bash
docker tag mon_image mon_utilisateur/mon_image
```
## Pousser une image vers Docker Hub :
```bash
docker push mon_utilisateur/mon_image
```

 # 11. Docker Swarm
 ## Initialiser un Swarm (sur le manager) :
 ```bash
docker swarm init
```
## Ajouter un worker au Swarm (commande à lancer sur le worker) :
 ```bash
docker swarm join --token <TOKEN> <IP_MANAGER>:2377
```
## Voir les nœuds du cluster (sur le manager) :
 ```bash
docker node ls
```
## Déployer un service :
 ```bash
docker service create --name mon_service -p 80:80 nginx
```
## Lister les services :
 ```bash
docker service ls
```
## Voir les tâches d’un service :
 ```bash
docker service ps mon_service
```
## Mettre à jour un service :
```bash
docker service update --image nginx:alpine mon_service
```
## Supprimer un service :
```bash
docker service rm mon_service
```
## Quitter le Swarm (sur un nœud) :
```bash
docker swarm leave
```
## Supprimer le cluster (sur le manager) :
```bash
docker swarm leave --force
```















