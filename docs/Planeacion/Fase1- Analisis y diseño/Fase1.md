# Fase 1

Se manejara la planeacion del proyecto tomando en cuenta lo siguiente
Requerimientos funcionales, casos de uso, diagrama de estados del pedido,diagrama entidad-relació

## Requerimientos Funcionales

- Usuarios:
  - El sistema debe permitir una nueva solicitud de envio mediante el llenado de un formularion con los siguientes elementos: `datos del remitente, destinatario, peso/dimensiones y direccion de entrega`
  - El sistema debe permitir al usuario consultar el historial y el estado en tiempo real de sus envios emitidos mediante el numero de guia
  - El sistema permite al usuario registrar reportes de incidencias asociados a un envio especifica `(ej.paquete dañado,retraso,dirreccion erronea)`
  - El sistema debe permitir al usuario solicitar la eliminacion lógica de su cuenta , desactivando su acceso sin eliminar fisicamente sus registros de envios pasados en la base de datos.

- Repartidor:
  - El sistema debe permitir al repartidor consultar la lista de paquetes asignados a su ruta diaria de reparticion.
  - El sistema debe permitir al repartidor actualizar el estado de un envio a "Entregado" al completar una entrega con exito.
  - El sistema debe permitir al repartidor actualizar el estado de un envio a "No entregado" cuando la entrega falle , adjuntando un registro del motivo correspondiente.
  - El sistema debe permitir al repartidor registrar incidencias ocurridas durante su ruta.

- Modulo de administrador
  - El sistema debe presentar un dashboard analitico con indicadores clave (metricas de envíos en transito, entregados, no entregados, tiempos promedio de entrega y tasas de incidencia) para la toma de decisiones.
  - El sistema debe permitir al administrador planear y asignar paquetes a las rutas de entrega de los repartidores.
  - El sistema debe permitir al administrador buscar, consultar y filtrar la informacion detallada de cualquier pedido registrado en la plataforma.
  - El sistema debe permitir al administrador gestionar los reportes de incidencias generados por usuarios o repartidores para su solucion.

- SuperAdmin
  - El sistema debe permitir al super admin gestionar el ciclo de vida completo(crear,consultar , actualizar, desactivar) de cuentas de usuario , repartidores y administradores.
  - El sistema debe otorgar al superAdmin acceso irrestricto a todos los modulos, configuraciones globales y registros de auditoria de software.
  - El sistema debe permitir al superAdmin respaldar o dar mantenimiento a los parametros generales de la base de datos del sistema.

## Casos de uso

1. USER(CLIENT)
   - CU-01: Registrar solicitud de envio.
     - El usuario seleciona la opcion crear nuevo pedido
     - El sistema muestra el formulario de envio
     - El ususario ingresa los datos del remitente , destinatario , direccion de entrega y detalles del paquete.
     - El sistema valida los datos ingresados.
     - El sistema genera un numero de guia unico, asigna el estado inicial "registrado" y guarda la informacion en la base de datos.
     - El sistema muestra un mensaje de confirmacion con el numero de guia generado.
     - Si falta algun dato obligatorio , el sistema muestra un mensaje de error solicitando corregir los campos marcados.

   - CU-02:Consultar estado de envio
   - CU-03:Reportar reporte de incidencia(cliente)
   - CU-04: Solicitar baja de cueta(eliminacion logica)

2. REPARTIDOR
   - CU-05:Consulta de ruta asignada
   - CU-06: Registrar entrega exitosa
     - El repartidor accede a su lista de pedidos del diay selecciona un paquete.
     - El repartidor selecciona el boton de accion "marcar como entregado"
     - El sistema solicita confirmacion o comprobante simple.
     - El sistema actualiza el estado del paquete a "entregado" y registra fecha/hora exacta.
     - El sistema notificara la finalizacion del envio.
     - El repartidor puede seleccionar "Marcar como no entregado"
     - El sistema despliaga una lista de motivos por la que no se pudo realizar la entrega(domicilio no encontrado , cliente ausente , etc)
     - El sistema cambia el estado del paquete a "no entregado" y registra el motivo en la base de datos.

   - CU-07: Registrar intento de entrega fallido
     - El repartidor accede a su lista de pedidos del diay selecciona un paquete.
     - El repartidor selecciona el boton de accion "marcar como entregado"
     - El sistema solicita confirmacion o comprobante simple.
     - El sistema actualiza el estado del paquete a "entregado" y registra fecha/hora exacta.
     - El sistema notificara la finalizacion del envio.
     - El repartidor puede seleccionar "Marcar como no entregado"
     - El sistema despliaga una lista de motivos por la que no se pudo realizar la entrega(domicilio no encontrado , cliente ausente , etc)
     - El sistema cambia el estado del paquete a "no entregado" y registra el motivo en la base de datos.
   - CU-08:Registrar reporte de incidencia(repartidor)

3. Administrativo
   - CU-09:Visualizar dashboard de decisiones(KPIs y metricas)
     - El administrador ingresa al panel principal.
     - El sistema realiza la consulta a la base de datos agregando metricas clave.
     - El sistema despliega paneles graficos con:
       - Total de paquetes distribuidos por estado(Registrado, En transito, en ruta, Entregado,no entregado)
       - Tiempo promedio global de entrega.
       - Porcentaje de entregas exitosas vs. fallidas.
     - El administrador aplica filtros por rango de fechas o zonas si lo requiere.
     - El sistema actualiza las graficas en pantalla.
   - CU-10: Planificar y asignar rutas de entrega
     - El administrador selecciona la seccion "asignacion de rutas"
     - El sistema muestra los paquetes pendientes de repartir y la lista de repartidores disponibles.
     - El administrador selecciona uno o varios paquetes y los asigna a un repartidor especifico.
     - El sistema actualiza el estado de los paquetes seleccionados a "En ruta"
     - El sistema notifica al reapartidor en su lista de tareas.
   - CU-11: Consultar historial global de pedidos.
   - CU-12:Gestionar y resolver incidencias

4. SuperAdmin
   - CU-13: Gestionar usuarios y roles (CRUD completo).
     - El superAdmin accede al modulo de "administracion de usuarios"
     - El sistema muestra la lista completa de cuentas registradas en el sistema.
     - El superAdmin selecciona una accion : Crear nuevo usuario , modificar rol/datos de usuario existente o desactivar usuario.
     - Ell sistema valida la solicitud y efectua el cambio en la base de datos.
       El sistema muestra la confirmacion de la operacion.
   - CU-14: Configurar parametros globales del sistema.
