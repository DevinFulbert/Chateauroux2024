# 10/ Docker

## <span style="color: black"> **Installation de Docker** ##

###Installation du service Docker###

`sudo apt install docker-ce` <---- Installation du service

`sudo systemctl status docker` <---- Vérification du service

###Création des différents fichiers pour l'installation###

Nous avons créer les fichiers suivants : `app.js` et `Dockerfile` au répertoire suivant : `/home/chx-docker/docker`

####app.js####

`// app.js`

`const http = require('http');`

`const server = http.createServer((req, res) => {`

`  res.statusCode = 200;`

`  res.setHeader('Content-Type', 'text/plain');`

`  res.end('Hello, Docker!\n');`

`});`

`const port = process.env.PORT || 3000;`

`server.listen(port, () => {`

`  console.log(``Server running on http://localhost:${port}``);`

`});`

####Dockerfile####

`# Use the official Node.js image`

`FROM node:14`

`# Set the working directory`

`WORKDIR /usr/src/app`

`# Copy package.json and package-lock.json`

`COPY package*.json ./`

`# Install app dependencies`

`RUN npm install`

`# Bundle app source`

`COPY . .`

`# Expose the port`

`EXPOSE 80`

`# Command to run the application`

`CMD ["node", "app.js"]`

###Créer l'image et run le container###

`sudo docker build -t node:latest .`

`docker run -it --name node -p 8080:80 node:latest`

