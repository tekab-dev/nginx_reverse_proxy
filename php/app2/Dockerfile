FROM php:7.3-apache
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions gd xdebug
RUN pecl install -o -f redis \
&&  rm -rf /tmp/pear \
&&  docker-php-ext-enable redis
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
COPY php.ini /usr/local/etc/php/php.ini
COPY src/ /var/www/html/
