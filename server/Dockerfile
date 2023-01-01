FROM php:7.4-apache

# Enabla mod rewrite rules
RUN a2enmod rewrite

# For ssl certificate
RUN a2enmod ssl && a2enmod socache_shmcb

RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql; \
    apt-get update && apt-get upgrade -y; \
    apt-get install wget \
    unzip

EXPOSE 80

RUN usermod -u 1000 www-data; \
    chmod 755 /var/www/html

# Clean up
RUN apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

