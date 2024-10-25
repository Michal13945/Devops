# Etap 1: Budowanie aplikacji
FROM node:14 AS build

# Ustawiamy katalog roboczy w kontenerze
WORKDIR /app

# Kopiujemy pliki package.json i package-lock.json
COPY package*.json ./

# Instalujemy zależności
RUN npm install

# Kopiujemy pozostałe pliki projektu
COPY . .

# Budujemy aplikację (statyczne pliki w katalogu 'build')
RUN npm run build

# Etap 2: Serwowanie aplikacji za pomocą Nginx
FROM nginx:alpine

# Kopiujemy zbudowane pliki do katalogu Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Otwieramy port 80
EXPOSE 80

# Uruchamiamy Nginx
CMD ["nginx", "-g", "daemon off;"]

