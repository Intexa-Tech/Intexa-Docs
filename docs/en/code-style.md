# Code style (JavaScript)

This document defines simple and clear rules to keep code style consistent.

---

## Code language

- All **code** (variable, function, class, constant, file names, etc.) must be in **English**.

---

## Naming conventions

- **Variables:** `camelCase`
- **Functions:** `camelCase`
- **Classes:** `PascalCase`
- **Constants:** `UPPER_SNAKE_CASE`

### Quick rules

- Use descriptive names (avoid abbreviations unless they are domain standards).
- Keep consistency: if something is a class, it must look like a class (`PascalCase`).
- Constants should represent “fixed” module/domain values.

---

## Semicolons

- **Rule:** always use `;`.

If in the future the team decides to *not* use `;`, this document must be updated and the formatter/linter must reflect it.

---

## Examples

```js
const API_BASE_URL = 'https://example.com';

function buildUserProfileUrl(userId) {
  const profileUrl = `${API_BASE_URL}/users/${userId}`;
  return profileUrl;
}

class UserService {
  constructor(httpClient) {
    this.httpClient = httpClient;
  }
}
```

---

## PR checklist

- Code is written in English.
- Variables and functions use `camelCase`.
- Classes use `PascalCase`.
- Constants use `UPPER_SNAKE_CASE`.
- Indentation uses 2 spaces.
- Semicolons `;` are used.
