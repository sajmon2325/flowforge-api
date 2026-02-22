# FlowForge

FlowForge is a workflow and process automation engine built with ASP.NET Core.  
It allows users to define workflows (states and transitions) and execute tasks that strictly follow those workflow rules.

The project follows Clean Architecture and CQRS principles with event-driven synchronization between database instances.

---

## 🚀 Features

- Create and manage workflows
- Define workflow states (initial, intermediate, final)
- Define valid transitions between states
- Create tasks bound to workflows
- Move tasks through valid transitions only
- Track full task state history
- Event-driven database synchronization
- Two database instances (write + read)
- RabbitMQ message broker for events
- Outbox pattern for reliable event delivery
- Optimistic concurrency handling
- Dockerized environment
- CI/CD pipeline with GitHub Actions

---

## 🏗 Architecture

FlowForge uses:

✔ Clean Architecture  
✔ CQRS (Command Query Responsibility Segregation)  
✔ Event-driven synchronization  
✔ Two databases  
✔ RabbitMQ for messaging  
✔ Outbox pattern (no event sourcing)

### Database Strategy

| Database | Purpose |
|----------|---------|
| flowforge_write | Source of truth (commands) |
| flowforge_read | Optimized read model (queries) |

Events synchronize read database projections.

---

### Project Structure
```
src/
├── FlowForge.Api
├── FlowForge.Application
├── FlowForge.Domain
├── FlowForge.Infrastructure
├── FlowForge.Messaging
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
- Handlers (MediatR)
- DTOs
- Validation (FluentValidation)

**Infrastructure**
- Entity Framework Core
- Database repositories
- Migrations
- Outbox implementation

**Messaging**
- RabbitMQ integration
- Event publishing
- Event consumers
- Message contracts

**API**
- REST endpoints
- Middleware
- Exception handling
- Swagger / OpenAPI

---

## 🧠 Design Principles

- CQRS for command/query separation
- Event-driven synchronization
- Two database projections
- Outbox pattern for reliable delivery
- Domain-driven business rules
- Clean separation of concerns

---

## 🛠 Technology Stack

### Backend
- .NET 8
- ASP.NET Core Web API
- Entity Framework Core
- MediatR
- FluentValidation
- MassTransit (RabbitMQ)
- Serilog
- xUnit
- FluentAssertions

### Databases
- Microsoft SQL Server (write)
- Microsoft SQL Server (read)

### Messaging
- RabbitMQ
- MassTransit abstraction
- Outbox pattern

### DevOps
- Docker
- Docker Compose
- GitHub Actions (CI/CD)

---

## 🐳 Running with Docker

Ensure Docker is installed, then run:

```bash
docker-compose up --build
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
- Handlers (MediatR)
- DTOs
- Validation (FluentValidation)

**Infrastructure**
- Entity Framework Core
- Database repositories
- Migrations
- Outbox implementation

**Messaging**
- RabbitMQ integration
- Event publishing
- Event consumers
- Message contracts

**API**
- REST endpoints
- Middleware
- Exception handling
- Swagger / OpenAPI

---

## 🧠 Design Principles

- CQRS for command/query separation
- Event-driven synchronization
- Two database projections
- Outbox pattern for reliable delivery
- Domain-driven business rules
- Clean separation of concerns

---

## 🛠 Technology Stack

### Backend
- .NET 8
- ASP.NET Core Web API
- Entity Framework Core
- MediatR
- FluentValidation
- MassTransit (RabbitMQ)
- Serilog
- xUnit
- FluentAssertions

### Databases
- Microsoft SQL Server (write)
- Microsoft SQL Server (read)

### Messaging
- RabbitMQ
- MassTransit abstraction
- Outbox pattern

### DevOps
- Docker
- Docker Compose
- GitHub Actions (CI/CD)

---

## 🐳 Running with Docker

Ensure Docker is installed, then run:

```bash
docker-compose up --build
```

This will start:

API container

Write database

Read database

RabbitMQ broker

The API will be available at:
http://localhost:5000

Swagger UI:
http://localhost:5000/swagger

---

🧪 Running Tests

From the root directory:
```bash
dotnet test
```

---

## 🔄 Event-Driven Synchronization

Database synchronization flow:
```
Command
↓
Write DB (transaction)
↓
Outbox table record
↓
Event published (RabbitMQ)
↓
Read DB projection update
```

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
