# Spring Boot Java

#### Spring Initilizr:

[https://start.spring.io/](https://start.spring.io/)

dependencies:

* `Spring Web`
* `Spring Data JPA`
* `PostgreSQL Driver`

maven, java 21, application.properties then download zip, unpack and open.



create .env file:

```
DB_URL=jdbc:postgresql://127.0.0.1:5432/postgres
DB_USERNAME=postgres
DB_PASSWORD=secretpassword
```



applications.properties under src/main/java/resources

```
spring.application.name=example-app
server.port=8080

# Loggin
logging.pattern.console=%clr(%d{HH:mm:ss}){faint} %clr(%-5level) %msg%n

# Database
spring.datasource.url=${DB_URL}
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}

# JPA and Hibernate
spring.datasource.driver-class-name=org.postgresql.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.sql.init.mode=never

# OpenAPI
springdoc.api-docs.path=/openapi.json
springdoc.swagger-ui.path=/
```





go 2 folders down after `/src/main/java/com/`

```
mkdir controller service repository model 
```



controller:

@RestController



service:

@Service&#x20;



repository:

interface ... extends JpaRepository {}



entity:

@Entity @Id

```
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
@Schema(accessMode = Schema.AccessMode.READ_ONLY)
private Long id;
@CreationTimestamp
@Schema(accessMode = Schema.AccessMode.READ_ONLY)
private Instant createdAt;
@UpdateTimestamp
@Schema(accessMode = Schema.AccessMode.READ_ONLY)
private Instant updatedAt;
```



create run.sh

```
#!/usr/bin/env bash

set -a && . ./.env && set +a && ./mvnw spring-boot:run
```

then run it using bash run.sh.







#### config

openapi config:

&#x20;`/src/main/java/com/`  2 folders down create config folder and in it CorsConfig.java

```
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class CorsConfig implements WebMvcConfigurer {

    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOriginPatterns("*") // Add the client URL here
                .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                .allowedHeaders("*")
                .allowCredentials(true);
    }
}
```

&#x20;OpenApiConfig.java:

```
import io.swagger.v3.oas.annotations.OpenAPIDefinition;
import io.swagger.v3.oas.annotations.info.Contact;
import io.swagger.v3.oas.annotations.info.Info;
import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.servers.Server;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.util.List;

@OpenAPIDefinition(info = @Info(title = "Math API", contact = @Contact(name = "Leander", email = "contact@leanderziehm.com"), version = "0.1.0"))
@Configuration
public class OpenApiConfig {

    @Value("${x.openapi.server.url}")
    private String serverUrl;

    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
                .servers(List.of(
                        new Server().url(serverUrl).description("Server")));
    }
}
```



























Prometheus

OpenTelemetry

Sentry

Datadog

Datasource Micrometer



## AWS S3

```
<dependency>
    <groupId>software.amazon.awssdk</groupId>
    <artifactId>s3</artifactId>
    <version>2.29.0</version>
</dependency>
```
