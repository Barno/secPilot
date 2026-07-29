# Sezione 1: BASE (Installa le dipendenze condivise)
FROM node:22-alpine AS base
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install

# Sezione 2: SVILUPPO (Usa la base, copia il codice e avvia in live-reload)
FROM base AS development
COPY . .
EXPOSE 3000
CMD ["npm", "run", "start:dev"]

# Sezione 3: PRODUZIONE (Usa la base, compila in JS puro ed esegue)
FROM base AS production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["node", "dist/main.js"]
