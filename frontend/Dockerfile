# Use official nginx image
FROM nginx:stable

# Remove default nginx page
RUN rm -rf /usr/share/nginx/html/*

# Copy Angular build output to nginx html directory
COPY dist/frontend-app/ /usr/share/nginx/html/

# Copy custom nginx config
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose nginx port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]

