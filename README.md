# spring-boot-microservices
Complete Spring Boot Infrastructure

## Infrastructure service via docker
### mysql
#### command line
```sh
docker run -d --name mysql -p 3306:3306 -v ${HOME}/dev/docker/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=<PASSWD> mysql
```
#### docker-compose
```yaml
services:
  mysqldb:
    image: mysql
    container_name: mysql
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: <PASSWD>
    volumes:
      - ${HOME}/dev/docker/mysql:/var/lib/mysql
```
### rabbitmq
#### command line
```sh
docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 -e RABBITMQ_DEFAULT_USER=guest RABBITMQ_DEFAULT_PASS=guest rabbitmq:management
```
#### docker-compose
```yaml
services:
  rabbitmq:
    container_name: rabbitmq
    image: rabbitmq:management
    environment:
      - RABBITMQ_DEFAULT_USER=guest
      - RABBITMQ_DEFAULT_PASS=guest
    ports:
      - "5672:5672"
      - "15672:15672"
```
### vault
#### command line
```sh
docker run -d --name vault -p 8200:8200 --cap_add=IPC_LOCK -e VAULT_DEV_ROOT_TOKEN_ID=934f9eae-31ff-a8ef-e1ca-4bea9e07aa09 vault
```
#### docker-compose
```yaml
services:
  vault:
    image: vault
    container_name: vault
    cap_add:
      - IPC_LOCK
    environment:
      VAULT_DEV_ROOT_TOKEN_ID: 934f9eae-31ff-a8ef-e1ca-4bea9e07aa09
    ports:
      - 8200:8200
```
### zipkin
#### command line
```sh
docker run -d --name zipkin -p 9411:9411 -e STORAGE_TYPE=mem openzipkin/zipkin
```
#### docker-compose
```yaml
services:
  zipkin:
    image: openzipkin/zipkin
    container_name: zipkin
    # Environment settings are defined here https://github.com/openzipkin/zipkin/tree/1.19.0/zipkin-server#environment-variables
    environment:
      - STORAGE_TYPE=mem
      # Uncomment to disable scribe
      # - SCRIBE_ENABLED=false
      # Uncomment to enable self-tracing
      # - SELF_TRACING_ENABLED=true
      # Uncomment to enable debug logging
      # - JAVA_OPTS=-Dlogging.level.zipkin=DEBUG
    ports:
      # Port used for the Zipkin UI and HTTP Api
      - 9411:9411
```
### redis
### nosql db
## Spring Cloud microservices
- [x] config-server
- [x] eureka
- [x] admin
- [x] zuul
- [x] hystrix-dashboard
- [ ] spring cloud bus
- [ ] microservices-dashboard
- [ ] spring boot microservices
