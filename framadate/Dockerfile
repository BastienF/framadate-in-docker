FROM php:5.6-apache
MAINTAINER "Bastien Fiorentino <fiorentino.bastien@gmail.com>"

RUN apt-get update && \
    apt-get install -y git zlib1g-dev libicu-dev g++ php5-mysqlnd zip unzip

RUN docker-php-ext-configure intl && \
    docker-php-ext-install intl mysqli mysql pdo pdo_mysql zip

RUN git clone https://github.com/BastienF/framadate.git .

RUN php -r "readfile('https://getcomposer.org/installer');" | php && ./composer.phar install
RUN mkdir tpl_c && \
    chown -R www-data:www-data .

ADD php.ini /var/www/html/
