# Spring

## Config

`bootstrap.yml`
`application.yml`

### Cloud Config

https://cloud.spring.io/spring-cloud-config/reference/html/

* Naming Rules

```text
{application}/{profile}[/{label}]
{application}-{profile}.yml
{label}/{application}-{profile}.yml
{application}-{profile}.properties
{label}/{application}-{profile}.properties
```

#### Server Side

```yml
spring:
  config:
    name: configserver
```

There is a `configserver.yml` in the **Config Server jar**. 
Another is to use your own application.properties, as shown in the following example:

```yml
server:
  port: 8888

spring:
  cloud:
    config:
      server:
        git:
          uri: file://${user.home}/config-repo
          # uri: https://github.com/spring-cloud-samples/config-repo
          # skipSslValidation: true
          # timeout: 4
          # fail-fast: false
          # username: xxx
          # password: xxx
          
          # ignoreLocalSshSettings: true
          # hostKey: someHostKey
          # hostKeyAlgorithm: ssh-rsa
          # privateKey: |
                        -----BEGIN RSA PRIVATE KEY-----
                        ...
                        -----END RSA PRIVATE KEY-----
                        
          # uri: https://github.com/spring-cloud-samples/config-repo
          # repos:
          #   development:
          #     pattern:
          #       - '*/development'
          #       - '*/staging'
          #     uri: https://github.com/development/config-repo
          #   staging:
          #     pattern:
          #       - '*/qa'
          #       - '*/production'
          #     uri: https://github.com/staging/config-repo
```


#### Client Side

`bootstrap.yml`

This context loads before the one that uses `application.yml`


```yml
spring:
  cloud:
    config:
      uri: http://myconfigserver.com
```

By default, if no application name is set, `application` will be used. To modify the name, the following property can be added to the `bootstrap.yml` file:

```yml
spring:
  application:
    name: myapp
```


---

## On Kubernetes

https://www.baeldung.com/spring-cloud-kubernetes

### Context: ConfigMap

:warning: **The NAME of the `ConfigMap` should matches the name of the application.

* From `application.yml`:

```yml
spring:
  cloud:
    kubernetes:
      reload:
        enabled: true
      secrets
        name: mdb-secret
spring:
  data:
    mongodb:
      host: mongodb-service
      port: 27017
      database: ${MONGO_DATABASE}
      username: ${MONGO_USERNAME}
      password: ${MONGO_PASSWORD}
```

```yml
apiVersion: v1 by d
kind: ConfigMap
metadata:
  name: spring-service
data:
  application.yml: |-
    spring:
      cloud:
        kubernetes:
          reload:
            enabled: true
          secrets
            name: mdb-secret
    spring:
      data:
        mongodb:
          host: mongodb-service
          port: 27017
          database: ${MONGO_DATABASE}
          username: ${MONGO_USERNAME}
          password: ${MONGO_PASSWORD}
```



### Context: Secrets

* `application.yml`:

```yml
spring:
  cloud:
    kubernetes:
      reload:
        enabled: true
      secrets
        name: db-secret
spring:
  data:
    mongodb:
      host: mongodb-service
      port: 27017
      database: ${MONGO_DATABASE}
      username: ${MONGO_USERNAME}
      password: ${MONGO_PASSWORD}
```

* To `ConfigMap`:

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mdb-secret
data:
  username: xxxx
  password: xxxx
```

and the pod env is:

``yml
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: spring-service
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: spring-service
      name: spring
    spec:
      containers:
      - image: javaapplication:latest
        name: springservice
        env:
          - name: MONGO_DATABASE
            value: mdb
          - name: MONGO_USERNAME
            valueFrom:
              secretKeyRef:
                name: mdb-secret
                key: username
          - name: MONGO_PASSWORD
            valueFrom:
              secretKeyRef:
                name: mdb-secret
                key: password
```

and 
