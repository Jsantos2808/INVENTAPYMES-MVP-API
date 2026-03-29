# Requisitos del sistema — InventaPyme

## Requisitos Funcionales

### Autenticación

| ID | Requisito |
|---|---|
| RF-01 | El sistema debe permitir registrar un nuevo usuario con nombre, nombre de usuario y contraseña. |
| RF-02 | El sistema debe validar que el nombre de usuario no esté duplicado al registrarse. |
| RF-03 | El sistema debe permitir iniciar sesión con nombre de usuario y contraseña. |
| RF-04 | El sistema debe permitir cerrar sesión. |
| RF-05 | El sistema debe restringir el acceso a rutas protegidas a usuarios no autenticados. |

### Gestión de negocio

| ID | Requisito |
|---|---|
| RF-06 | El sistema debe permitir al usuario crear un negocio con nombre. |
| RF-07 | El sistema debe limitar a 1 negocio por cuenta de usuario. |
| RF-08 | El sistema debe mostrar un panel con el negocio registrado y su cantidad de productos. |

### Gestión de inventario

| ID | Requisito |
|---|---|
| RF-09 | El sistema debe mostrar la lista de productos del negocio ordenada por nombre. |
| RF-10 | El sistema debe permitir buscar productos por nombre o código. |
| RF-11 | El sistema debe permitir agregar un producto con nombre, código (opcional), cantidad inicial y stock mínimo. |
| RF-12 | El sistema debe validar que no existan dos productos con el mismo nombre en el mismo negocio. |
| RF-13 | El sistema debe permitir editar el nombre, código, cantidad y stock mínimo de un producto. |
| RF-14 | El sistema debe permitir eliminar un producto del inventario. |

### Movimientos de stock

| ID | Requisito |
|---|---|
| RF-15 | El sistema debe permitir ingresar unidades al stock de un producto (entrada). |
| RF-16 | El sistema debe permitir despachar unidades del stock de un producto (salida). |
| RF-17 | El sistema debe validar que la cantidad a despachar no supere el stock disponible. |
| RF-18 | El sistema debe validar que las cantidades ingresadas sean números enteros positivos. |

### Retroalimentación

| ID | Requisito |
|---|---|
| RF-19 | El sistema debe mostrar mensajes de éxito, error e información después de cada operación. |

---

## Requisitos No Funcionales

### Seguridad

| ID | Requisito |
|---|---|
| RNF-01 | Las contraseñas deben almacenarse como hash usando Werkzeug (pbkdf2:sha256). |
| RNF-02 | Las sesiones de usuario deben manejarse con una clave secreta del servidor. |
| RNF-03 | Toda ruta del panel debe requerir autenticación activa. |

### Usabilidad

| ID | Requisito |
|---|---|
| RNF-04 | La interfaz debe ser accesible desde cualquier navegador web moderno sin instalación de software adicional. |
| RNF-05 | El sistema debe proporcionar retroalimentación clara al usuario ante errores de validación. |

### Disponibilidad y rendimiento

| ID | Requisito |
|---|---|
| RNF-06 | El sistema debe responder a las solicitudes del usuario en menos de 2 segundos en condiciones normales. |
| RNF-07 | El sistema debe funcionar en un servidor local durante la fase de MVP. |

### Mantenibilidad

| ID | Requisito |
|---|---|
| RNF-08 | El código debe estar organizado en módulos separados por responsabilidad (app.py, db.py). |
| RNF-09 | La base de datos debe inicializarse automáticamente al arrancar la aplicación. |
