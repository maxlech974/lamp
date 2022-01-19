FROM php:7.4-fpm-buster

RUN apt-get update; \
    apt-get upgrade;

RUN apt-get install -y \
    poppler-utils \
    ghostscript \
    wkhtmltopdf \
    libzip-dev \
    zlib1g-dev \ 
    libicu-dev \
    xvfb \
    g++ \
    imagemagick \
    zip

RUN apt install -y libmagickwand-dev --no-install-recommends && \
    pecl install imagick

RUN docker-php-ext-install pdo_mysql && \
    docker-php-ext-configure intl && \
    docker-php-ext-install intl && \
    docker-php-ext-install zip && \
    docker-php-ext-enable imagick && \
    docker-php-ext-install gd


ADD https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/
RUN chmod uga+x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions imagick

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /var/www