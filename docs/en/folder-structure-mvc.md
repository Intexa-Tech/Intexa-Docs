# Folder structure (MVC)

This document defines a baseline structure to organize projects (mainly backend) using the **MVC** pattern.

The goal is to avoid chaos as the project grows, separate responsibilities, and make maintenance easier.

---

## What is MVC?

MVC stands for:

- **Model:** represents domain data and rules. It defines how information is structured and persisted.
- **View:** presentation layer (UI). In a backend-only project this is often not a UI, but it can mean:
  - templates (server-side rendering)
  - or simply the “response format” (JSON) as a controlled responsibility.
- **Controller:** orchestrates the request: reads input, validates it, calls services/models, and returns a response.

We use MVC in most products because:

- It makes it clear where things belong.
- It reduces coupling.
- It makes testing easier.
- It lets the team scale without stepping on each other.

---

## Example structure (backend)

```text
src/
  controllers/
  models/
  routes/
  services/
  middlewares/
  utils/
  config/
```

---

## What goes in each folder?

## `src/controllers/`

- Endpoint controllers.
- Keep them “thin”:
  - parse request
  - validate (or delegate validation)
  - call `services/`
  - map to response

Avoid putting complex business logic here.

## `src/models/`

- Domain models and/or schemas.
- Typical examples:
  - ORM models (Sequelize/Prisma/Mongoose)
  - domain entities
  - model structural validation (if applicable)

## `src/routes/`

- Route definitions (HTTP) and wiring to controllers.
- Organize the API by module:
  - `users.routes.js`
  - `orders.routes.js`

## `src/services/`

- Business logic.
- Domain rules.
- Coordination between models/repositories/external APIs.

In general:

- A controller calls one or more services.
- A service talks to models and/or integrations.

## `src/middlewares/`

- HTTP middlewares (Express or other frameworks):
  - auth
  - rate limiting
  - error handling
  - pre-validation
  - logging

## `src/utils/`

- Reusable utilities with no strong domain dependency.
- Examples:
  - date helpers
  - sanitization
  - fetch/http wrappers
  - cross-cutting constants

## `src/config/`

- Project configuration:
  - env loading/validation
  - DB config
  - CORS config
  - logging config

---

## Practical rules to keep things clean

- Each file should have **one main responsibility**.
- If a folder grows too much, create submodules:

```text
src/
  modules/
    users/
      users.routes.js
      users.controller.js
      users.service.js
      users.model.js
```

- Keep “domain” (services/models) separate from HTTP (routes/controllers/middlewares).

---

## (Optional) Minimal recommended structure

```text
src/
  app.js
  server.js
  routes/
    index.routes.js
  controllers/
  services/
  models/
  middlewares/
  utils/
  config/
```

---

## Placeholders to customize

- Backend framework: `REPLACE_ME` (Express / Fastify / Nest / etc.)
- ORM/DB: `REPLACE_ME`
- Module convention: `REPLACE_ME` (by folder or by feature)
