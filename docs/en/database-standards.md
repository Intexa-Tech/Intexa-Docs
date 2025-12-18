# Database standards

Rules to keep DB naming consistent and maintenance-friendly.

---

## Naming

- **Tables:** `snake_case`
  - example: `user_accounts`, `purchase_orders`

- **Columns:** `snake_case`
  - example: `created_at`, `updated_at`, `order_total`

---

## Keys

- **Primary key:** `id`
- **Foreign keys:** `id_table`
  - example: `id_user`, `id_order`

---

## Dates

- **Presentation format (UI/reports):** `DD-MM-YYYY`

Note:

- In the DB and APIs it’s recommended to store/transport dates using a standard format (e.g. ISO 8601) and **format to `DD-MM-YYYY` at the view layer**.
- Decision placeholders:
  - DB storage: `REPLACE_ME` (UTC timestamp / date / datetime)
  - API date format: `REPLACE_ME` (ISO 8601 recommended)

---

## Soft delete

- Use soft delete whenever possible.

Typical options:

- `deleted_at` (nullable timestamp)
- `is_deleted` (boolean)

Rules:

- Default queries should not return deleted records.
- There must be an admin/audit way to view deleted records.

---

## Audit fields (recommended)

- `created_at`
- `updated_at`
- `deleted_at` (if applicable)
- `created_by` / `updated_by` (if applicable)

---

## Example

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

## Placeholders to customize

- DB engine: `REPLACE_ME` (Postgres / MySQL / SQL Server / etc.)
- Migrations: `REPLACE_ME` (Prisma / Knex / Sequelize / Flyway / etc.)
