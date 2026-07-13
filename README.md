# Tracer Asset Management

**A modern, full-stack IT asset management platform for tracking hardware, software licenses, accessories, components, requests, and user assignments across an organization.** Tracer combines a clean Angular workspace with a hardened .NET 9 API, SQL Server persistence, Redis-backed infrastructure, background processing, and Docker-first deployment.

[![.NET](https://img.shields.io/badge/.NET-9.0-512BD4?logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/) [![Angular](https://img.shields.io/badge/Angular-22-DD0031?logo=angular&logoColor=white)](https://angular.dev/) [![TypeScript](https://img.shields.io/badge/TypeScript-6.0-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/) [![SQL Server](https://img.shields.io/badge/SQL%20Server-2022-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/sql-server) [![Redis](https://img.shields.io/badge/Redis-Alpine-DC382D?logo=redis&logoColor=white)](https://redis.io/) [![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)](https://www.docker.com/) [![Tests](https://img.shields.io/badge/Tests-xUnit%20%7C%20Vitest%20%7C%20k6-brightgreen)](#-testing)

## Why this project?

IT teams need a reliable way to know **what assets exist, who has them, where they are, what they cost, and what needs approval**. Tracer is designed as an enterprise-ready asset management backbone: it models the real lifecycle of assets, licenses, consumables, components, requests, notifications, depreciation, settings, and role-based permissions while keeping local setup approachable through Docker Compose.

## Novelty / Key Features

Tracer is not just a CRUD demo. It uses a layered, domain-oriented backend with vertical application slices, an Angular Material SPA, permission-aware UI rendering, JWT authentication, health checks, background jobs, structured logging, and production-style containerization.


- Clean Architecture-style .NET solution: `Domain`, `Application`, `Persistence`, `Infrastructure`, `Api`, and `Shared` layers.


- Enterprise asset workflows: check-out/check-in, assigned items, request approvals, inventory, licenses, depreciation, notifications, and tenant settings.


- Hardened API surface: JWT auth, RBAC policies, rate limiting, output caching, response compression, security headers, correlation IDs, and global exception handling.


- Dockerized stack with API, Angular web app, SQL Server, Redis, and Seq observability.


- Developer-friendly hot reload profile for both .NET and Angular.

## ✨ Features

### Asset & inventory operations


- Asset registration, update, delete, search, pagination, sorting, and lifecycle transitions.


- Check-out/check-in workflows for assigned assets.


- Inventory modules for accessories, components, consumables, and software licenses.


- Master data management for categories, manufacturers, suppliers, locations, departments, companies, status labels, and asset models.


- Depreciation modeling and financial reporting jobs.

### People, approvals & permissions


- JWT login, refresh token, and current-user endpoints.


- User and role management.


- Permission-gated API policies and Angular UI elements.


- Request workflows for “my requests”, approval queues, return requests, and request catalogs.


- “My items” views for assets, consumables, components, accessories, and licenses assigned to the active user.

### Reliability & operations


- EF Core SQL Server persistence with optional automatic migrations.


- Hangfire background processing and local dashboard.


- SQL Server and Redis readiness health checks.


- Serilog structured logs with Seq support.


- k6 smoke and load test scripts for API performance validation.


- Docker Compose deployment script with local service URLs and default seeded login.

## 🛠 Tech Stack

### Frontend

![Angular](https://img.shields.io/badge/Angular-22-DD0031?logo=angular&logoColor=white) ![Angular Material](https://img.shields.io/badge/Angular%20Material-22-757575?logo=angular&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-6.0-3178C6?logo=typescript&logoColor=white) ![RxJS](https://img.shields.io/badge/RxJS-7.8-B7178C?logo=reactivex&logoColor=white) ![SCSS](https://img.shields.io/badge/SCSS-styles-CC6699?logo=sass&logoColor=white)

- Angular standalone components, lazy routes, Angular Material UI, reactive forms, route guards, signals, and HTTP services.

### Backend

![.NET](https://img.shields.io/badge/.NET-9.0-512BD4?logo=dotnet&logoColor=white) ![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-Web%20API-512BD4?logo=dotnet&logoColor=white) ![EF Core](https://img.shields.io/badge/EF%20Core-9.0-512BD4?logo=dotnet&logoColor=white) ![MediatR](https://img.shields.io/badge/MediatR-12.4-blue) ![FluentValidation](https://img.shields.io/badge/FluentValidation-11.10-blue) ![Hangfire](https://img.shields.io/badge/Hangfire-1.8-orange)

- ASP.NET Core Web API, MediatR command/query handlers, FluentValidation pipeline behavior, EF Core migrations, Hangfire jobs, Swagger/OpenAPI, health checks, and rate limiting.

### Database & cache

![SQL Server](https://img.shields.io/badge/SQL%20Server-2022-CC2927?logo=microsoftsqlserver&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-Alpine-DC382D?logo=redis&logoColor=white)

- SQL Server stores operational data and Hangfire jobs; Redis is configured for cache/rate-limit-adjacent infrastructure and readiness monitoring.

### Authentication & authorization

![JWT](https://img.shields.io/badge/JWT-Bearer-000000?logo=jsonwebtokens&logoColor=white) ![BCrypt](https://img.shields.io/badge/BCrypt-passwords-yellowgreen)

- JWT bearer authentication, refresh tokens, BCrypt password hashing, permission constants, API authorization policies, and Angular permission guards/directives.

### Cloud / DevOps / Observability

![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-SPA%20hosting-009639?logo=nginx&logoColor=white) ![Seq](https://img.shields.io/badge/Seq-structured%20logs-5341ff) ![Serilog](https://img.shields.io/badge/Serilog-logging-2D3748)

- Multi-stage Dockerfiles for API and web app, Docker Compose services, Nginx static hosting for Angular, Seq log sink support, health checks, resource limits, and deployment helper script.

### Testing

![xUnit](https://img.shields.io/badge/xUnit-.NET%20unit%20tests-brightgreen) ![FluentAssertions](https://img.shields.io/badge/FluentAssertions-7.0-brightgreen) ![Moq](https://img.shields.io/badge/Moq-4.20-brightgreen) ![Vitest](https://img.shields.io/badge/Vitest-4.0-6E9F18?logo=vitest&logoColor=white) ![k6](https://img.shields.io/badge/k6-load%20tests-7D64FF?logo=k6&logoColor=white)

## 📂 Project Structure

```
.    
├── Tracer.sln                         \\\# Visual Studio/.NET solution    
├── Directory.Build.props              \\\# Shared .NET build settings: net9.0, nullable, warnings as errors    
├── global.json                        \\\# .NET SDK pin/roll-forward policy    
├── docker-compose.yml                 \\\# Full local stack: API, web, SQL Server, Redis, Seq    
├── docker-compose.dev.yml             \\\# Hot-reload overlay for API and Angular    
├── migrations.sql                     \\\# Database migration/support SQL    
├── package.json                       \\\# Root npm dependency metadata    
├── scripts/    
│   └── deploy-docker.sh               \\\# One-command Docker Compose deployment helper    
├── src/    
│   ├── Tracer.Api/                    \\\# ASP.NET Core API, middleware, controllers, Hangfire, health checks    
│   ├── Tracer.Application/            \\\# Use cases, commands/queries, validation, interfaces, DTOs    
│   ├── Tracer.Domain/                 \\\# Aggregates, entities, value objects, domain events, domain errors    
│   ├── Tracer.Infrastructure/         \\\# Auth, external services, caching/infrastructure registrations    
│   ├── Tracer.Persistence/            \\\# EF Core DbContext, configurations, repositories, migrations, seed data    
│   ├── Tracer.Shared/                 \\\# Cross-cutting shared contracts and authorization constants    
│   └── Tracer.Web/                    \\\# Angular 22 SPA, Material UI, routes, features, services, Docker/Nginx config    
└── tests/    
    ├── Tracer.Application.UnitTests/   \\\# Application-layer xUnit tests    
    ├── Tracer.Domain.UnitTests/        \\\# Domain model xUnit tests    
    └── k6/                            \\\# Smoke/load tests for API workflows
```

## 🚀 Getting Started

### Prerequisites

- [.NET SDK 9](https://dotnet.microsoft.com/download)

- [Node.js 22+](https://nodejs.org/) and npm

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) or Docker Engine with Compose

- Optional: `k6` for load tests

### Installation

```
\\\# clone    
git clone \\\<your-repository-url\\\>    
cd ASSET-MANAGEMENT    
    
\\\# restore backend dependencies    
dotnet restore Tracer.sln    
    
\\\# install frontend dependencies    
cd src/Tracer.Web    
npm ci    
cd ../..    
    
\\\# configure environment    
\\\# Option A: use Docker Compose defaults from docker-compose.yml    
\\\# Option B: override appsettings or environment variables listed below    
    
\\\# run locally with the complete container stack    
docker compose up -d --build
```

Open the services:

| Service | URL |
| - | - |
| Angular UI | [http://localhost:4200](http://localhost:4200/) |
| API | [http://localhost:5001](http://localhost:5001/) |
| Swagger UI | [http://localhost:5001/swagger](http://localhost:5001/swagger) |
| Health live | [http://localhost:5001/health/live](http://localhost:5001/health/live) |
| Health ready | [http://localhost:5001/health/ready](http://localhost:5001/health/ready) |
| Hangfire dashboard | [http://localhost:5001/hangfire](http://localhost:5001/hangfire) |
| Seq logs | [http://localhost:8081](http://localhost:8081/) |


Default development login seeded by the Docker helper:

```
Email:    admin@tracer.io    
Password: Admin123!
```

### Development hot reload

```
\\\# API + web hot reload via Compose overlay    
docker compose -f docker-compose.yml -f docker-compose.dev.yml up --build
```

Or run each layer manually:

```
\\\# terminal 1: API    
dotnet run --project src/Tracer.Api/Tracer.Api.csproj    
    
\\\# terminal 2: Angular    
cd src/Tracer.Web    
npm run start
```

## ⚙️ Configuration

### Primary environment variables

| Variable / key | Purpose | Default/example |
| - | - | - |
| `ASPNETCORE\\\_ENVIRONMENT` | Runtime environment | `Development` |
| `ASPNETCORE\\\_URLS` | API bind URL inside container | `http://+:8080` |
| `RUN\\\_MIGRATIONS` | Apply EF Core migrations at startup | `true` in Compose |
| `ConnectionStrings\\\_\\\_DefaultConnection` | SQL Server connection string | `Server=sql-server;Database=TracerDb;...` |
| `ConnectionStrings\\\_\\\_Redis` | Redis connection string | `redis:6379` |
| `Cors\\\_\\\_Origins\\\_\\\_0..n` | Allowed SPA origins | `http://localhost:4200`, `http://tracer-web` |
| `JwtSettings\\\_\\\_Secret` | JWT signing secret | Local-only value in `appsettings.Development.json` |
| `JwtSettings\\\_\\\_Issuer` | JWT issuer | `TracerApi` |
| `JwtSettings\\\_\\\_Audience` | JWT audience | `TracerClient` |
| `JwtSettings\\\_\\\_AccessTokenExpirationMinutes` | Access token lifetime | `15` |
| `JwtSettings\\\_\\\_RefreshTokenExpirationDays` | Refresh token lifetime | `7` |
| `NotificationSettings\\\_\\\_Slack\\\_\\\_WebhookUrl` | Slack notification webhook | empty by default |
| `NotificationSettings\\\_\\\_Teams\\\_\\\_WebhookUrl` | Teams notification webhook | empty by default |
| `NotificationSettings\\\_\\\_Email\\\_\\\_Host` | SMTP host | empty by default |
| `Serilog\\\_\\\_WriteTo\\\_\\\_0\\\_\\\_Args\\\_\\\_configure\\\_\\\_0\\\_\\\_Args\\\_\\\_serverUrl` | Seq endpoint | `http://seq:5341` |
| `DOTNET\\\_USE\\\_POLLING\\\_FILE\\\_WATCHER` | Hot reload support in containers | `1` |
| `CHOKIDAR\\\_USEPOLLING` | Angular file watching in containers | `true` |


> Never commit production secrets. Use environment variables, Docker secrets, or your deployment platform’s secret store for real credentials.

## 📜 Scripts & Commands

### Root

| Command | Description |
| - | - |
| `dotnet restore Tracer.sln` | Restore all .NET projects. |
| `dotnet build Tracer.sln` | Build API, domain, application, persistence, infrastructure, shared, and tests. |
| `dotnet test Tracer.sln` | Run xUnit test projects. |
| `docker compose up -d --build` | Build and run the full production-like local stack. |
| `docker compose -f docker-compose.yml -f docker-compose.dev.yml up --build` | Run the stack with API/Angular hot reload. |
| `./scripts/deploy-docker.sh` | Build, start, wait for API health, and print useful URLs. |


### Frontend (`src/Tracer.Web/package.json`)

| npm script | Description |
| - | - |
| `npm run ng` | Run Angular CLI. |
| `npm run start` | Serve the Angular app locally. |
| `npm run start:docker` | Serve Angular in Docker on `0.0.0.0:4200` with proxy config and polling. |
| `npm run build` | Build the Angular application. |
| `npm run watch` | Build Angular in watch mode using development configuration. |
| `npm run test` | Run Angular unit tests through the configured Angular test builder. |


## 🧪 Testing

```
\\\# .NET unit tests    
dotnet test Tracer.sln    
    
\\\# Angular unit tests    
cd src/Tracer.Web    
npm run test    
    
\\\# k6 smoke/load tests, with the stack already running    
k6 run tests/k6/smoke-test.js    
k6 run tests/k6/load-test-assets.js    
k6 run tests/k6/load-test-notifications.js
```

## 🚢 Deployment

### Docker Compose

The repository ships with a Docker-first deployment path:

```
./scripts/deploy-docker.sh
```

This starts:

- `tracer-api` — ASP.NET Core API on host port `5001`.

- `tracer-web` — Angular/Nginx web app on host port `4200`.

- `sql-server` — SQL Server 2022 on host port `1433`.

- `redis` — Redis on host port `6379`.

- `seq` — Seq ingestion/UI on ports `5341` and `8081`.

### Production notes

- Replace Compose sample passwords and JWT secrets before deployment.

- Move SQL Server and Redis to managed services for production workloads when possible.

- Keep `RUN\\\_MIGRATIONS` deliberate in production; run migrations in CI/CD if your release process requires approvals.

- Expose the API behind HTTPS and configure CORS for your production web origin.

- Consider securing or disabling the Hangfire dashboard outside local/admin networks.

## 🔌 API Overview

The API is versioned under `/api/v1` and includes resource areas such as:

- `/auth` — login, token refresh, current user.

- `/assets` — asset list, details, create/update/delete, check-out/check-in.

- `/requests` — user requests, catalogs, approvals, rejections.

- `/users` and `/me/assigned-items` — user administration and assignment visibility.

- `/accessories`, `/components`, `/consumables`, `/licenses` — inventory resources.

- `/categories`, `/manufacturers`, `/suppliers`, `/locations`, `/departments`, `/companies`, `/status-labels`, `/asset-models` — master data.

- `/settings` — tenant and integration settings.

Swagger is enabled in Development at [http://localhost:5001/swagger](http://localhost:5001/swagger).

## 🧭 Architecture

```
graph TD    
  Web\\\[Angular Material SPA\\\] --\\\>|HTTP /api/v1| Api\\\[ASP.NET Core API\\\]    
  Api --\\\> App\\\[Application: commands, queries, validation\\\]    
  App --\\\> Domain\\\[Domain: aggregates, entities, events\\\]    
  App --\\\> Persistence\\\[Persistence: EF Core + SQL Server\\\]    
  Api --\\\> Infrastructure\\\[Infrastructure: auth/cache/services\\\]    
  Api --\\\> Hangfire\\\[Hangfire background jobs\\\]    
  Persistence --\\\> Sql\\\[(SQL Server)\\\]    
  Infrastructure --\\\> Redis\\\[(Redis)\\\]    
  Api --\\\> Seq\\\[Seq / Serilog\\\]
```

## 🤝 Contributing

1. Create a feature branch.

2. Keep changes aligned with the layered architecture.

3. Add or update unit tests for business logic.

4. Run `dotnet test Tracer.sln` and frontend checks before opening a pull request.

5. Avoid committing generated build outputs, local secrets, or container volumes.

## 📝 License

No license file is currently included. Add a `LICENSE` file before publishing or distributing this project.

