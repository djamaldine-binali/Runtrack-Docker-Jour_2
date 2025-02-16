FROM php:7.4-fpm

RUN apt-get update && apt-get install -y nginx




RUN echo 'server { \
listen 80; \
server_name localhost; \
    root /usr/share/nginx/html; \
    index index.html; \
    location / { try_files $uri $uri/ =404; } \
    location ~ \.php$ { \
        include fastcgi_params; \
        fastcgi_pass 127.0.0.1:9000; \
        fastcgi_index index.php; \
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name; \
        } \
        }' > /etc/nginx/sites-available/default
        
        
        COPY index.html /usr/share/nginx/html/index.html
        COPY save.php /usr/share/nginx/html/results/save.php
        COPY results.json /usr/share/nginx/html/results/results.json
        
RUN chmod -R 777 /usr/share/nginx/html/results/
EXPOSE 80



CMD ["sh", "-c", "php-fpm -D && nginx -g 'daemon off;'"]


