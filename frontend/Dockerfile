# Stage 1 — Build Angular App
FROM node:18 AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build --prod

# Stage 2 — Serve with Nginx
FROM nginx:stable

# Clear default nginx HTML directory
RUN rm -rf /usr/share/nginx/html/*

# IMPORTANT — Copy the correct Angular dist folder
COPY --from=build /app/dist/angular-15-crud/ /usr/share/nginx/html/

# Copy custom Nginx config
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

