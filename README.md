# Spring Boot Todo API (PostgreSQL + Hibernate + Unit Tests + Quality Checks)

A simple **RESTful API** built with **Spring Boot**, **Hibernate (JPA)**, and **PostgreSQL** to manage a Todo list.  
Supports basic CRUD operations and includes **JUnit 5** + **Mockito** unit tests with >80% coverage.  
Quality checks are enforced with **JaCoCo** (coverage) and **Checkstyle** (code style).

---

## Features
- Create a todo item (title + description)
- Read all todo items or a single item by ID
- Update a todo item by ID
- Delete a todo item by ID
- Unit tests with >80% coverage for `TodoController`
- Quality checks:
  - **JaCoCo**: Enforces minimum 80% line coverage
  - **Checkstyle**: Enforces Google Java Style Guide

---

## Requirements
- Java 17+
- Maven 3.9+
- PostgreSQL (local or remote)

---

## Setup

### 1. Clone the repository
```sh
git clone https://github.com/your-username/todo-app.git
cd todo-app
```

### 2. Create PostgreSQL Database
```sh
psql -U postgres -c "CREATE DATABASE tododb;"
```

### 3. Configure `application.properties`
Edit `src/main/resources/application.properties`:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/tododb
spring.datasource.username=postgres
spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

---

## Build & Run

### Run locally
```sh
mvn spring-boot:run
```

### Test with Maven
```sh
mvn clean test
```

### Run quality checks
```sh
mvn clean verify
```
- Fails if coverage <80%  
- Fails if style violations exist  

---

## API Endpoints

| Method | Endpoint        | Description                 |
|--------|----------------|-----------------------------|
| POST   | `/todos`        | Create a new todo           |
| GET    | `/todos`        | Get all todos               |
| GET    | `/todos/{id}`   | Get todo by ID              |
| PUT    | `/todos/{id}`   | Update todo by ID           |
| DELETE | `/todos/{id}`   | Delete todo by ID           |

---

## Example Requests

### Create Todo
```sh
curl -X POST -H "Content-Type: application/json" \
-d '{"title":"Buy groceries", "description":"Milk, bread"}' \
http://localhost:8080/todos
```

### Get All Todos
```sh
curl http://localhost:8080/todos
```

### Update Todo
```sh
curl -X PUT -H "Content-Type: application/json" \
-d '{"title":"Buy food", "description":"Rice and beans"}' \
http://localhost:8080/todos/1
```

### Delete Todo
```sh
curl -X DELETE http://localhost:8080/todos/1
```

---

## Testing & Coverage

This project uses:
- **JUnit 5** for testing
- **Mockito** for mocking dependencies
- **Spring Boot Test** for test utilities
- **JaCoCo** for coverage reports
- **Checkstyle** for style checks

To run tests with coverage in IntelliJ IDEA:
1. Right-click the project → **Run 'All Tests with Coverage'**
2. Check the coverage report

JaCoCo HTML report is generated at:
```
target/site/jacoco/index.html
```

---

## License
MIT License. See [LICENSE](LICENSE) for details.
