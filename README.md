# SETUP PHP LARAVEL

- Ter o docker instalado no computador ```https://docs.docker.com/engine/install/```

## PASSOS

Clone repositório do SETUP PHP

```
git clone https://github.com/profssavio/setup-php-docker-etc.git
cd setup-php-docker-etc
git checkout setup-laravel-docker
cd ..
```

Clone repositório do Laravel e passo a passo

```
git clone https://github.com/laravel/laravel.git app-laravel
```

Copie os arquivos do branch setup-laravel-docker para o seu projeto

```
cp -rf setup-php-docker-etc/* app-laravel/
```

Entra dentro do diretório

```
cd app-laravel
```

Apagar as referências do git anterior

```
rm -rf .git .github/
```

Crie o Arquivo .env

```
cp .env.example .env
```

Atualize as variáveis de ambiente do arquivo .env


```
APP_NAME=LaravelApp
APP_URL=http://localhost:3000

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=nome_que_desejar_db
DB_USERNAME=nome_usuario
DB_PASSWORD=senha_aqui

CACHE_DRIVER=redis
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```

Suba os containers do projeto

```
docker compose up -d
```

Acessar o container do app

```
docker compose exec app bash
```

Instale as dependências do projeto

```
composer install
```

Gere a key do projeto Laravel

```
php artisan key:generate
```

Acessar o projeto: http://localhost:3002



## COMANDOS BÁSICOS

- ```composer init``` : cria seu arquivo composer.json para você de forma simples e rápida.
- ```composer install``` : instalar todas as dependências descritas no arquivo composer.json, devemos utilizar este comando para executar a tarefa de forma automática.
- ```composer update``` : caso deseje inserir ou remover pacotes ou alterar o autoload devemos sempre atualizar nosso projeto.
- ```composer dump-autoload``` : toda vez que houver necessidade de atualizar o autoloader do nosso sistema


# PhpMyAdmin

### http://localhost:8082

Administrador

- usuário: ```root```
- senha: ```123456```

# VERSIONAMENTO

## 1 - Remover todo o histórico do git

```
rm -rf .git
```

## 2 - Crie um repositorio no GIT e sigas instruções, exemplo:

```
git init
git remote add origin https://github.com/xxxxx.git
git branch -M main
git add .
git commit -m "xxx"
git push
```

# XDEBUG com VSCODE

```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "type": "php",
            "request": "launch",
            "port": 9003,
            "pathMappings": {
                "/var/www/html": "${workspaceRoot}"
            }
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9003,
        }
    ]
}
```
# DOCKER - COMANDOS EXTRAS

1. Listar os container que estão rodando

```
docker ps 
```

2. Listar todos os container (rodando ou parado)

```
docker ps -a
```

3. Parar ou subir um container

```
docker stop $CONTAINER_ID

docker start $CONTAINER_ID
```

4. Remover um container 

```
docker rm $CONTAINER_ID
```

5. Listar uma imagem e remover

```
docker images
docker rmi $IMAGE_id
```

6. Listar os volumes

```
docker volume list
```

7. Parar e eliminar os container de outra forma.

```
docker compose down
```

8. Recriar a imagem

```
docker compose up --build --force-recreate
```
