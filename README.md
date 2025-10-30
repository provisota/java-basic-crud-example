<!-- TOC -->
* [Java Spring Boot PostgreSQL CRUD Example](#java-spring-boot-postgresql-crud-example)
  * [Prerequisites](#prerequisites)
  * [Project Structure](#project-structure)
  * [Build & Run](#build--run)
  * [API Usage](#api-usage)
    * [User Requests](#user-requests)
    * [Payment Requests](#payment-requests)
  * [Swagger UI](#swagger-ui)
<!-- TOC -->

# Java Spring Boot PostgreSQL CRUD Example

## Prerequisites

* JDK 17 or higher
* Apache Maven 3.9+
* PostgreSQL database

## Project Structure

```
java-basic-crud-example
├── pom.xml
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
        │               │   ├── PaymentController.java
        │               │   └── UserController.java
        │               ├── model
        │               │   ├── Payment.java
        │               │   └── User.java
        │               ├── repository
        │               │   ├── PaymentRepository.java
        │               │   └── UserRepository.java
        │               └── service
        │                   ├── PaymentService.java
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

2. **Build the project**

   ```bash
   mvn clean package
   ```

   A JAR file will be created in `target/` (e.g., `java-basic-crud-example-0.0.1-SNAPSHOT.jar`).

3. **Run the application**

   * Via Maven:

     ```bash
     mvn spring-boot:run
     ```

   * Or by executing the packaged JAR:

     ```bash
     java -jar target/java-basic-crud-example-0.0.1-SNAPSHOT.jar
     ```

   The application starts on port **8080**.

## API Usage

This project provides CRUD REST APIs for `User` and `Payment` entities under the `/users` and `/payments` endpoints.

### User Requests

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

### Payment Requests

* **Create a payment**

  ```bash
  curl -X POST -H "Content-Type: application/json" \
    -d '{"amount":100.50,"description":"Order #123"}' \
    http://localhost:8080/payments/
  ```

* **Get all payments**

  ```bash
  curl http://localhost:8080/payments/
  ```

* **Get a payment by ID**

  ```bash
  curl http://localhost:8080/payments/1
  ```

* **Update a payment**

  ```bash
  curl -X PUT -H "Content-Type: application/json" \
    -d '{"amount":150.75,"description":"Updated order"}' \
    http://localhost:8080/payments/1
  ```

* **Delete a payment**

  ```bash
  curl -X DELETE http://localhost:8080/payments/1
  ```

## Swagger UI

The project already includes the OpenAPI dependency (`springdoc-openapi-starter-webmvc-ui`) configured in `pom.xml`.

1. **(Optional) Customize API info** by annotating `DemoApplication.java`:

   ```java
   @OpenAPIDefinition(
     info = @Info(
       title = "User & Payment CRUD API",
       version = "1.0",
       description = "Spring Boot CRUD example"
     )
   )
   ```

2. **Rebuild and run** the application.

3. **Open Swagger UI** in your browser:

   ```
   http://localhost:8080/swagger-ui/index.html
   ```
