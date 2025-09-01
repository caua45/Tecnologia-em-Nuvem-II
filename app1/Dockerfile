FROM php:8.2-apche

ENV PORT=8080

RUN a2emod rewrite

COPY . /var/www/html/

RUN chown -R www-data:www-data /var/wwww/html && chmod -R 755 /var/www/html

RUN sed -i "s/Listen 80/Listen ${PORT}/" /etc/apache2/ports.conf && \
    sed -i "s/<VirtualHost \*:80>/<VirtualHost \*:${PORT}>/" /etc/apache2/sites-avaliable/000-default.conf

    RUN echo '<Directory /var/www/html>' >> /etc/apache2.conf && \
        echo '   Options Indexes FollowSymLinks'  >> /etc/apache2/apache2.conf && \
        echo '   AllowOverride All' >> /etc/apache2/apache2.conf && \
        echo '   Require all granted'  >> /etc/apache2/apache2.conf && \
         echo '</Directory>' >> /etc/apache2/apache2.conf 

         EXPOSE ${PORT}

         CMD ["apache2-foreground"]
