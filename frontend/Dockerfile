# Étape 1 : Construire l'application React
FROM node:14 AS build
WORKDIR /app

# Copier les fichiers nécessaires pour installer les dépendances
COPY package.json ./
RUN npm install

# Copier tout le code source et construire le projet
COPY . .
RUN npm run build

# Étape 2 : Servir les fichiers statiques avec Nginx
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Exposer le port 80 (par défaut pour Nginx)
EXPOSE 80

# Lancer Nginx en mode foreground
CMD ["nginx", "-g", "daemon off;"]
