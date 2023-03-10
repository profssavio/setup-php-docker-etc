# SETUP PHP ESCOLA TÉCNICA

## REQUISITOS NECESSÁRIOS

- Ter o docker instalado no computador ```https://docs.docker.com/engine/install/```

## PASSOS

### 1 - Clone repositório do SETUP PHP

```
https://github.com/profssavio/setup-php-docker-etc.git
```

### 2 - Suba os containers do projeto

```
docker compose up -d
```

### 3 - Testar se o php está funcionando corretamente

No browser digitar: http://localhost:3000/phpinfo.php


### 4 - Acessar o container para rodar o composer

```
docker compose exec app bash
```

```
composer install
```

# PhpMyAdmin

### http://localhost:8082

# VERSIONAMENTO

## 1 - Remover todo o histórico do git

```
rm -rf .git
```

## 2 - Versionando 

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
