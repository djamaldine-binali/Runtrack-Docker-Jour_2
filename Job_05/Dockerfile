FROM php:8-apache 

COPY /var/www/html/

EXPOSE 80 

RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

CMD ["apache2-foreground"]

