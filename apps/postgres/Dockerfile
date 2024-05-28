FROM ubuntu
# Utilise une image Node.js comme base
FROM node:20.13.1

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier les fichiers de l'application dans le conteneur
COPY . .

# Installer les dépendances de l'application
RUN npm install

# Construire l'application
RUN npm run build

# Copier et installer Progress DB (remplacez par les commandes réelles si disponibles)
COPY install_progress_db.sh /install_progress_db.sh
RUN chmod +x /install_progress_db.sh
RUN /install_progress_db.sh

# Copier le script de démarrage de Progress DB
COPY start_progress_db.sh /start_progress_db.sh
RUN chmod +x /start_progress_db.sh

# Exposer le port de l'application
EXPOSE 3000

# Démarrer Progress DB et l'application
CMD ["/bin/sh", "-c", "/start_progress_db.sh && ./node_modules/.bin/next start"]
