# System Brief — InventaPyme

## Nombre del sistema

**InventaPyme**

## Descripción general

InventaPyme es una aplicación web de gestión de inventario diseñada para pequeñas y medianas empresas que actualmente llevan su control de stock en hojas de cálculo o cuadernos físicos. El sistema permite registrar productos, controlar entradas y salidas de stock, y detectar productos con stock bajo, todo desde un navegador web sin necesidad de instalar software adicional.

## Problema que resuelve

Las pequeñas y medianas empresas (tiendas, ferreterías, distribuidoras, minisupers) controlan su inventario con hojas de Excel o cuadernos físicos. Esta práctica genera:

- Quiebres de stock no detectados a tiempo
- Discrepancias entre el inventario físico y el registrado
- Pérdidas no trazables
- Decisiones de reabastecimiento basadas en intuición en vez de datos reales

## Usuarios objetivo

Propietarios o encargados de pequeñas y medianas empresas comerciales que necesitan una herramienta simple para controlar su inventario sin requerir conocimientos técnicos avanzados.

## Scope (En alcance — MVP)

- Registro, login y logout de usuarios
- Contraseñas hasheadas y sesiones protegidas
- Creación de 1 negocio por usuario
- Visualización del inventario con buscador por nombre o código
- Crear, editar y eliminar productos
- Ingresar y despachar unidades de stock
- Validaciones: nombres duplicados, cantidades negativas, stock insuficiente
- Mensajes de retroalimentación al usuario (flash messages)

## No-Scope (Fuera de alcance — MVP)

- Múltiples negocios por cuenta
- Historial de movimientos de inventario
- Roles de usuario (administrador, empleado, vendedor)
- Reportes exportables (Excel, PDF)
- Gráficas y estadísticas
- Precios de compra y venta en productos
- Categorías de productos
- Notificaciones activas de stock mínimo
- API REST con respuestas JSON
- Multi-usuario por negocio
- Recuperación de contraseña

## Stack tecnológico

| Capa | Tecnología |
|---|---|
| Lenguaje | Python 3 |
| Framework web | Flask |
| Motor de plantillas | Jinja2 |
| Base de datos | SQLite |
| Seguridad | Werkzeug |
| Servidor de desarrollo | Flask built-in (debug mode) |

## Tipo de arquitectura

Monolítica MVC (Model-View-Controller) de una sola capa de despliegue.
