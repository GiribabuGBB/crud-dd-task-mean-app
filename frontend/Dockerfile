# Stage 1: Build Angular app
FROM node:18 AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build --prod

# Stage 2: Serve with NGINX
FROM nginx:stable

RUN rm -rf /usr/share/nginx/html/*

COPY --from=build /app/dist/frontend-app/ /usr/share/nginx/html/

COPY nginx.conf /etc/nginx/conf.d/default.conf

