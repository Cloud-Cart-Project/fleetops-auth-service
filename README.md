# 🔐 CloudCart Auth Service

The Authentication and Authorization service for the CloudCart E-commerce platform. It handles user registration, login, and JWT token issuance.

## 🛠️ Tech Stack
*   **Framework:** Spring Boot 3.4
*   **Security:** Spring Security 6
*   **Database:** PostgreSQL (uses `auth_db`)
*   **Authentication:** Stateless JWT (HS512)
*   **Password Hashing:** BCrypt

## 🎯 Responsibilities
*   **User Registration:** Creates new users with the `CUSTOMER` role by default.
*   **User Login:** Validates credentials and generates a JWT valid for 24 hours.
*   **Role Management:** Supports `CUSTOMER` and `ADMIN` roles. The JWT payload includes the user's role, allowing other services to perform stateless authorization.
*   **Profile Retrieval:** Returns the authenticated user's username.

## 📡 API Endpoints

| Method | Endpoint | Auth Required | Description |
| :--- | :--- | :--- | :--- |
| `POST` | `/auth/register` | No | Register a new user (`username`, `email`, `password`) |
| `POST` | `/auth/login` | No | Authenticate and receive a JWT |
| `GET` | `/auth/me` | Yes (JWT) | Get the current authenticated user's username |

## 🚀 Running Locally

### Prerequisites
*   Java 17+
*   Maven
*   PostgreSQL running locally (with `auth_db` created)

### Environment Variables
You must set the `JWT_SECRET` environment variable (must be at least 32 characters long).

```bash
export JWT_SECRET=your-super-secret-key-minimum-32-chars
mvn spring-boot:run
```

## 🐳 Docker

```bash
docker build -t cloudcart-auth-service:v1.0.0 .
```
