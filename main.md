# Dependencies for Connecting your Spring Boot Application to PostgreSQL 
### (If dependency is not added in Spring Initializr

```xml
<dependency>
			<groupId>org.postgresql</groupId>
			<artifactId>postgresql</artifactId>
			<scope>runtime</scope>
</dependency>
```

# Confogure the application.properties

```java
spring.datasource.url=jdbc:postgresql://localhost:5432/sqltest # db connection
spring.datasource.username=postgres 
spring.datasource.password=your-pass

spring.jpa.hibernate.ddl-auto=update # automatically create tables
spring.jpa.show-sql=true # print SQL queries in console
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
```
