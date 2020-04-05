## Desenvolvimento de Aplicações Modernas e Escaláveis com Microsserviços

#### Desafio - Publicando imagem Laravel

Imagem DockerHub
https://hub.docker.com/repository/docker/diovanes/laravel

docker pull diovanes/laravel

⇒ docker build -t diovanes/laravel .

⇒ docker run -d --name laravel -p 8000:8000 diovanes/laravel

⇒ docker exec -it laravel bash
-> php artisan serve --host=0.0.0.0

#### Desafio - Docker

⇒ docker-compose up -d

#### Desafio - Docker Parte 2 Go

https://github.com/Diovanes/microservices/tree/master/docker/go
