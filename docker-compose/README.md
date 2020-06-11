# Docker Compose

도커 컴포즈에 대한 이해

## Task 1. Docker Compose 실습

### YAML

[YAML Syntax](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)

### 기본 명령어

| 명령어  |  설명  |
|---|---|
| up | 시작 |
| stop | 중지 |
| down | 중지 후 삭제 |
| ps | 목록 |
| logs | 로그보기 |

### 도커 컴포즈 실습

**간단한 웹 애플리케이션 생성**

docker-compose/nginx/docker-compose.yml

```yml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "1005:80"
```

```
docker-compose up -d
```

curl http://172.42.42.2:1005

**wordpress 생성**

docker-compose/wordpress/docker-compose.yml

```yml
version: '3'
services:
  wordpress:
    image: wordpress
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_NAME: annguk
      WORDPRESS_DB_USER: annguk
      WORDPRESS_DB_PASSWORD: annguk
    ports:
      - "2005:80"
    restart: always
  mysql:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: annguk
      MYSQL_DATABASE: annguk
      MYSQL_USER: annguk
      MYSQL_PASSWORD: annguk
```

```
docker-compose up -d
```

**목록**

```
docker-compose ps
```

**로그**

```
docker-compose logs -f
```

**종료 후 제거**

```
docker-compose down
```

## 정리

```
docker-compose down
docker system prune -a
```
