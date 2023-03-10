# SETUP PHP ESCOLA TÉCNICA

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

