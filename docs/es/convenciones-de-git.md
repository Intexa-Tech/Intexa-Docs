# Convenciones de Git

Este documento define cómo trabajamos con Git para mantener un flujo ordenado y consistente.

---

## Ramas

### Ramas principales

- `main`: producción.
- `develop`: desarrollo / integración.

### Ramas de trabajo

- `feature/nombre-corto`: nueva funcionalidad.
- `fix/nombre-corto`: corrección de error.

#### Reglas prácticas

- Nombres en minúscula.
- Usa guiones `-` para separar palabras.
- El nombre debe describir el objetivo:
  - `feature/user-auth`
  - `feature/payment-webhook`
  - `fix/login-redirect`
  - `fix/order-total-rounding`

---

## Commits

Usamos un formato simple inspirado en **Conventional Commits**.

### Tipos

- `feat:` nueva funcionalidad.
- `fix:` corrección de error.
- `docs:` documentación.
- `refactor:` mejora de código (sin cambiar comportamiento).

### Reglas

- Mensajes cortos y claros.
- En **presente**.
- Sin punto final.
- Deben explicar el *qué* (el *por qué* va en la descripción del PR si hace falta).

### Ejemplos

```text
feat: add user registration endpoint
fix: prevent null pointer on invoice creation
docs: update onboarding steps
refactor: extract order total calculation
```

---

## Flujo recomendado (resumen)

1. Crear rama desde `develop`:

```text
git checkout develop
git pull
git checkout -b feature/REPLACE_ME
```

2. Hacer commits pequeños y frecuentes.

3. Mantener la rama actualizada (si aplica):

```text
git fetch
REPLACE_ME
```

4. Abrir PR hacia `develop`.

5. Una vez aprobado y mergeado a `develop`, el despliegue/merge a `main` se realiza siguiendo el proceso de releases del proyecto:

- `REPLACE_ME` (manual / CI/CD / tag / release branch)

---

## Placeholders para personalizar

- Estrategia de releases: `REPLACE_ME`
- Reglas de PR (mínimo 1 reviewer, checks obligatorios, etc.): `REPLACE_ME`
- Naming adicional (hotfix, chore, etc. si lo usan): `REPLACE_ME`
