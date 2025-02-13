FROM php:7.4-fpm

RUN apt-get update && apt-get install -y nginx

RUN echo 'server {\
    listen 80;\
    server_name localhost;\
    root /var/www/html;\
    index index.php index.html index.htm;\
    location / {\
        try_files $uri $uri/ =404;\
    }\
    location ~ \.php$ {\
        include fastcgi_params;\
        fastcgi_pass 127.0.0.1:9000;\
        fastcgi_index index.php;\
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;\
    }\
    location ~ /\.ht {\
        deny all;\
    }\
}' > /etc/nginx/sites-available/default

COPY index.html /var/www/html/index.html
COPY save.php   /var/www/html/save.php 
COPY results.json /var/www/html/results.json

EXPOSE 80 

RUN chmod -R 777 /var/www/html

CMD ["sh", "-c", "php-fpm -D && nginx -g 'daemon off;'"]


