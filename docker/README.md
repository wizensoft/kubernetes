## Task 1. Docker 기본

### 기본 명령어

| 명령어  |  설명  |
|---|---|
| run | 컨테이너 실행하기 |
| ps | 컨테이너 목록 확인하기 |
| stop | 컨테이너 중지하기 |
| rm | 컨테이너 제거하기 |
| logs | 컨테이너 로그보기 |
| images | 이미지 목록 확인하기 |
| pull | 이미지 다운로드하기 |
| rmi | 이미지 삭제하기 |

### 컨테이너 생성 실습

**centos 컨테이너 생성**

```
docker run --rm -it centos:7 /bin/sh
```

**간단한 웹 애플리케이션 생성**

```
docker run -d -p 4567:80 nginx
```

curl http://172.42.42.2:4567

**MySQL 생성**

```
docker run -d -p 3306:3306 \
  -e MYSQL_ALLOW_EMPTY_PASSWORD=true \
  --name mysql \
  mysql:5.7
```

*Database 생성*

```
docker exec -it mysql mysql
create database annguk CHARACTER SET utf8;
grant all privileges on annguk.* to annguk@'%' identified by 'annguk';
flush privileges;
quit
```

**Wordpress 생성**

```
docker run -d -p 8000:80 \
  -e WORDPRESS_DB_HOST=172.42.42.2 \
  -e WORDPRESS_DB_NAME=annguk \
  -e WORDPRESS_DB_USER=annguk \
  -e WORDPRESS_DB_PASSWORD=annguk \
  wordpress
```

http://172.42.42.2:8000

**컨테이너 목록 확인**

```
docker ps -a
```

**컨테이너 로그**

```
docker logs xxx
```

**컨테이너 종료**

```
docker stop xxx
```

**컨테이너 삭제**

```
docker rm xxx
```

**이미지 목록 확인**

```
docker images
```

**네트워크 생성**

```
docker network create app-network
```

## 정리

```
docker stop xxx
docker rm xxx
docker rm `docker ps -a -q`
docker rmi `docker images -q`
docker system prune -a
```
