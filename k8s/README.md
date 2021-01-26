# Spring on Kubernetes

## Build

### maven plugin: 

```bash
$ mvn spring-boot:build-image
```

```txt
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (java-compile) @ ifservice ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-resources-plugin:3.1.0:testResources (default-testResources) @ ifservice ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory C:\Users\pydemia\git\airuntime-ifservice\src\test\resources
[INFO] 
[INFO] --- kotlin-maven-plugin:1.4.10:test-compile (test-compile) @ ifservice ---
[WARNING] Source root doesn't exist: C:\Users\pydemia\git\airuntime-ifservice\src\test\java
[INFO] Applied plugin: 'spring'
[INFO] Applied plugin: 'all-open'
[INFO] Applied plugin: 'jpa'
[INFO] Applied plugin: 'no-arg'
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:testCompile (java-test-compile) @ ifservice ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-surefire-plugin:2.22.2:test (default-test) @ ifservice ---
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------

...

.   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.3.3.RELEASE)
...

2021-01-27 04:15:43.957  INFO 14020 --- [extShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2021-01-27 04:15:44.007  INFO 14020 --- [extShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
[INFO] 
[INFO] Results:
[INFO] 
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO] 
[INFO] 
[INFO] --- maven-jar-plugin:3.2.0:jar (default-jar) @ ifservice ---
[INFO] Building jar: C:\Users\pydemia\git\airuntime-ifservice\target\ifservice-0.0.1-SNAPSHOT.jar
[INFO] 
[INFO] --- spring-boot-maven-plugin:2.3.3.RELEASE:repackage (repackage) @ ifservice ---
[INFO] Replacing main artifact with repackaged archive
[INFO] 
[INFO] <<< spring-boot-maven-plugin:2.3.3.RELEASE:build-image (default-cli) < package @ ifservice <<<
[INFO] 
[INFO] 
[INFO] --- spring-boot-maven-plugin:2.3.3.RELEASE:build-image (default-cli) @ ifservice ---
[INFO] Building image 'docker.io/library/ifservice:0.0.1-SNAPSHOT'
[INFO] 
[INFO]  > Pulling builder image 'gcr.io/paketo-buildpacks/builder:base-platform-api-0.3' 100%
[INFO]  > Pulled builder image 'gcr.io/paketo-buildpacks/builder@sha256:e00ab721d73ba886849d27c21ab411e32a5db57965a4283fe5b9746227bd4766'
[INFO]  > Pulling run image 'docker.io/paketobuildpacks/run:base-cnb' 100%
[INFO]  > Pulled run image 'paketobuildpacks/run@sha256:f084de391a20a9cd1521a9fbeffe782f210fd014d4557eb3cc3bfd56cade69fb'
[INFO]  > Executing lifecycle version v0.10.2
[INFO]  > Using build cache volume 'pack-cache-8e7d99bab980.build'
[INFO] 
[INFO]  > Running creator
[INFO]     [creator]     ===> DETECTING
[INFO]     [creator]     5 of 18 buildpacks participating
[INFO]     [creator]     paketo-buildpacks/ca-certificates   1.0.1
[INFO]     [creator]     paketo-buildpacks/bellsoft-liberica 6.2.0
[INFO]     [creator]     paketo-buildpacks/executable-jar    3.1.3
[INFO]     [creator]     paketo-buildpacks/dist-zip          2.2.2
[INFO]     [creator]     paketo-buildpacks/spring-boot       3.5.0
[INFO]     [creator]     ===> ANALYZING
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/ca-certificates:helper" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/bellsoft-liberica:helper" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/bellsoft-liberica:java-security-properties" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/bellsoft-liberica:jre" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/bellsoft-liberica:jvmkill" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/executable-jar:class-path" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/spring-boot:helper" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/spring-boot:spring-cloud-bindings" from app image
[INFO]     [creator]     Restoring metadata for "paketo-buildpacks/spring-boot:web-application-type" from app image
[INFO]     [creator]     ===> RESTORING
[INFO]     [creator]     ===> BUILDING
[INFO]     [creator]     
[INFO]     [creator]     Paketo CA Certificates Buildpack 1.0.1
[INFO]     [creator]       https://github.com/paketo-buildpacks/ca-certificates
[INFO]     [creator]       Launch Helper: Reusing cached layer
[INFO]     [creator]     
[INFO]     [creator]     Paketo BellSoft Liberica Buildpack 6.2.0
[INFO]     [creator]       https://github.com/paketo-buildpacks/bellsoft-liberica
[INFO]     [creator]       Build Configuration:
[INFO]     [creator]         $BP_JVM_VERSION              11.*            the Java version
[INFO]     [creator]       Launch Configuration:
[INFO]     [creator]         $BPL_JVM_HEAD_ROOM           0               the headroom in memory calculation
[INFO]     [creator]         $BPL_JVM_LOADED_CLASS_COUNT  35% of classes  the number of loaded classes in memory calculation
[INFO]     [creator]         $BPL_JVM_THREAD_COUNT        250             the number of threads in memory calculation
[INFO]     [creator]         $JAVA_TOOL_OPTIONS                           the JVM launch flags
[INFO]     [creator]       BellSoft Liberica JRE 11.0.10: Reusing cached layer
[INFO]     [creator]       Launch Helper: Reusing cached layer
[INFO]     [creator]       JVMKill Agent 1.16.0: Reusing cached layer
[INFO]     [creator]       Java Security Properties: Reusing cached layer
[INFO]     [creator]     
[INFO]     [creator]     Paketo Executable JAR Buildpack 3.1.3
[INFO]     [creator]       https://github.com/paketo-buildpacks/executable-jar
[INFO]     [creator]       Process types:
[INFO]     [creator]         executable-jar: java org.springframework.boot.loader.JarLauncher
[INFO]     [creator]         task:           java org.springframework.boot.loader.JarLauncher
[INFO]     [creator]         web:            java org.springframework.boot.loader.JarLauncher
[INFO]     [creator]     
[INFO]     [creator]     Paketo Spring Boot Buildpack 3.5.0
[INFO]     [creator]       https://github.com/paketo-buildpacks/spring-boot
[INFO]     [creator]       Launch Helper: Reusing cached layer
[INFO]     [creator]       Web Application Type: Reusing cached layer
[INFO]     [creator]       Spring Cloud Bindings 1.7.0: Reusing cached layer
[INFO]     [creator]       Image labels:
[INFO]     [creator]         org.opencontainers.image.title
[INFO]     [creator]         org.opencontainers.image.version
[INFO]     [creator]         org.springframework.boot.spring-configuration-metadata.json
[INFO]     [creator]         org.springframework.boot.version
[INFO]     [creator]     ===> EXPORTING
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/ca-certificates:helper'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/bellsoft-liberica:helper'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/bellsoft-liberica:java-security-properties'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/bellsoft-liberica:jre'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/bellsoft-liberica:jvmkill'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/executable-jar:class-path'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/spring-boot:helper'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/spring-boot:spring-cloud-bindings'
[INFO]     [creator]     Reusing layer 'paketo-buildpacks/spring-boot:web-application-type'
[INFO]     [creator]     Reusing 1/1 app layer(s)
[INFO]     [creator]     Reusing layer 'launcher'
[INFO]     [creator]     Reusing layer 'config'
[INFO]     [creator]     Adding label 'io.buildpacks.lifecycle.metadata'
[INFO]     [creator]     Adding label 'io.buildpacks.build.metadata'
[INFO]     [creator]     Adding label 'io.buildpacks.project.metadata'
[INFO]     [creator]     Adding label 'org.opencontainers.image.title'
[INFO]     [creator]     Adding label 'org.opencontainers.image.version'
[INFO]     [creator]     Adding label 'org.springframework.boot.spring-configuration-metadata.json'
[INFO]     [creator]     Adding label 'org.springframework.boot.version'
[INFO]     [creator]     *** Images (6b9e151e13e9):
[INFO]     [creator]           docker.io/library/ifservice:0.0.1-SNAPSHOT
[INFO] 
[INFO] Successfully built image 'docker.io/library/ifservice:0.0.1-SNAPSHOT'
[INFO] 

```


## Deploy


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
