# Error handling

This document defines how errors should be handled to keep good UX, stability, and security.

---

## Rules

- **Always return clear messages** to the client.
- **Never expose internal errors** (stack traces, queries, paths, internal names) to the client.
- **Separate logs for development and production**.

---

## Client responses

### What to do

- Simple, actionable messages.
- Correct HTTP status codes.

Examples:

- `400` invalid input
- `401` unauthorized
- `403` forbidden
- `404` not found
- `409` conflict
- `422` validation error
- `500` internal server error

### What NOT to do

- Stack trace
- ORM/DB raw errors
- Infrastructure details

---

## Handling with `try/catch`

Rule:

- Controllers catch expected errors.
- Unexpected errors go to a centralized handler.

Example (pseudo):

```js
async function createUserController(req, res) {
  try {
    const input = req.body;

    // REPLACE_ME: validate
    // REPLACE_ME: service call

    return res.status(201).json({ message: 'User created' });
  } catch (error) {
    // REPLACE_ME: log error (dev/prod)

    return res.status(500).json({
      message: 'Internal server error',
    });
  }
}
```

---

## Logging by environment

- **Development:**
  - more verbose logs
  - may include stack traces

- **Production:**
  - structured logs
  - correlation/request id
  - no secrets
  - no PII (or minimized)

Placeholders:

- Logger: `REPLACE_ME` (console / pino / winston / datadog / etc.)
- Request ID: `REPLACE_ME`

---

## Checklist

- The client always receives an understandable message.
- No internal information is leaked.
- Logging is sufficient for debugging.
- Production logs do not print secrets.
