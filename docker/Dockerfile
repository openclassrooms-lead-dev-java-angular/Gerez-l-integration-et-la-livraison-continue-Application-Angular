# Build Angular
FROM node:20.19.0 AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci --cache .npm --prefer-offline

COPY . .

RUN npm run build


## Nginx server
FROM nginx:1.27-alpine

COPY nginx/nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist/olympic-games-starter/browser/ /app/
expose 80

cmd ["nginx", "-g", "daemon off;"]
