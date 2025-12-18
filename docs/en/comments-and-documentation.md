# Comments and documentation

Simple rules to keep the repo understandable and easy to maintain.

---

## Comments

- **Comments only when necessary.**
- Avoid obvious comments (“add 1”).
- Useful comments explain **why**, not only **what**.

### When to comment

- Non-obvious decisions.
- Workarounds.
- Complex business rules.
- Complex functions/algorithms.

---

## Documentation

- **Keep the README updated.**
- API endpoints must be well documented.

### Minimum documentation

- How to run the project locally.
- Required environment variables (no secrets).
- Common commands.
- Endpoints (method, route, request, response, errors).

---

## Endpoint documentation (example)

### `POST /api/users`

**Description**

Creates a user.

**Request**

Headers:

- `Content-Type: application/json`

Body:

```json
{
  "email": "user@example.com",
  "password": "REPLACE_ME"
}
```

**Responses**

- `201 Created`

```json
{
  "message": "User created"
}
```

- `400 Bad Request`

```json
{
  "message": "Invalid input"
}
```

---

## Placeholders to customize

- API documentation standard: `REPLACE_ME` (OpenAPI/Swagger / Markdown / Postman collections)
- API docs location: `REPLACE_ME`
