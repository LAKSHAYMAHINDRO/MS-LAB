# Spring Boot Microservices Project

## Overview
This project is based on Spring Boot Microservices architecture. It allows users to register and login via an Auth Service through an API Gateway. Depending on their role (ADMIN or USER), users can send requests to the relevant services with a bearer token. The project includes five key services that are communicating with each other, as detailed below. 

## Services
1. **Eureka Server**: Service registry for service discovery.
2. **Config Server**: Responsible for managing centralized configuration for other microservices.
3. **API Gateway**: Entry point for all client requests, routing them to the appropriate services.
4. **Auth Service**: Handles user authentication and authorization.
5. **User Service**: Manages user data and profiles.
6. **File Storage**: Manages file upload and storage.

## Key Features
- User registration and login with role-based access (ADMIN or USER)
- Secure communication through bearer token authentication
- Microservices architecture with centralized configuration

## Used Dependencies
### Core
- **Spring Framework**: Core framework for building Java applications.
- **Spring Boot**: Simplifies Spring application development.
- **Spring Security**: Secures the application with authentication and authorization.
- **Spring Security JWT**: Implements JWT-based authentication.
- **Spring Web**: Provides web functionalities.

### Service Discovery
- **Netflix Eureka Server**: Service registry for microservices.
- **Netflix Eureka Client**: Registers services with Eureka Server.

### Utilities
- **ModelMapper**: Object mapping library.
- **OpenAPI UI**: Generates API documentation.
- **Lombok**: Reduces boilerplate code.
- **Log4j2**: Logging framework.

### Data
- **Spring Data JPA**: Abstraction over JPA for database interactions.
- **PostgreSQL**: Relational database for data storage.

### Validation
- **Spring Validation**: Validates user input.
- **File Storage**: Manages file uploads and storage operations.

## API Endpoints and Request Bodies

### Auth Service
- **Register for User**
  - **POST**: `http://localhost:8080/v1/auth/register`
  - **Request Body**:
    ```json
    {
      "username": "string",
      "password": "string",
      "email": "string"
    }
    ```

- **Login for User and Admin**
  - **POST**: `http://localhost:8080/v1/auth/login`
  - **Request Body**:
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```

### User Service
- **Get User By Id**
  - **GET**: `http://localhost:8080/v1/user/getUserById/{id}`
  - **Bearer Token**: User Token

- **Get User By Email**
  - **GET**: `http://localhost:8080/v1/user/getUserByEmail/{email}`
  - **Bearer Token**: User Token

### File Storage
- **Upload File**
  - **POST**: `http://localhost:8080/v1/file-storage/upload`
  - **Form Data**:
    ```json
    {
      "file": "string"
    }
    ```
  - **Bearer Token**: User Token

- **Download Image to File Storage**
  - **GET**: `http://localhost:8080/v1/file-storage/download/{id}`
  - **Bearer Token**: User Token

## Running the Application
### Local Setup
1. Clone the project:
   ```sh
   git clone https://github.com/LAKSHAYMAHINDRO/MS-LAB.git
   ```
2. Navigate to the project directory:
   ```sh
   cd spring-boot-microservices
   ```
3. Run Docker Compose:
   ```sh
   docker compose up
   ```
4. Run the following services in order:
   - Eureka Server
   - Config Server
   - Gateway
   - Auth Service
   - User Service
   - File Storage
     

5. Access the Eureka Server dashboard to monitor registered services:
   ```
   http://localhost:8761
   ```

6. Access Swagger UI for API documentation:
   ```
   http://localhost:8080/v1/{service-name}/swagger-ui/index.html
   ```

## Project Demo

Download and watch the demo video [here](videos/video.mp4)

( Google Drive ) [Drive Link](https://drive.google.com/file/d/1HOgalAhYIuper2MG7Y4tIZjk_FXGhhcn/view?usp=sharing).




