FROM php:7.4-fpm-alpine3.11

RUN apk add --no-cache openssl bash mysql-client

ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz

RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/bin/ --filename=composer

RUN docker-php-ext-install pdo pdo_mysql

WORKDIR /var/www
RUN rm -rf /var/www/html

RUN ln -s public html

EXPOSE 9000
