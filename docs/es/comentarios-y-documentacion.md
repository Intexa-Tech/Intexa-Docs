# Comentarios y documentación

Reglas simples para mantener el repo entendible y fácil de mantener.

---

## Comentarios

- **Comentarios solo cuando sea necesario.**
- Evitar comentarios obvios (“sumamos 1”).
- Comentarios útiles explican **por qué**, no solo **qué**.

### Cuándo sí comentar

- Decisiones no evidentes.
- Workarounds.
- Reglas del negocio complejas.
- Algoritmos/funciones complejas.

---

## Documentación

- **README siempre actualizado.**
- Los endpoints de las APIs deben estar bien documentados.

### Qué documentar como mínimo

- Cómo correr el proyecto local.
- Variables de entorno requeridas (sin secretos).
- Comandos comunes.
- Endpoints (método, ruta, request, response, errores).

---

## Documentación de endpoints (ejemplo)

### `POST /api/users`

**Descripción**

Crea un usuario.

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

## Placeholders para personalizar

- Estándar de documentación de APIs: `REPLACE_ME` (OpenAPI/Swagger / Markdown / Postman collections)
- Ubicación de docs de API: `REPLACE_ME`
