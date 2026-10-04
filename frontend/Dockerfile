# ---------- Étape 1 : compiler l'application Angular ----------
# Angular 22 exige Node >= 22.22.3 ou >= 24.15 -> Node 24
FROM node:24-alpine AS build
WORKDIR /app

# Copier d'abord package*.json : Docker met en cache "npm ci"
# tant que les dépendances ne changent pas
COPY package*.json ./
RUN npm ci

# Copier le reste du code puis compiler en mode production
COPY . .
RUN npx ng build --configuration production

# ---------- Étape 2 : servir les fichiers avec nginx ----------
FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/dist/frontend/browser /usr/share/nginx/html
EXPOSE 80
