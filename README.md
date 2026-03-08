# User Management Service

A REST API for managing users, built with Spring Boot, JPA, and H2.

---

## Tech Stack

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

---

## API Endpoints

| Method | Path        | Description        |
|--------|-------------|--------------------|
| GET    | /users      | List all users     |
| GET    | /users/{id} | Get user by ID     |
| POST   | /users      | Create a user      |
| PUT    | /users/{id} | Update a user      |
| DELETE | /users/{id} | Delete a user      |

---

## API Output Examples

### 1. Create User (POST /users)

**Request:**
```bash
curl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Siva Ganesh","email":"siva@example.com"}'
```

**Response:** `201 Created`
```json
{
  "id": 1,
  "name": "Siva Ganesh",
  "email": "siva@example.com"
}
```

---

### 2. Get All Users (GET /users)

**Request:**
```bash
curl http://localhost:8080/users
```

**Response:** `200 OK`
```json
[
  {
    "id": 1,
    "name": "Siva Ganesh",
    "email": "siva@example.com"
  },
  {
    "id": 2,
    "name": "John Doe",
    "email": "john@example.com"
  }
]
```

---

### 3. Get User by ID (GET /users/1)

**Request:**
```bash
curl http://localhost:8080/users/1
```

**Response:** `200 OK`
```json
{
  "id": 1,
  "name": "Siva Ganesh",
  "email": "siva@example.com"
}
```

---

### 4. Update User (PUT /users/1)

**Request:**
```bash
curl -X PUT http://localhost:8080/users/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Siva Ganesh (Updated)","email":"siva@example.com"}'
```

**Response:** `200 OK`
```json
{
  "id": 1,
  "name": "Siva Ganesh (Updated)",
  "email": "siva@example.com"
}
```

---

### 5. Delete User (DELETE /users/1)

**Request:**
```bash
curl -X DELETE http://localhost:8080/users/1
```

**Response:** `204 No Content`

---

## Error Handling Examples

### User Not Found (404)

**Request:**
```bash
curl http://localhost:8080/users/999
```

**Response:** `404 Not Found`
```json
{
  "status": 404,
  "message": "User not found with id: 999",
  "timestamp": "2026-03-08T19:18:38.709335"
}
```

---

### Duplicate Email (409 Conflict)

**Request:**
```bash
curl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Another User","email":"siva@example.com"}'
```

**Response:** `409 Conflict`
```json
{
  "status": 409,
  "message": "Email already exists: siva@example.com",
  "timestamp": "2026-03-08T19:18:30.794143"
}
```

---

### Validation Error (400 Bad Request)

**Request:**
```bash
curl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Test","email":"invalid-email"}'
```

**Response:** `400 Bad Request`
```json
{
  "status": 400,
  "message": "Validation failed",
  "errors": [
    "email: Email must be a valid email address"
  ]
}
```

---

## Run the Application

```bash
./mvnw spring-boot:run
```

The API runs at **http://localhost:8080**

H2 Console: **http://localhost:8080/h2-console**
- JDBC URL: `jdbc:h2:mem:userdb`
- Username: `sa`
- Password: (empty)

---

## Run Tests

```bash
./mvnw test
```

**Output:**
```
Tests run: 19, Failures: 0, Errors: 0, Skipped: 0
BUILD SUCCESS
```

---

## Project Structure

```
src/main/java/com/user/user_management_service/
├── UserManagementServiceApplication.java    # Main application
├── controller/
│   └── UserController.java                  # REST endpoints
├── service/
│   └── UserService.java                     # Business logic
├── repository/
│   └── UserRepository.java                  # Database access
├── entity/
│   └── User.java                            # JPA entity
├── dto/
│   ├── UserRequest.java                     # Input validation
│   ├── UserResponse.java                    # API response
│   └── ErrorResponse.java                   # Error format
└── exception/
    ├── UserNotFoundException.java           # 404 errors
    ├── DuplicateEmailException.java         # 409 conflicts
    └── GlobalExceptionHandler.java          # Central error handling
```

---

## Author

**Siva Ganesh** - [GitHub Profile](https://github.com/sivaganesh1407)

---

## License

This project is licensed under the MIT License.
