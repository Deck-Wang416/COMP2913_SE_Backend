# PathPals — Backend API

![golang](https://img.shields.io/badge/Go-00ADD8.svg?style=for-the-badge&logo=Go&logoColor=white)
![gin](https://img.shields.io/badge/Gin-008ECF.svg?style=for-the-badge&logo=Gin&logoColor=white)
![mysql](https://img.shields.io/badge/MySQL-4479A1.svg?style=for-the-badge&logo=MySQL&logoColor=white)
![redis](https://img.shields.io/badge/Redis-DC382D.svg?style=for-the-badge&logo=Redis&logoColor=white)
![rabbitmq](https://img.shields.io/badge/RabbitMQ-FF6600.svg?style=for-the-badge&logo=RabbitMQ&logoColor=white)
![docker](https://img.shields.io/badge/Docker-2496ED.svg?style=for-the-badge&logo=Docker&logoColor=white)

PathPals is a fitness tracking and social sharing platform developed as a team software engineering project. This repository contains its backend API, built with Go and Gin using a layered architecture.

Original team repository: [XJCO2913/API_Backend](https://github.com/XJCO2913/API_Backend).

## Project Structure

<img src="./img/repo_tree.png" alt="Repository directory structure" width="480" />

### 1. `cmd`

Contains the application entry point (`package main`), including the main function, route registration, and initialization of resources required at startup.

### 2. `config`

Contains application and deployment configuration, including database settings, environment variables, JWT settings, and Docker configuration. Sensitive configuration files are excluded from version control.

### 3. `middleware`

Implements shared request processing such as authentication, rate limiting, and request context management before requests reach the controllers.

### 4. `controller`

Handles incoming HTTP requests, validates request parameters, and delegates business operations to the service layer. Controllers also prepare responses for clients.

**DTO (Data Transfer Object)**

DTOs represent structured request data. For example, a JSON request such as:

```json
{
    "id": 1,
    "name": "Alex",
    "age": 20
}
```

can be represented by a Go struct:

```go
type UserReq struct {
    ID   int    `json:"id"`
    Name string `json:"name"`
    Age  int    `json:"age"`
}
```

### 5. `service`

Contains the core business logic. Services receive structured data from controllers, perform business operations, and pass the corresponding models to the data access layer.

**SDTO (Service Data Transfer Object)**

SDTOs transfer data between controllers and services, whereas request DTOs represent data received at the HTTP boundary.

### 6. `dao`

The data access object layer encapsulates database operations and separates persistence logic from business logic. Parts of this layer were generated using the framework's scaffolding tools.

### 7. `util`

Contains reusable utility functions shared across the application.

## Architecture

<img src="./img/layer.jpg" alt="Interaction between application layers" width="640" />
