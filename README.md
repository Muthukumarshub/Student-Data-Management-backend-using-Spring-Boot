# Student Data Management API

A RESTful API built with Spring Boot for managing student data with basic CRUD operations.

## Overview

This project provides a backend service for managing student information with the following capabilities:
- Create new student records
- Retrieve all students or a specific student by ID
- Update student information
- Delete student records

## Tech Stack

- **Spring Boot**: Framework for creating stand-alone, production-grade Spring-based Applications
- **Spring Data JPA**: Data access layer implementation
- **H2 Database**: In-memory database for development/testing
- **Maven**: Dependency management and build tool
- **Postman**: API testing

## Project Structure

```
.
└── src
    ├── main
    │   ├── java
    │   │   └── com
    │   │       └── sjprogramming
    │   │           └── restapi
    │   │               ├── RestapiApplication.java
    │   │               ├── controller
    │   │               │   └── StudentControler.java
    │   │               ├── entity
    │   │               │   └── Student.java
    │   │               └── repository
    │   │                   └── StudentRepository.java
    │   └── resources
    │       └── application.properties
    └── test
        └── java
            └── com
                └── sjprogramming
                    └── restapi
                        └── RestapiApplicationTests.java
```

## Getting Started

### Prerequisites
- Java 8 or higher
- Maven 3.6 or higher

### Setup & Run
1. Clone the repository
   ```
   git clone (https://github.com/Muthukumarshub/Student-Data-Management-backend-using-Spring-Boot).git
   cd student-data-management
   ```

2. Build the project
   ```
   mvn clean install
   ```

3. Run the application
   ```
   mvn spring-boot:run
   ```

4. The application will start running at `http://localhost:8080`

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/api/v1/students` | Get all students |
| GET    | `/students/{id}` | Get student by ID |
| POST   | `/student/add` | Create a new student |
| PUT    | `/student/update/{id}` | Update student by ID |
| DELETE | `/student/delete/{id}` | Delete student by ID |

## H2 Database Access

The application uses H2 in-memory database for development. You can access the H2 console at:

```
URL: http://localhost:8080/h2-console
JDBC URL: jdbc:h2:mem:testdb (or as configured in application.properties)
Username: root
Password: root
```

## API Testing with Postman

### GET All Students
Send a GET request to `http://localhost:8080/api/v1/students` to retrieve all student records.


### GET Student by ID
Send a GET request to `http://localhost:8080/students/{id}` replacing `{id}` with the student ID.
![Screenshot 2025-05-13 125552](https://github.com/user-attachments/assets/cb93fb70-8204-4037-84c0-6178958040fc)


### POST Create New Student
Send a POST request to `http://localhost:8080/student/add` with a JSON body:

```json
{
    "name": "John Doe",
    "percentage": 85
}
```
![image](https://github.com/user-attachments/assets/e3069dd5-48dc-4f4a-89c3-d4d6441ff5ac)


### PUT Update Student
Send a PUT request to `http://localhost:8080/student/update/{id}` replacing `{id}` with the student ID.
![Screenshot 2025-05-13 130030](https://github.com/user-attachments/assets/9a1aacc6-2dc8-48f8-aa5e-219c031c1540)


### DELETE Student
Send a DELETE request to `http://localhost:8080/student/delete/{id}` replacing `{id}` with the student ID.

![image](https://github.com/user-attachments/assets/d999785c-53e5-437a-ad9d-5449d7dbc61d)

## Entity Structure

```java
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private float percentage;
    
    // Getters and setters
}
```

## Application Properties

Make sure your `application.properties` contains appropriate configurations for H2 database:

```properties
# H2 Database Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect

# Enable H2 Console
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# JPA Configuration
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
```

