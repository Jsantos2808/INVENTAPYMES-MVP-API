# Arquitectura del sistema — InventaPyme

## Tipo de arquitectura

**Monolítica MVC (Model-View-Controller)**

Toda la aplicación reside en un único proceso Flask. No hay microservicios, ni separación de frontend/backend en proyectos distintos.

## Diagrama de capas

```
┌─────────────────────────────────┐
│         Navegador Web           │
│    (HTML Forms / HTTP Requests) │
└────────────────┬────────────────┘
                 │ HTTP
┌────────────────▼────────────────┐
│           app.py                │
│      Flask — Rutas + Lógica     │
│                                 │
│  @login_required  @before_request│
│  Werkzeug (hashing)             │
└──────┬──────────────┬───────────┘
       │              │
┌──────▼──────┐ ┌─────▼──────────┐
│  Templates  │ │     db.py      │
│  Jinja2     │ │  Conexión      │
│  .html      │ │  SQLite        │
└─────────────┘ └─────┬──────────┘
                      │
               ┌──────▼──────────┐
               │   SQLite DB     │
               │ inventapyme.db  │
               └─────────────────┘
```

## Componentes

### app.py — Capa de lógica y rutas

Archivo principal que contiene todas las rutas HTTP, validaciones de negocio y manejo de sesiones. Actúa como controlador (C) del patrón MVC.

**Responsabilidades:**
- Definir y manejar todos los endpoints de la aplicación
- Validar datos de entrada de formularios
- Gestionar sesiones de usuario
- Comunicar resultados al usuario mediante flash messages
- Llamar a `db.py` para operaciones de datos

**Middlewares:**
- `@login_required`: decorador que protege rutas privadas
- `@before_request` → `load_user()`: carga el usuario actual en `g` antes de cada solicitud

### db.py — Capa de datos

Módulo encargado de la conexión con SQLite y la inicialización del esquema de base de datos.

**Responsabilidades:**
- Proveer la función `get_db()` para obtener una conexión activa
- Ejecutar `init_db()` al arrancar la aplicación para crear las tablas si no existen

### Templates Jinja2 — Capa de presentación

Archivos HTML que reciben variables del controlador y renderizan la interfaz de usuario. Actúan como la vista (V) del patrón MVC.

| Template | Descripción |
|---|---|
| `login.html` | Formulario de inicio de sesión |
| `register.html` | Formulario de registro de usuario |
| `dashboard.html` | Panel principal con lista de negocios |
| `inventario.html` | Vista del inventario con buscador y operaciones |

### SQLite — Persistencia

Base de datos relacional embebida. No requiere servidor externo.

## Esquema de base de datos

### Tabla `users`

| Columna | Tipo | Descripción |
|---|---|---|
| id | INTEGER PK | Identificador único |
| username | TEXT UNIQUE | Nombre de usuario |
| password_hash | TEXT | Contraseña hasheada |
| nombre | TEXT | Nombre del usuario |

### Tabla `businesses`

| Columna | Tipo | Descripción |
|---|---|---|
| id | INTEGER PK | Identificador único |
| user_id | INTEGER FK | Referencia a `users.id` |
| nombre | TEXT | Nombre del negocio |
| created_at | TIMESTAMP | Fecha de creación |

### Tabla `products`

| Columna | Tipo | Descripción |
|---|---|---|
| id | INTEGER PK | Identificador único |
| business_id | INTEGER FK | Referencia a `businesses.id` |
| nombre | TEXT | Nombre del producto |
| codigo | TEXT | Código del producto (opcional) |
| cantidad | INTEGER | Stock actual |
| stock_minimo | INTEGER | Nivel mínimo de stock |
| created_at | TIMESTAMP | Fecha de creación |

## Flujo de una solicitud típica

```
1. Usuario llena un formulario en el navegador
2. Navegador envía POST HTTP a Flask
3. @before_request carga el usuario desde la sesión
4. @login_required verifica autenticación
5. La función de la ruta valida los datos del formulario
6. Se ejecuta la consulta SQL mediante get_db()
7. Se genera un flash message con el resultado
8. Flask redirige al usuario (redirect)
9. La siguiente solicitud GET renderiza la vista actualizada
```

## Decisiones de diseño

| Decisión | Justificación |
|---|---|
| SQLite en lugar de PostgreSQL | Simplicidad de despliegue para MVP; sin servidor externo |
| Monolito en lugar de microservicios | Menor complejidad operacional para el alcance del MVP |
| Sesiones con cookie firmada | Solución integrada de Flask; suficiente para un solo usuario por sesión |
| Werkzeug para hashing | Librería incluida en Flask; pbkdf2:sha256 es seguro para producción básica |

## Evolución futura sugerida

- Migrar a PostgreSQL cuando el volumen de datos crezca
- Separar la lógica en Blueprints de Flask por módulo (auth, inventario, reportes)
- Agregar una capa de API REST (JSON) para soportar un frontend desacoplado
- Implementar un sistema de roles con Flask-Login
