# Security best practices

Simple, mandatory rules to avoid incidents.

---

## Rules (critical)

- **❌ Never commit `.env` files**.
- **❌ Never commit keys / tokens / credentials** (API keys, JWT secrets, passwords, private keys, service accounts, etc.).
- **✔ Use environment variables** for any sensitive configuration.
- **✔ Validate inputs** (body, params, query) before processing.
- **✔ Handle errors with `try/catch`** (or a centralized error middleware) to avoid crashes and information leaks.

---

## Environment variables

- Any secret must only exist in:
  - system/CI environment variables
  - a secret manager (recommended)

### Checklist

- The repo includes an example file:
  - `REPLACE_ME` (e.g. `.env.example`) with variable **names**, but **no real values**.
- Variables are validated at app startup:
  - `REPLACE_ME` (e.g. `zod`, `envalid`, manual validation)

---

## Input validation

Always validate:

- `req.body`
- `req.params`
- `req.query`

### Rules

- Reject extra fields if the endpoint doesn’t allow them.
- Validate types, formats, limits (very long strings, ranges, etc.).
- Sanitize when needed (trim, normalization).

### Example (pseudo)

```js
// REPLACE_ME: validation library
function validateCreateUser(input) {
  // validate email, password, etc.
  return input;
}
```

---

## Errors and responses

- Never return stack traces, SQL errors, or internal details to the client.
- Client-facing: clear, generic messages.
- Logs: enough detail to diagnose.

---

## Git hygiene

Add to `.gitignore`:

- `.env`
- `*.key`
- `*.pem`
- `credentials*.json`

---

## Examples of things that must NOT be committed

- AWS keys
- Firebase service account JSON
- JWT secret
- DB password
- API tokens (Stripe, Twilio, etc.)

---

## Placeholders to customize

- Secret manager: `REPLACE_ME` (AWS Secrets Manager / GCP Secret Manager / Vault / etc.)
- Validation library: `REPLACE_ME`
- Logging strategy: `REPLACE_ME`
