FROM httpd:2.4.52-alpine3.15

RUN apk update; \
    apk upgrade;
    
RUN apk add \
    bash \
    apache2 \
    php-apache2 \
    curl \
    ca-certificates \
    php-pdo \
    php-zip \
    php-mysqli \
    php-pdo_mysql \
    php-curl

RUN sed -i "s/#LoadModule\ rewrite_module/LoadModule\ rewrite_module/" /usr/local/apache2/conf/httpd.conf;

COPY docker/apache/apache.conf /usr/local/apache2/conf/apache.conf
RUN echo "Include /usr/local/apache2/conf/apache.conf" \
    >> /usr/local/apache2/conf/httpd.conf