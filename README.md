# InventaPyme

Sistema web de gestión de inventario para pequeñas y medianas empresas.

## Problema que resuelve

Las pequeñas y medianas empresas (tiendas, ferreterías, distribuidoras, minisupers) controlan su inventario con hojas de Excel o cuadernos físicos. Esta práctica genera quiebres de stock no detectados, discrepancias entre el inventario físico y el registrado, pérdidas no trazables y decisiones de reabastecimiento basadas en intuición en vez de datos reales.

**InventaPyme** ofrece una solución web simple, accesible desde cualquier navegador, que permite registrar y controlar el inventario en tiempo real.

## Tecnologías

| Capa | Tecnología |
|---|---|
| Backend | Python 3 + Flask |
| Plantillas | Jinja2 |
| Base de datos | SQLite |
| Seguridad | Werkzeug (hashing) |

## Instalación y ejecución local

```bash
# 1. Clonar el repositorio
git clone https://github.com/tu-usuario/inventapyme.git
cd inventapyme

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Ejecutar la aplicación
python app.py
```

La aplicación estará disponible en `http://127.0.0.1:5000`.

## Estructura del proyecto

```
inventapyme/
├── app.py              # Rutas y lógica principal
├── db.py               # Conexión y configuración de la base de datos
├── requirements.txt    # Dependencias del proyecto
├── templates/          # Plantillas HTML (Jinja2)
│   ├── login.html
│   ├── register.html
│   ├── dashboard.html
│   └── inventario.html
└── docs/               # Documentación del sistema
    ├── system-brief.md
    ├── requirements.md
    ├── architecture.md
    └── api/
        └── openapi.yaml
```

## Documentación

- [Resumen del sistema](docs/system-brief.md)
- [Requisitos](docs/requirements.md)
- [Arquitectura](docs/architecture.md)
- [API](docs/api/openapi.yaml)

## Estado del proyecto

MVP en desarrollo. Ver el [backlog del proyecto](#) para seguimiento de tareas.
