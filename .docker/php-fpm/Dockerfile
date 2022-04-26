FROM php:7.3.19-fpm

RUN useradd -ms /bin/bash gas

WORKDIR /usr/local/etc/php-fpm.d

USER root

# composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# system
RUN apt-get update && apt-get install --no-install-recommends -qy \
        openssl \
        libpq-dev \
        libxslt-dev \
        unzip \
        git \
        libzip-dev

RUN chmod 777 -R /var/www

RUN apt update && apt upgrade -y

# clean
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
WORKDIR /var/www

# xdebug
RUN pecl install xdebug-2.7.2 && docker-php-ext-enable xdebug

# db
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql && \
    docker-php-ext-install pdo_pgsql pgsql xsl

RUN docker-php-ext-install zip
ADD php.ini /usr/local/etc/php/php.ini
RUN mkdir -p /var/www/.composer
COPY keys.dev.pub /var/www/.composer/keys.dev.pub
COPY keys.tags.pub /var/www/.composer/keys.tags.pub
COPY cacert.pem /etc/ssl/certs/cacert.pem

EXPOSE 9000