# Estilo de código (JavaScript)

Este documento define reglas simples y claras para mantener un estilo consistente en el código.

---

## Idioma del código

- Todo el **código** (nombres de variables, funciones, clases, constantes, archivos, etc.) debe estar en **inglés**.

---

## Convenciones de nombres

- **Variables:** `camelCase`
- **Funciones:** `camelCase`
- **Clases:** `PascalCase`
- **Constantes:** `UPPER_SNAKE_CASE`

### Reglas rápidas

- Usa nombres descriptivos (evita abreviaciones salvo que sean estándar del dominio).
- Mantén consistencia: si una entidad es una clase, debe verse como clase (`PascalCase`).
- Las constantes deben representar valores “fijos” del módulo o del dominio.

---

## Punto y coma

- **Regla:** siempre usar `;`.

Si en el futuro se decide *no* usar `;`, este documento debe actualizarse y el formateador/linter debe reflejarlo.

---

## Ejemplos

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

## Checklist antes de hacer PR

- El código está en inglés.
- Variables y funciones usan `camelCase`.
- Clases usan `PascalCase`.
- Constantes usan `UPPER_SNAKE_CASE`.
- Indentación a 2 espacios.
- Se usan `;`.
