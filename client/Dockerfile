# Stage 1: Build React aplikacije
FROM node:18-alpine as build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Serviranje builda preko Nginx-a
FROM nginx:alpine

# Kopiraj build direktorij iz prethodnog stagea u Nginx direktorij
COPY --from=build /app/build /usr/share/nginx/html

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
