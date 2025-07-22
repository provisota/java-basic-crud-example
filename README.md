<!-- TOC -->
* [Java Spring Boot PostgreSQL CRUD Example](#java-spring-boot-postgresql-crud-example)
  * [Prerequisites](#prerequisites)
  * [Project Structure](#project-structure)
  * [Build & Run](#build--run)
  * [API Usage](#api-usage)
    * [Sample Requests](#sample-requests)
  * [Swagger UI](#swagger-ui)
<!-- TOC -->

# Java Spring Boot PostgreSQL CRUD Example

## Prerequisites

* JDK 17 or higher
* Gradle (or use the provided Gradle Wrapper)
* PostgreSQL database

## Project Structure

```
java-basic-crud-example
├── build.gradle
├── settings.gradle
├── .gitignore
├── README.md
└── src
    └── main
        ├── java
        │   └── com
        │       └── example
        │           └── demo
        │               ├── DemoApplication.java
        │               ├── controller
        │               │   └── UserController.java
        │               ├── model
        │               │   └── User.java
        │               ├── repository
        │               │   └── UserRepository.java
        │               └── service
        │                   └── UserService.java
        └── resources
            └── application.properties
```

## Build & Run

1. **Clone or unzip the project**

   ```bash
   git clone <repo-url>  # or unzip java-basic-crud-example.zip
   cd java-basic-crud-example
   ```

2. **(Optional) Generate Gradle Wrapper**
   If the `gradlew` scripts are missing:

   ```bash
   gradle wrapper
   ```

3. **Build the project**

    * Using Gradle Wrapper (recommended):

      ```bash
      ./gradlew clean build
      ```
    * Or using system Gradle:

      ```bash
      gradle clean build
      ```

   A JAR file will be created in `build/libs/` (e.g., `java-basic-crud-example-0.0.1-SNAPSHOT.jar`).

4. **Run the application**

    * Via Gradle:

      ```bash
      ./gradlew bootRun
      ```
    * Or directly:

      ```bash
      java -jar build/libs/java-basic-crud-example-0.0.1-SNAPSHOT.jar
      ```

   The application starts on port **8080**.

## API Usage

This project provides a CRUD REST API for a `User` entity under the `/users` endpoint.

### Sample Requests

* **Create a user**

  ```bash
  curl -X POST -H "Content-Type: application/json" \
    -d '{"name":"Alice","email":"alice@example.com"}' \
    http://localhost:8080/users/
  ```

* **Get all users**

  ```bash
  curl http://localhost:8080/users/
  ```

* **Get a user by ID**

  ```bash
  curl http://localhost:8080/users/1
  ```

* **Update a user**

  ```bash
  curl -X PUT -H "Content-Type: application/json" \
    -d '{"name":"Alice Smith","email":"alice.smith@example.com"}' \
    http://localhost:8080/users/1
  ```

* **Delete a user**

  ```bash
  curl -X DELETE http://localhost:8080/users/1
  ```

## Swagger UI

To enable interactive API documentation:

1. **Add dependency** in `build.gradle`:

   ```groovy
   implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.1.0'
   ```

2. **(Optional) Customize API info** by annotating `DemoApplication.java`:

   ```java
   @OpenAPIDefinition(
     info = @Info(
       title = "User CRUD API",
       version = "1.0",
       description = "Spring Boot CRUD example"
     )
   )
   ```

3. **Rebuild and run** the application.

4. **Open Swagger UI** in your browser:

   ```
   http://localhost:8080/swagger-ui/index.html
   ```
