# Introdução
Projeto para registro e descoberta de microserviços (Service Discovery / Registry - Eureka Cloud). Para tanto basta instalar
o Eureka Netflix Server com Spring. Com isso, é possível registrar várias instancias de serviços com mesmo serviceId 
que fica registrado o Eureka System Status bem como poder utilizar o Zuul Server para router (como o VIP) para os
microserviços registrados no Eureka.

# Tecnologias
Java 8, spring-boot 1.2.8 e spring-cloud-netflix 1.0.7.

# Como inicar o servidor
mvn spring-boot:run

# Como acessar o projeto
- Eureka System Status: http://localhost:8761/
- Eureka System Apps: http://localhost:8761/eureka/apps/

# Application.yml
Arquivo que contém as configurações do servidor em /resources/application.yml

```
server:
  port: ${PORT:8761}

eureka:
  instance:
    hostname: localhost
    leaseRenewalIntervalInSeconds: 15
  client:
    registerWithEureka: false
    fetchRegistry: false
    server:
      enable-self-preservation: false
      waitTimeInMsWhenSyncEmpty: 0
    serviceUrl:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
```