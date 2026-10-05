# Planeacion general del Proyecto integrador

## Front-end

Técnologias a utilizar

- HTML
- CSS
- Javascript
- bootstrap
- netlify

### Páginas a realizar

**Usuario(cliente)**

- LogIn
- SignIn
- Dashboard(Cliente):
  - historial de envios,
  - Pedidos pendientes,
  - Realizar pedidos ,
  - consultar pedidos
- Pagina de incidencias

**usuario(Repartidor)**

- LogIn
- Ruta de reparticion
- Pagina de confirmacion de pedido
- Pagina de incidencias

**Admin**

- LogIn
- Administrar rutas
- dashboard de actividad
- Menu de gestion de incidencias.
- Menu de administracion de pedidos

**SuperAdmin**

- LogIn
- Menu de administracion de usuarios

## Back-end

Técnologias a utilizar

- Nodejs
- Firestore
- sql
- Apis externas :{una de localizacion}

## Modulos(Endpoints)

- Pedidos
- Usuarios

- Autenticación (login/registro con JWT y control de roles)
- Rutas (asignar pedidos a repartidores)
- Incidencias
- Seguimiento/Tracking (historial de estados de cada paquete)

### Plan por fases

Fase Objetivo Entregables

1. Análisis y diseño Definir qué hace el sistema Requerimientos funcionales, casos de uso, diagrama de estados del pedido, diagrama entidad-relación
2. Base y auth Cimientos del back-end Modelo de datos, registro/login, roles con JWT
3. Núcleo Lo mínimo funcional Crear pedido, generar guía, rastrear, panel del cliente
4. Operación Lado de la empresa Rutas, panel del repartidor, confirmación de entrega
5. Gestión Control administrativo Incidencias, dashboard del admin, gestión de usuarios (superadmin)
6. Extras Pulido Mapa, cotizador, notificaciones, despliegue

Entidades base para tu modelo de datos
Usuario (id, nombre, correo, contraseña, rol)
Pedido/Envío (id, número de guía, cliente, remitente, destinatario, direcciones, peso, dimensiones, estado, costo)
HistorialEstado (pedido, estado, fecha, quién lo cambió)
Ruta (id, repartidor, fecha) y RutaPedido (ruta, pedido, orden)
Incidencia (pedido, tipo, descripción, estado, quién la reportó)
