# Testing (basic)

Even if automated tests don’t exist yet, there is a minimum required to avoid shipping broken code.

---

## Rules

- **Every important feature must be tested**.
- **Do not push broken code**.
- **Test endpoints before opening a PR**.

---

## What “test” means

Depending on the project, at least one:

- Manual test in local environment.
- Endpoint testing with Postman/Insomnia/cURL.
- Basic smoke test.

Placeholders:

- API testing tool: `REPLACE_ME` (Postman / Insomnia)
- Staging environment: `REPLACE_ME`

---

## PR checklist

- The project runs locally.
- No console errors.
- Modified endpoints were tested:
  - expected status code
  - expected payload
  - error cases (invalid inputs)
- Existing flows are not broken.

---

## Example (endpoint test)

```bash
# REPLACE_ME: local URL
curl -X POST http://localhost:REPLACE_ME/api/users \
  -H 'Content-Type: application/json' \
  -d '{"email":"test@example.com","password":"REPLACE_ME"}'
```

---

## If we add automated tests later

Recommended:

- Unit tests for `services/` logic.
- Integration tests for critical endpoints.

Framework placeholder:

- `REPLACE_ME` (Jest / Vitest / Mocha)
