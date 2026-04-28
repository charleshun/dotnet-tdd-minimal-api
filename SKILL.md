---
name: dotnet-minimal-api-tdd
description: Use this skill when working on C# Minimal APIs with .NET 10 using strict Test Driven Development. Apply a red-green-refactor loop, create tests first, keep endpoints thin, use route groups, validate contracts, and run tests after each small change.
---

# .NET 10 Minimal API TDD Skill

You are an expert in C# Minimal APIs on .NET 10 with Test Driven Development.

## C# Minimal API Standards

- Before implementing .NET 10 functionality, fetch the relevant docs from the URL: https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-10/overview
- Use ASP.NET Core Minimal APIs (.NET 10).
- Structure: Program.cs → Endpoints → Models/DTOs → Services.
- Controllers: MapGroup("/api/v1") for versioning.
- DTOs: Records with validation attributes ([Required], [JsonPropertyName]).
- DB: Dapper with PostgreSQL with init-sql script.
- Error handling: ProblemDetails middleware.
- CORS: Allow frontend origin explicitly.

## Code Style
- Async/await everywhere.
- Dependency Injection: IServices scoped.
- Swagger: AddEndpointsApiExplorer + SwaggerUI.

## Goals
- Work in very small increments.
- Always start with a failing test.
- Prefer clean, production-grade Minimal API structure.
- Keep Program.cs thin.
- Organize endpoints by feature.
- Use route groups where appropriate.
- Add integration tests for HTTP behavior and unit tests for business logic.
- Refactor only after tests pass.

## Default workflow
1. Understand the requested endpoint or behavior.
2. Propose the next smallest user-visible behavior.
3. Write the failing test first.
4. Run tests.
5. Implement the minimum code to pass.
6. Run tests again.
7. Refactor carefully.
8. Repeat.

## Project conventions
- Target .NET 10.
- Use Minimal API style.
- Prefer feature folders.
- Put business logic outside endpoint mapping code.
- Use DTOs for contracts.
- Return typed or explicit HTTP results when clarity helps.
- Add validation and unhappy-path tests.

## Testing conventions
- Integration tests for:
  - route registration
  - HTTP status codes
  - request/response payloads
  - validation failures
- Unit tests for:
  - domain rules
  - services
  - mappers
- For every new endpoint:
  - one happy-path test
  - one validation or not-found test
  - one edge-case test if relevant

## Behavior rules
- Never write implementation before the failing test exists unless the user explicitly asks otherwise.
- Keep each iteration small.
- After each step, explain what changed and what test should be run next.
- If the project structure is missing, scaffold the minimum viable layout first.

## Full-Stack Communication
- Frontend API calls: axios/fetch to /api/v1 endpoints.
- DTOs: Shared TypeScript types from C# records (use NSwag/Swagger-codegen).
- Error handling: Axios interceptors for 4xx/5xx → toast notifications.
- Auth flow: Login → JWT token → localStorage → axios headers.
- Real-time: SignalR hubs if needed.

## Suggested repo layout
- src/Api
- src/Application
- tests/Api.Tests
- tests/Application.Tests

## If asked to scaffold
Create:
- solution file
- web project
- test projects
- initial health endpoint
- first integration test

