# FlowForge

FlowForge is a workflow and process automation engine built with ASP.NET Core.  
It allows users to define workflows (states and transitions) and execute tasks that strictly follow those workflow rules.

The project is designed as a clean, modular monolith using CQRS and Domain-Driven Design principles.  
Its purpose is to demonstrate production-grade backend architecture, containerization, and CI/CD practices.

---

##  Features

- Create and manage workflows
- Define workflow states (initial, intermediate, final)
- Define valid transitions between states
- Create tasks bound to workflows
- Move tasks through valid transitions only
- Track full task state history
- Enforce domain invariants inside aggregates
- Optimistic concurrency handling
- Clean CQRS separation (Commands & Queries)
- Dockerized environment
- CI/CD pipeline with GitHub Actions

---

##  Architecture

FlowForge follows Clean Architecture principles and is structured as a modular monolith.
```
src/
├── FlowForge.Api
├── FlowForge.Application
├── FlowForge.Domain
├── FlowForge.Infrastructure
└── FlowForge.Tests
```

### Layers

**Domain**
- Entities
- Value Objects
- Domain Events
- Business rules & invariants

**Application**
- Commands
- Queries
- Handlers
- DTOs
- Validation

**Infrastructure**
- Entity Framework Core
- MS SQL integration
- Repository implementations
- Migrations
- Logging configuration

**API**
- REST endpoints
- Middleware
- Exception handling
- Swagger / OpenAPI

---

##  Design Principles

- CQRS (Command Query Responsibility Segregation)
- Domain-Driven Design (DDD)
- Aggregates enforce invariants
- Optimistic concurrency via RowVersion
- Separation of concerns
- Infrastructure-independent domain layer

---

##  Technology Stack

### Backend
- .NET 8
- ASP.NET Core Web API
- Entity Framework Core
- MediatR
- FluentValidation
- Serilog
- xUnit
- FluentAssertions

### Database
- Microsoft SQL Server

### DevOps
- Docker
- Docker Compose
- GitHub Actions (CI/CD)

---

## 🐳 Running with Docker

Ensure Docker is installed, then run:
docker-compose up --build


This will start:
- API container
- SQL Server container

The API will be available at:
http://localhost:5000

Swagger UI:
http://localhost:5000/swagger


---

## 🧪 Running Tests

From the root directory:
dotnet test


---

## 🔄 CI/CD Pipeline

The GitHub Actions pipeline performs:

1. Restore dependencies
2. Build solution
3. Run linters
4. Execute unit tests
5. Build Docker image
6. Deploy to test environment

---

## 📌 Roadmap

- Workflow versioning
- Role-based transition permissions
- Task comments & attachments
- Deadlines and escalation logic
- Angular frontend integration

---

## 📄 License

MIT License

Copyright (c) 2026 Šimon Pavlík
