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

Imagem DockerHub
https://hub.docker.com/repository/docker/diovanes/codeeducation

⇒ docker push diovanes/codeeducation
⇒ docker run diovanes/codeeducation
