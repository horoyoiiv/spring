
## JPA(Hibernate) - MySQL 연동  

* **의존성** 추가  
build.gradle
```
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    runtimeOnly 'mysql:mysql-connector-java'
```

* **속성** 추가  
application.yml
```
server:
  port : 8089
  context-path: api/v1

spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3308/blog?allowPublicKeyRetrieval=true&useSSL=false&characterEncoding=UTF-8&serverTimezone=UTC
    username: root
    password: 12345

jpa:
  database-platform: org.hibernate.dialect.MySQL5InnoDBDialect
  open-in-view: false
  show-sql: true
  hibernate:
    format_sql: true
    ddl-auto: create
```
##### [속성 details](https://victorydntmd.tistory.com/323)  


