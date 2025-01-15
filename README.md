# Spring Boot Microservices Project

## Overview
This project is based on Spring Boot Microservices architecture. It allows users to register and login via an Auth Service through an API Gateway. Depending on their role (ADMIN or USER), users can send requests to the relevant services with a bearer token. The project includes eight services, as detailed below.

## Services
1. **Config Server**: Centralized configuration management for all services.
2. **Eureka Server**: Service registry for service discovery.
3. **API Gateway**: Entry point for all client requests, routing them to the appropriate services.
4. **Auth Service**: Handles user authentication and authorization.
5. **Job Service**: Manages job-related operations.
6. **User Service**: Manages user data and profiles.
7. **Notification Service**: Sends notifications to users.
8. **File Storage**: Manages file upload and storage.

## Key Features
- User registration and login with role-based access (ADMIN or USER)
- Secure communication through bearer token authentication
- Microservices architecture with service discovery and centralized configuration
- API Gateway for routing requests to appropriate services

## Used Dependencies
### Core
- **Spring Framework**: Core framework for building Java applications.
- **Spring Boot**: Simplifies Spring application development.
- **Spring Security**: Secures the application with authentication and authorization.
- **Spring Security JWT**: Implements JWT-based authentication.
- **Spring Web**: Provides web functionalities.

### Microservices
- **Spring Cloud Gateway Server**: API Gateway for routing and filtering requests.
- **Spring Cloud Config Server**: Manages external configurations for distributed systems.
- **Spring Cloud Config Client**: Fetches configurations from the Config Server.

### Service Discovery
- **Netflix Eureka Server**: Service registry for microservices.
- **Netflix Eureka Client**: Registers services with Eureka Server.

### Data
- **Spring Data JPA**: Abstraction over JPA for database interactions.
- **PostgreSQL**: Relational database for data storage.

### Messaging
- **Kafka**: Message broker for asynchronous communication.
- **Redis**: In-memory data store for caching.

### Docker
- **Docker**: Containerization platform for deploying microservices.

### Utilities
- **ModelMapper**: Object mapping library.
- **OpenAPI UI**: Generates API documentation.
- **Lombok**: Reduces boilerplate code.
- **Log4j2**: Logging framework.

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
- **Update User**
  - **POST**: `http://localhost:8080/v1/user/update`
  - **Form Data**:
    ```json
    {
      "request": {
        "id": "string",
        "username": "string",
        "password": "string",
        "userDetails": {
          "firstName": "string",
          "lastName": "string",
          "phoneNumber": "string",
          "country": "string",
          "city": "string",
          "address": "string",
          "postalCode": "string",
          "aboutMe": "string",
          "profilePicture": "string"
        }
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: Authorized User or Admin

### Job Service
- **Create Category**
  - **POST**: `http://localhost:8080/v1/job-service/category/create`
  - **Form Data**:
    ```json
    {
      "request": {
        "name": "string",
        "description": "string"
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: Admin Token

- **Update Category**
  - **POST**: `http://localhost:8080/v1/job-service/category/updateCategory`
  - **Form Data**:
    ```json
    {
      "request": {
        "id": "string",
        "name": "string",
        "description": "string"
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: Admin Token

- **Create Job**
  - **POST**: `http://localhost:8080/v1/job-service/job/create`
  - **Form Data**:
    ```json
    {
      "request": {
        "name": "string",
        "description": "string",
        "categoryId": "string",
        "keys": ["string"]
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: Admin Token

- **Update Job**
  - **POST**: `http://localhost:8080/v1/job-service/job/updateJob`
  - **Form Data**:
    ```json
    {
      "request": {
        "id": "string",
        "name": "string",
        "description": "string",
        "categoryId": "string",
        "keys": ["string"]
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: Admin Token

- **Create Advert**
  - **POST**: `http://localhost:8080/v1/job-service/advert/create`
  - **Form Data**:
    ```json
    {
      "request": {
        "name": "string",
        "description": "string",
        "deliveryTime": 0,
        "price": 0,
        "advertiser": "EMPLOYEE",
        "userId": "string",
        "jobId": "string"
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: User Token

- **Update Advert**
  - **POST**: `http://localhost:8080/v1/job-service/advert/update`
  - **Form Data**:
    ```json
    {
      "request": {
        "id": "string",
        "name": "string",
        "description": "string",
        "deliveryTime": 0,
        "price": 0,
        "status": "OPEN"
      },
      "file": "string"
    }
    ```
  - **Bearer Token**: Authorized User or Admin

