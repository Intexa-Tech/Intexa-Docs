# Estructura de carpetas (MVC)

Este documento define una estructura base para organizar proyectos (principalmente backend) usando el patrón **MVC**.

El objetivo es evitar desorden cuando el proyecto crece, separar responsabilidades y facilitar el mantenimiento.

---

## ¿Qué es MVC?

MVC significa:

- **Model (Modelo):** representa la data y reglas del dominio. Se encarga de cómo se estructura y persiste la información.
- **View (Vista):** capa de presentación (UI). En backend puro normalmente no existe como UI, pero puede representar:
  - plantillas (si usas renderizado server-side)
  - o simplemente el “formato de respuesta” (JSON) como una responsabilidad controlada.
- **Controller (Controlador):** orquesta la petición: recibe input, valida, llama servicios/modelos y devuelve una respuesta.

En la mayoría de productos, usamos MVC porque:

- Aclara dónde va cada cosa.
- Reduce acoplamiento.
- Hace más fácil testear.
- Permite escalar el equipo sin pisarse.

---

## Estructura ejemplo (backend)

```text
src/
  controllers/
  models/
  routes/
  services/
  middlewares/
  utils/
  config/
```

---

## ¿Qué va en cada carpeta?

## `src/controllers/`

- Controladores de endpoints.
- Deben ser “delgados”:
  - parsear request
  - validar (o delegar validación)
  - llamar a `services/`
  - mapear a response

Evita poner lógica de negocio compleja aquí.

## `src/models/`

- Modelos del dominio y/o esquemas.
- Ejemplos típicos:
  - modelos ORM (Sequelize/Prisma/Mongoose)
  - entidades del dominio
  - validación estructural del modelo (si aplica)

## `src/routes/`

- Definición de rutas (HTTP) y conexión con controllers.
- Aquí se organiza el API por módulos:
  - `users.routes.js`
  - `orders.routes.js`

## `src/services/`

- Lógica de negocio.
- Reglas del dominio.
- Coordinación entre modelos/repositorios/APIs.

En general:

- Un controller llama a uno o más services.
- Un service habla con models y/o integraciones.

## `src/middlewares/`

- Middlewares HTTP (Express u otro framework):
  - auth
  - rate limiting
  - manejo de errores
  - validación previa
  - logging

## `src/utils/`

- Utilidades reutilizables, sin dependencia fuerte del dominio.
- Ejemplos:
  - helpers de fechas
  - sanitización
  - wrappers de fetch/http
  - constantes de uso transversal

## `src/config/`

- Configuración del proyecto:
  - variables de entorno (carga/validación)
  - configuración de DB
  - configuración de CORS
  - configuración de logging

---

## Reglas prácticas para mantener el orden

- Un archivo debe tener **una responsabilidad principal**.
- Si una carpeta empieza a crecer demasiado, crea submódulos:

```text
src/
  modules/
    users/
      users.routes.js
      users.controller.js
      users.service.js
      users.model.js
```

- Mantén “dominio” (services/models) separado de HTTP (routes/controllers/middlewares).

---

## (Opcional) Estructura mínima recomendada

Si quieres un punto de partida típico:

```text
src/
  app.js
  server.js
  routes/
    index.routes.js
  controllers/
  services/
  models/
  middlewares/
  utils/
  config/
```

---

## Placeholders para personalizar

- Framework backend: `REPLACE_ME` (Express / Fastify / Nest / etc.)
- ORM/DB: `REPLACE_ME`
- Convención de módulos: `REPLACE_ME` (por carpeta o por feature)
