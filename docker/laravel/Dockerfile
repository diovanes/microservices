FROM php:7.3.6-fpm-alpine3.9

# Instala utils
RUN apk add --no-cache openssl bash mysql-client
RUN docker-php-ext-install pdo pdo_mysql

# Install Dockerize - https://github.com/jwilder/dockerize
ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz

# Define a pasta de trabalho
WORKDIR /var/www

# Remove o conteúdo padrão do PHP
RUN rm -rf /var/www/html

# Intala o composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# copiando todo o conteudo do Laravel para a pasta publica do PHPFPM
COPY . /var/www

# Criando um link simbolico da pasta /var/www/public (do Laravel)
RUN ln -s public html

RUN composer install && \
    cp .env.example .env && \
    php artisan key:generate && \
    php artisan config:cache

# Porta padrao do PHP FPM
EXPOSE 9000

# Manter o servirdor rodandndo
ENTRYPOINT ["php-fpm"]