- **Make An Offer**
  - **POST**: `http://localhost:8080/v1/job-service/offer/makeAnOffer`
  - **Request Body**:
    ```json
    {
      "userId": "string",
      "advertId": "string",
      "offeredPrice": 0
    }
    ```
  - **Bearer Token**: User Token

- **Update Offer**
  - **POST**: `http://localhost:8080/v1/job-service/offer/update`
  - **Request Body**:
    ```json
    {
      "id": "string",
      "offeredPrice": 0,
      "status": "OPEN"
    }
    ```
  - **Bearer Token**: Authorized User or Admin

## API Endpoints and Request Parameters

### User Service
- **Get User By Id**
  - **GET**: `http://localhost:8080/v1/user/getUserById/{id}`
  - **Bearer Token**: User Token

- **Get User By Email**
  - **GET**: `http://localhost:8080/v1/user/getUserByEmail/{email}`
  - **Bearer Token**: User Token

- **Delete User By Id**
  - **DELETE**: `http://localhost:8080/v1/user/deleteUserById/{id}`
  - **Bearer Token**: Authorized User or Admin

### Job Service
- **Get Category By Id**
  - **GET**: `http://localhost:8080/v1/job-service/category/getCategoryById/{id}`
  - **Bearer Token**: User Token

- **Delete Category By Id**
  - **DELETE**: `http://localhost:8080/v1/job-service/category/deleteCategoryById/{id}`
  - **Bearer Token**: Admin Token

- **Get Job By Id**
  - **GET**: `http://localhost:8080/v1/job-service/job/getJobById/{id}`
  - **Bearer Token**: User Token

- **Get Jobs That Fit Your Needs**
  - **GET**: `http://localhost:8080/v1/job-service/job/getJobsThatFitYourNeeds/{needs}`
  - **Bearer Token**: User Token

- **Delete Job By Id**
  - **DELETE**: `http://localhost:8080/v1/job-service/job/deleteJobById/{id}`
  - **Bearer Token**: Admin Token

- **Get Advert By Id**
  - **GET**: `http://localhost:8080/v1/job-service/advert/getAdvertById/{id}`
  - **Bearer Token**: Authorized User or Admin

- **Get Advert By User Id**
  - **GET**: `http://localhost:8080/v1/job-service/advert/getAdvertByUserId/{id}`
  - **Bearer Token**: User Token

- **Delete Advert By Id**
  - **DELETE**: `http://localhost:8080/v1/job-service/job/deleteAdvertById/{id}`
  - **Bearer Token**: Authorized User or Admin

- **Get Offer By Id**
  - **GET**: `http://localhost:8080/v1/job-service/offer/getOfferById/{id}`
  - **Bearer Token**: User Token

- **Get Offer By User Id**
  - **GET**: `http://localhost:8080/v1/job-service/offer/getOfferByUserId/{id}`
  - **Bearer Token**: User Token

- **Get Offer By Advert Id**
  - **GET**: `http://localhost:8080/v1/job-service/offer/getOfferByAdvertId/{id}`
  - **Bearer Token**: User Token

- **Delete Offer By Id**
  - **DELETE**: `http://localhost:8080/v1/job-service/offer/deleteOfferById/{id}`
  - **Bearer Token**: Authorized User or Admin

### Notification Service
- **Get All Notification By User Id**
  - **GET**: `http://localhost:8080/v1/notification/getAllByUserId/{id}`
  - **Bearer Token**: Authorized User or Admin

### File Storage
- **Download Image to File Storage**
  - **GET**: `http://localhost:8080/v1/file-storage/download/{id}`
  - **Bearer Token**: User Token

## Running the Application
### Local Setup
1. Clone the project:
   ```sh
   git clone https://github.com/devsyx/spring-boot-microservices.git
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
   - Gateway
   - Config Server
   - Auth Service
   - User Service
   - Job Service
   - Notification Service
   - File Storage
5. Access Swagger UI for API documentation:
   ```
   http://localhost:8080/v1/{service-name}/swagger-ui/index.html
   ```
# Video

[Watch the video](MS Lab Demo.mp4)

