# User Management Service

A REST API for managing users, built with Spring Boot, JPA, and H2.

---

## Tech stack

| Layer        | Technology              |
|-------------|-------------------------|
| Framework   | Spring Boot 2.7         |
| Language    | Java 11+                |
| Data        | Spring Data JPA, H2     |
| Build       | Maven                   |
| Validation  | Bean Validation (JSR 380) |
| Tests       | JUnit 5, Mockito, MockMvc |

---

## Features

- **Full CRUD**: Create, read, update, and delete users
- **Validation**: Request validation (name, email format)
- **Unique email**: Duplicate emails are rejected with 409 Conflict
- **Structured errors**: Global exception handler returns consistent JSON (404, 400, 409, 500)
- **In-memory DB**: H2 with console for development

## Requirements

- Java 17+
- Maven 3.6+

## Run the application

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
.\mvnw.cmd spring-boot:run
```

The API runs at **http://localhost:8080**.  
H2 console: **http://localhost:8080/h2-console** (JDBC URL: `jdbc:h2:mem:userdb`, user: `sa`, password: empty).

## API Endpoints

| Method | Path        | Description        |
|--------|-------------|--------------------|
| GET    | /users      | List all users     |
| GET    | /users/{id} | Get user by id    |
| POST   | /users      | Create a user      |
| PUT    | /users/{id} | Update a user      |
| DELETE | /users/{id} | Delete a user     |

### Examples

**Create user**

```bash
curl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d "{\"name\":\"Alice\",\"email\":\"alice@example.com\"}"
```

**Get all users**

```bash
curl http://localhost:8080/users
```

**Get user by id**

```bash
curl http://localhost:8080/users/1
```

**Update user**

```bash
curl -X PUT http://localhost:8080/users/1 \
  -H "Content-Type: application/json" \
  -d "{\"name\":\"Alice Smith\",\"email\":\"alice@example.com\"}"
```

**Delete user**

```bash
curl -X DELETE http://localhost:8080/users/1
```

## Run tests

```bash
./mvnw test
```

## Project structure

```
src/main/java/com/user/user_management_service/
├── UserManagementServiceApplication.java
├── controller/   # REST API
├── dto/          # Request/response DTOs
├── entity/       # JPA User entity
├── exception/    # Custom exceptions and global handler
├── repository/   # UserRepository
└── service/      # UserService
```

---

## Project link (LinkedIn / portfolio)

After pushing to GitHub, use your repo URL (e.g. `https://github.com/YOUR_USERNAME/user-management-service`) in your LinkedIn project and posts.

- **LINKEDIN.md** – Ready-to-use post text and project description.
- **docs/SCREENSHOTS_GUIDE.md** – Which screenshots to take for the post.
