# Spring Boot Microservices Project
(Eureka Server, Config Server, API Gateway, Kafka, File Storage, JWT, Authentication, Authorization, Redis, Docker)
# About the project
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

## Getting Started
1. Clone the repository.
2. Configure the services in `application.yml` files.
3. Run `docker-compose up` to start all services.
4. Access the application through the API Gateway.

## Contributions
Contributions are welcome. Please fork the repository and create a pull request with your changes.

## License
This project is licensed under the MIT License.

