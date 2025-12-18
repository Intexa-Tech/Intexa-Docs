# Manejo de errores

Este documento define cómo deben manejarse los errores para mantener buena UX, estabilidad y seguridad.

---

## Reglas

- **Siempre devolver mensajes claros** al cliente.
- **Nunca exponer errores internos** (stack traces, queries, paths, nombres internos) al cliente.
- **Logs separados para desarrollo y producción**.

---

## Respuestas al cliente

### Qué SÍ

- Mensajes simples y accionables.
- Códigos HTTP correctos.

Ejemplos:

- `400` invalid input
- `401` unauthorized
- `403` forbidden
- `404` not found
- `409` conflict
- `422` validation error
- `500` internal server error

### Qué NO

- Stack trace
- Mensajes del ORM/DB
- Detalles de infraestructura

---

## Manejo con `try/catch`

Regla:

- Los controllers capturan errores esperables.
- Los errores inesperados se envían a un manejador central.

Ejemplo (pseudo):

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

## Logging por entorno

- **Desarrollo:**
  - logs más verbosos
  - puede incluir stack trace

- **Producción:**
  - logs estructurados
  - correlation/request id
  - sin secretos
  - sin PII (o minimizada)

Placeholders:

- Logger: `REPLACE_ME` (console / pino / winston / datadog / etc.)
- Request ID: `REPLACE_ME`

---

## Checklist

- El cliente siempre recibe un mensaje entendible.
- No se filtra información interna.
- Hay logging suficiente para debug.
- Producción no imprime secretos.
