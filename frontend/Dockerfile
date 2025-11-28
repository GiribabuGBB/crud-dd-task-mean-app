# Stage 1: Build Angular app
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

# Install Angular CLI globally
RUN npm install -g @angular/cli

COPY . .

# Build Angular app
RUN ng build --configuration production

# Stage 2: Serve using NGINX
FROM nginx:stable

COPY --from=builder /app/dist/angular-15-crud /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

