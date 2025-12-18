# Testing (básico)

Aunque no existan tests automatizados aún, hay un mínimo obligatorio para no subir código roto.

---

## Reglas

- **Toda feature importante debe probarse**.
- **No subir código roto**.
- **Probar endpoints antes de hacer PR**.

---

## Qué significa “probar”

Dependiendo del proyecto, al menos uno:

- Prueba manual en entorno local.
- Prueba de endpoints con Postman/Insomnia/cURL.
- Smoke test básico.

Placeholders:

- Herramienta de API testing: `REPLACE_ME` (Postman / Insomnia)
- Entorno de staging: `REPLACE_ME`

---

## Checklist antes de PR

- El proyecto corre local.
- No hay errores en consola.
- Los endpoints modificados fueron probados:
  - status code esperado
  - payload esperado
  - casos de error (inputs inválidos)
- No se rompen flujos existentes.

---

## Ejemplo (prueba de endpoint)

```bash
# REPLACE_ME: URL local
curl -X POST http://localhost:REPLACE_ME/api/users \
  -H 'Content-Type: application/json' \
  -d '{"email":"test@example.com","password":"REPLACE_ME"}'
```

---

## Si en el futuro agregamos tests automáticos

Recomendado:

- Unit tests para lógica de `services/`.
- Integration tests para endpoints críticos.

Framework placeholder:

- `REPLACE_ME` (Jest / Vitest / Mocha)
