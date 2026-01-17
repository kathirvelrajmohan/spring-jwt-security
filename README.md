# 🔐 Spring Boot JWT Implementation

A simple, clean JWT authentication implementation with Spring Boot and Spring Security. This project demonstrates the fundamentals of JWT-based authentication for learning purposes.

## 🎯 What I Built

A complete JWT authentication system with:
- ✅ User registration
- ✅ User login with JWT generation
- ✅ Protected endpoints with token validation
- ✅ Role-based access (USER/ADMIN)
- ✅ Database persistence with PostgreSQL

## 🚀 Quick Start

### Prerequisites
- Java 17
- Maven
- PostgreSQL

### Setup & Run
1. Clone and navigate to project
2. Create PostgreSQL database: `jwt_security_db`
3. Update database credentials in `application.properties`
4. Run: `mvn spring-boot:run`

## 📡 API Endpoints

### Public Endpoints (No Auth Required)

#### 1. Register
```http
POST http://localhost:8080/api/v1/auth/register
Content-Type: application/json

{
    "firstname": "John",
    "lastname": "Doe",
    "email": "john@example.com",
    "password": "password123"
}
```

#### 2. Login

```
POST http://localhost:8080/api/v1/auth/authenticate
Content-Type: application/json

{
    "email": "john@example.com",
    "password": "password123"
}
```
Returns: ``` { "token": "eyJhbGciOiJIUzI1NiIs..." } ```

### Protected Endpoints (Requires JWT Token)
Add header to all requests:

```
Authorization: Bearer your-jwt-token-here
```

## 🏗️ Project Structure
```
src/main/java/com/jwtsecurity/jwt_security/
├── auth/           # Authentication controllers & services
├── config/         # Security configuration & JWT handling
├── user/           # User entity & repository
└── repository/     # Database repositories
```

## 🔧 Key Components

1. SecurityConfiguration - Configures Spring Security with JWT filter
2. JwtAuthenticationFilter - Validates JWT tokens on each request
3. JwtService - Creates and validates JWT tokens
4. AuthenticationService - Handles registration and login logic
5. User - Entity implementing Spring Security's UserDetails

## 📚 What I Learned

- ✅ JWT token generation and validation
- ✅ Spring Security filter chain configuration
- ✅ Stateless authentication vs traditional sessions
- ✅ Role-based authorization implementation
- ✅ Password encryption with BCrypt
- ✅ Custom authentication filters

## 🧪 Testing with Postman

- Register a user
- Login to get JWT token
- Use token to access protected endpoints
- Try accessing without token → 401 Unauthorized

## 🔐 Security Features Implemented

- Password hashing with BCrypt
- JWT token expiration (24 hours)
- Secure secret key for token signing
- Role-based endpoint protection
- CSRF disabled for API endpoints
- Stateless session management
