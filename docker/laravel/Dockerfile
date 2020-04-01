FROM php:7.3.6-fpm-alpine3.9

RUN apk add bash mysql-client
RUN docker-php-ext-install pdo pdo_mysql

# Os comandos RUN abaixo serao executados de dentro do /var/www
WORKDIR /var/www

# Removendo todo o conteúdo padrão do PHP
RUN rm -rf /var/www/html

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# copiando todo o conteudo do Laravel para a pasta publica do PHPFPM

COPY . /var/www

RUN composer install && \
    cp .env.example .env && \
    php artisan key:generate && \
    php artisan config:cache
#


# Criando um link simbolico da pasta /var/www/public (do Laravel)
# para /var/www/html (que é a pasta pública do PHP FPM).
# Ou seja, toda vez que estiverem acessando a pasta html
# na realidade estao acessando a pasta public, tipo um redirecionamento
RUN ln -s public html

# Porta padrao do PHP FPM
EXPOSE 9000

# Manter o servirdor rodandndo
ENTRYPOINT ["php-fpm"]
