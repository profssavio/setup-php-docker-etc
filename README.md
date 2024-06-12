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

- No browser digitar: http://localhost:3000/phpinfo.php
- Agora bastar criar os seus arquivos php conforme o seu projeto.


# COMPOSER - Acessar o container para rodar o composer

```
docker compose exec app bash
```

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

# Descrição das principais diretivas do php.ini 

- https://www.php.net/manual/pt_BR/ini.core.php
- Arquivo de configuração fica no diretório: ```./docker/php/custom.ini```

#  PHP

## Conceito de strict_types

Por padrão todos os arquivos PHP estão em modo “fraco” de checagem de tipo, para entender melhor veja o exemplo abaixo:

```
<?php
function sum(int $num1) : int 
{
    return $num1 + 1;
}
var_dump(sum('1')); // int(2)
```

Percebam que nossa função foi assinada para receber um parâmetro $num1 do tipo int, e retornar também um int, sendo a soma do parâmetro passado mais 1, porém a chamada da função é feita passando a string ‘1’ e mesmo assim o PHP conseguiu interpretar, converter (string -> int) e retornar um int, que neste caso foi o número 2. E isso só foi possível devido estarmos com o modo fraco de tipo de checagem. Interessante não ?

Agora vamos ativar o modo strict_types e fazer o mesmo exemplo anterior:

```
<?php
declare(strict_types=1);
function sum(int $num1) : int 
{
    return $num1 + 1;
}
var_dump(sum('1'));
```

A única mudança feita foi a inclusão do comando declare(strict_types=1), ou seja, a partir deste momento, a checagem de tipo será feita, e é como se estivéssemos dizendo para o PHP para utilizar o modo “forte” de checagem de tipo. O exemplo acima irá produzir um fatal error, como abaixo:

```
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to sum() must be of the type integer, string given
```
# GIT

Alguns comandos fundamentais são essenciais para entender e usar efetivamente o controle de versão. 
Aqui estão alguns dos comandos mais importantes:

- **git init:** Inicializa um repositório Git em um diretório local.
- **git clone:** Clona um repositório Git existente para o seu diretório local.
- **git add:** Adiciona arquivos ao index (staging area) para serem incluídos no próximo commit.
- **git commit:** Grava as mudanças no repositório. É necessário incluir uma mensagem descritiva.
- **git status:** Mostra o estado atual do seu repositório, incluindo arquivos modificados, adicionados e excluídos.
- **git diff:** Mostra as diferenças entre o estado atual do seu diretório de trabalho e o estado atual do repositório.
- **git pull:** Atualiza o repositório local com as mudanças do repositório remoto.
- **git push:** Envia os commits locais para o repositório remoto.
- **git branch:** Lista, cria ou exclui branches.
- **git checkout:** Permite mudar entre branches ou restaurar arquivos.
- **git merge:** Une duas branches diferentes.
- **git rebase:** Reaplica commits de uma branch em outra base, reescrevendo o histórico.
- **git log:** Mostra o histórico de commits.
- **git remote:** Gerencia repositórios remotos.
- **git fetch:** Busca as atualizações do repositório remoto, mas não as aplica.
- **git reset:** Permite reverter o estado do repositório para um determinado ponto na história.
