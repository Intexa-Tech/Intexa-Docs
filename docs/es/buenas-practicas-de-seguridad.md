# Buenas prácticas de seguridad

Reglas simples y obligatorias para evitar incidentes.

---

## Reglas (importantes)

- **❌ Nunca subir `.env`**.
- **❌ Nunca subir claves / tokens / credenciales** (API keys, JWT secrets, passwords, private keys, service accounts, etc.).
- **✔ Usar variables de entorno** para toda configuración sensible.
- **✔ Validar inputs** (body, params, query) antes de procesar.
- **✔ Manejar errores con `try/catch`** (o middleware de error centralizado) para no romper el servidor ni filtrar información.

---

## Variables de entorno

- Todo secreto debe existir únicamente en:
  - variables de entorno del sistema / CI
  - secret manager (recomendado)

### Checklist

- El repo incluye un archivo ejemplo:
  - `REPLACE_ME` (ej: `.env.example`) con **nombres** de variables, pero **sin valores reales**.
- Las variables se validan al iniciar la app:
  - `REPLACE_ME` (ej: `zod`, `envalid`, validación manual)

---

## Validación de inputs

Validar siempre:

- `req.body`
- `req.params`
- `req.query`

### Reglas

- Rechazar campos extra si el endpoint no los permite.
- Validar tipos, formatos, límites (strings largos, rangos, etc.).
- Sanitizar cuando aplique (trim, normalización).

### Ejemplo (pseudo)

```js
// REPLACE_ME: librería de validación
function validateCreateUser(input) {
  // validar email, password, etc.
  return input;
}
```

---

## Errores y respuestas

- Nunca devuelvas stack traces, SQL errors o detalles internos al cliente.
- A nivel cliente: mensajes claros y genéricos.
- A nivel logs: detalle suficiente para diagnosticar.

---

## Git hygiene

- Agregar al `.gitignore`:
  - `.env`
  - `*.key`
  - `*.pem`
  - `credentials*.json`

---

## Ejemplos de cosas que NO se suben

- AWS keys
- Firebase service account JSON
- JWT secret
- DB password
- API tokens (Stripe, Twilio, etc.)

---

## Placeholders para personalizar

- Secret manager: `REPLACE_ME` (AWS Secrets Manager / GCP Secret Manager / Vault / etc.)
- Librería de validación: `REPLACE_ME`
- Estrategia de logging: `REPLACE_ME`
