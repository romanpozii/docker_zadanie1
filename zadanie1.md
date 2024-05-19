# Budowanie aplikacji
```
FROM node:14 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install --production
COPY . .
```

# Uruchomienie aplikacji na lekkim obrazie
```
FROM node:14-alpine AS final
WORKDIR /app
COPY --from=build /app .
```

# Uruchomienie serwera
```
EXPOSE 3000
CMD ["node", "server.js"]
```

# Metadane obrazu
```
LABEL maintainer="Roman Pozii"
```

# Komendy do uruchomienia serwera
```
docker build -t zadanie1 .
docker run -p 3000:3000 zadanie1
```

# Przeglądanie logów
```
docker logs 219054b2cc41
````

# Sprawdzenie liczby warstw
```
docker history zadanie1
```

