# Estándares de base de datos

Reglas para mantener consistencia y facilitar mantenimiento en DB.

---

## Nombres

- **Tablas:** `snake_case`
  - ejemplo: `user_accounts`, `purchase_orders`

- **Columnas:** `snake_case`
  - ejemplo: `created_at`, `updated_at`, `order_total`

---

## Claves

- **Clave primaria:** `id`
- **Foráneas:** `id_tabla`
  - ejemplo: `id_user`, `id_order`

---

## Fechas

- **Formato de presentación (UI/reportes):** `DD-MM-YYYY`

Nota:

- En la DB y APIs se recomienda almacenar/transportar en un formato estándar (ej. ISO 8601) y **formatear a `DD-MM-YYYY` en la vista**.
- Placeholder de decisión:
  - DB storage: `REPLACE_ME` (timestamp UTC / date / datetime)
  - API date format: `REPLACE_ME` (ISO 8601 recomendado)

---

## Soft delete

- Usar soft delete cuando sea posible.

Opciones típicas:

- `deleted_at` (timestamp nullable)
- `is_deleted` (boolean)

Reglas:

- Queries por defecto no deben traer registros eliminados.
- Debe existir forma admin/auditoría para ver eliminados.

---

## Auditoría (recomendado)

- `created_at`
- `updated_at`
- `deleted_at` (si aplica)
- `created_by` / `updated_by` (si aplica)

---

## Ejemplo

```text
purchase_orders
  id
  id_user
  status
  total_amount
  created_at
  updated_at
  deleted_at
```

---

## Placeholders para personalizar

- Motor DB: `REPLACE_ME` (Postgres / MySQL / SQL Server / etc.)
- Migraciones: `REPLACE_ME` (Prisma / Knex / Sequelize / Flyway / etc.)
