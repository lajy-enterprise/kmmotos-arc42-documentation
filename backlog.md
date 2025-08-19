## Backlog de la Aplicación KMMotos: Un Plan de Desarrollo por Fases

Este documento detalla el plan de desarrollo de la aplicación de gestión empresarial para KMMotos, estructurado en fases de implementación. Cada fase se enfoca en funcionalidades clave, permitiendo un enfoque iterativo y la entrega de un Producto Mínimo Viable (MVP) que evoluciona con las necesidades del negocio.

Para mas informacion sobre las fases de desarrollo y los módulos clave, por favor revisa el [Plan de Desarrollo](docs/ES/01_introduccion_y_objetivos.md).

- **Nota:** se omite fase 1 (Arquitectura e Infraestructura Básica) ya que no se requiere desarrollar en esta fase.

### **Fase 2: Sistema POS (Punto de Venta) MVP (Producto Mínimo Viable)**

- [x] **Gestión de Usuarios:**
  - [x] Registro de Usuarios (nombre, información general, etc.).
  - [x] Asignación de roles y permisos (integrado con Spatie Laravel Permission para seguridad).
  - [x] Gestión de credenciales de acceso.
- [x] **Gestión de Empleados:**
  - [x] Registro de empleados (nombre, información de contacto, perfiles).
- [x] **Gestión de Clientes:**
  - [x] Registro de clientes (nombre, dirección, información de contacto, NIF/CI).
  - [x] Gestión de datos de contacto y generales.
  - [x] Clubes
- [x] **Gestión de Mecanicos:**
  - [x] Registro de Mecanicos (nombre, informacion de contacto, NIF/CI).
- [x] **Gestión de Productos:**
  - [x] Bodegas (Almacen)
  - [x] Catálogo de productos (nombre, descripción, precio de venta, costo, SKU).
  - [x] Categorización de productos
    - [x] categorías, subcategorías, Rotacion, Aplicaciones.
  - [x] Gestión de variantes de productos
    - [x] marca, aplicaciones, modelo de motocicleta, Equivalencias.
  - [x] Asociación de productos con imágenes (Libreria Media Library).
- [x] **Gestión de Inventario (Básico):**
  - [x] Registro inicial de existencias.
  - [x] Importaciones de productos a inventario.
  - [x] Visualización del nivel de existencias por producto.
- [ ] **Facturación (Ventas):**
  - [x] Creación de nuevas ventas (selección de empleados, selección de clientes, selección de productos, descuentos, cálculo de totales).
  - [x] Registro de métodos de pago (efectivo, tarjeta, transferencia, etc).
  - [ ] Generación de facturas (impresión).
  - [ ] Devoluciones y anulaciones de ventas.
- [ ] **Documentos (Ventas)**
  - [ ] Cotización.
  - [ ] Proforma.
  - [ ] Convercion de documentos a facturas (Cotizacion a proforma -proforma afecta inventario-, proforma a factura -Ya el inventario se modifico en la proforma-).
- [ ] **módulo de pagos.**
  - [ ] ver pagos
  - [ ] abono cliente
- [x] **Gestión del manejo entre el tenancy central y los tenancies foraneos:**
  - [x] Gestión del manejo entre el tenancy central y los tenancies foraneos.

---

### **Fase 3: Sistema CRM (Customer Relationship Management)**

- [ ] **módulo de Devoluciones.**
  - [ ] ver Devoluciones
  - [ ] Gestionar Devoluciones
  - [ ] Gestion de Devoluciones como metodo de pago.
- [ ] **Gestión de Otros metodos de pagos de Clientes:**
  - [ ] Creditos de tienda
  - [ ] Creditos por Devolucion
  - [ ] Listado de Creditos de Clientes
- [ ] **Gestión de Grupo de vendedores (Rutas):**
  - [ ] Gestion de clientes en rutas (Grupo de vendedores)
  - [ ] Clientes Atendidos.
  - [ ] Comisiones en rutas (Grupo de vendedores)
- [ ] **Gestión Detallada de Clientes:**
  - [ ] Segmentación de clientes (ej. por tipo de motocicleta, frecuencia de compra).
  - [ ] Campos personalizados para perfiles de clientes, (mapas de ubicaciones, preferencias, interaccion con otros modulos, puntos, vales, etc).
- [ ] **Gestión de Interacciones con Clientes:**
  - [ ] Registro de llamadas, correos electrónicos, visitas, etc.
  - [ ] Historial de comunicaciones.
- [ ] **Tareas y Actividades para Empleados (Calendario):**
  - [ ] Asignación de tareas a empleados relacionadas con clientes (ej. seguimiento de cotizaciones, llamadas de post-venta).
  - [ ] Calendario de actividades.
  - [ ] Recordatorios y notificaciones de tareas pendientes.
- [ ] **Marketing Básico:**
  - [ ] Gestión de promociones y descuentos.

---

### **Fase 4: Funciones de RRHH (Recursos Humanos)**

- [x] **Gestión Detallada de Perfiles de Empleados:**
  - [x] Información personal, datos de contacto de emergencia, datos bancarios.
  - [x] Historial laboral dentro de la empresa.
  - [x] Documentos adjuntos (contratos, identificaciones, foto, etc).
- [ ] **Gestión de Planillas/Nóminas:**
  - [ ] DL Decimotercero
  - [ ] DL Decimocuarto
  - [ ] Registro de salarios y beneficios.
  - [ ] Cálculo de nóminas (sueldo base, horas extras, deducciones).
  - [ ] Generación de recibos de pago.
  - [ ] Gestión de impuestos y contribuciones.
- [ ] **Gestión de Horarios y Asistencias:**
  - [ ] Registro de entrada y salida (check-in/check-out).
  - [ ] Gestión de turnos.
  - [ ] Reportes de asistencia.
- [ ] **Vacaciones y Ausencias:**
  - [ ] Solicitudes y aprobación de vacaciones.
  - [ ] Registro de bajas por enfermedad u otras ausencias.
- [ ] **Acciones de Personal:**
  - [ ] Registro de ascensos, cambios de puesto, amonestaciones.
  - [ ] Evaluaciones de desempeño.
  - [ ] Gestión de capacitaciones.
- [ ] **Gestión de KPIS:**
  - [ ] Calendario de Tarea (Calendarios para que los empleados marquen sus tareas de trabajo)
  - [ ] Tareas de Perfiles (Asignacion de Tareas por sus respectivos perfiles)
  - [ ] Supervisar (Vista para que los supervisores puedan supervisar a los empleados)
  - [ ] Gestion de Supervisores (asignacion de supervisores y Configuración de Perfiles)
- [ ] **Solicitudes:**
  - [ ] Solicitar constancias
  - [ ] CheckList (De tiendas)
  - [ ] Documentacion Administrativas
  - [ ] Solicitudes y Seguimientos (Tickets de clientes para tareas dentro del sistema)
  - [ ] Solicitar Viáticos

---

### **Fase 5: Gestión Avanzada de Inventario (Movimiento entre Tiendas) ERP (Enterprise Resource Planning)**

- [ ] **Auditoria:**
  - [ ] Apertura de Tiendas (Gestion del proceso de creacion y Apertura de nuevas tiendas)
  - [ ] Auditoria de Tiendas (Gestion de la auditoria de tiendas para el manejo de inventario y control de stock)
- [ ] **Gestión de Inventario Dañado/Faltante:**
  - [ ] Productos dañados
  - [ ] Productos faltantes
- [ ] **Catalogo:**
  - [ ] Base imagenes
  - [ ] Galeria.
- [ ] **Múltiples Ubicaciones/Tiendas:** (Tenancy Central / Tenancies Foraneos)
  - [ ] Configuración y gestión de diferentes almacenes y tiendas.
  - [ ] Control de inventario por ubicación (Visualizacion de inventario de tenancies Foraneos).
- [ ] **Compras Locales (a Proveedores):**
  - [ ] Creación de órdenes de compra.
  - [ ] Recepción de productos y actualización de inventario.
  - [ ] Gestión de proveedores.
- [ ] **Packing:**
  - [ ] Preparación de pedidos para transferencia entre ubicaciones.
  - [ ] Generación de listas de empaque.
- [ ] **Pedidos de Productos a Bodega:**
  - [ ] Creación de solicitudes de reabastecimiento por parte de las tiendas.
  - [ ] Creación de solicitudes de reabastecimiento por parte de Grupos de Vendedores (Rutas).
  - [ ] Procesamiento y envío de pedidos desde la bodega central.
- [ ] **Solicitud de Complementos:**
  - [ ] Gestión de accesorios y piezas que complementan las motocicletas.
  - [ ] Pedidos específicos de complementos a la bodega o proveedores.
- [ ] **Solicitud de Surtidos:**
  - [ ] Procesos para solicitar una variedad de productos para mantener el stock adecuado en las tiendas.
- [ ] **Transferencias de Inventario:**
  - [ ] Gestión de transferencias entre Tiendas y Bodegas del mismo tenancy.
  - [ ] Convercion de transferencia a compra y venta local (Interna) entre empresas para el manejo de inventario y procesos financieros entre Empresas.
  - [ ] Seguimiento del estado de las transferencias.
  - [ ] Conciliación de inventario.
- [ ] **Gestión de Equipos / Materiales / Vienes de la Empresa:**
  - [ ] Registro de equipos y vienes de la empresa.
  - [ ] Gestión de equipos y vienes de la empresa.
  - [ ] Registro de Materiales e implementos de trabajo
  - [ ] Gestion de Surtido de Materiales e implementos de trabajo
- [ ] **Gestión de Aplicaciones Esternas:**
  - [ ] Integración con Shopify.
  - [ ] Integración con Supabase.
- [ ] **Importaciones**
  - [ ] Manejo de Status de pediodo de Importaciones de China
  - [ ] Valor Manual del Dolar

---

### **Fase 6: Módulos de Finanzas**

- [ ] **Optimización de Reportes con MongoDB:**
  - [ ] Los datos financieros transaccionales se almacenarán en PostgreSQL para integridad y relaciones. Sin embargo, para la generación de reportes complejos y agregados, y para la optimización de consultas analíticas, se utilizará MongoDB. Esto permitirá pre-calcular y almacenar resúmenes de datos financieros en un formato flexible, facilitando la extracción rápida de información para análisis de tendencias, proyecciones y dashboards financieros, sin sobrecargar la base de datos transaccional.
- [ ] **Optimización de Reportes con Queues/Jobs:**
  - [ ] Todos estos procesos de pre-cálculo y almacenamiento de resúmenes de datos financieros en un formato flexible deben procurarse realizar en colas de procesos controladas en segundo plano o, en su defecto, en un servidor aparte que ejecute dichas acciones como un servicio secundario que no afecte la operatividad de la empresa.
- [ ] **Cuentas Financieras:**
  - [ ] Registro de cuentas financieras donde se registran movimientos financieros, saldo guardado en cada tienda en efectivo y saldo en cuentas bancarias.
- [x] **Catalogo Contable:**
  - [x] Registro y mantenimiento de cuentas contables.
  - [x] Categorización de cuentas Contables.
  - [ ] Configuracion de automatizacion de cuentas Contables.
- [x] **Libro Diario:**
  - [ ] Registro de transacciones financieras.
  - [ ] Reportes financieros.
- [ ] **Contabilidad Básica:**
  - [x] Plan de cuentas simplificado. (Catalogo Contable)
  - [ ] Asientos contables automáticos derivados de transacciones (Libro Diario) (ventas, compras, pagos).
- [ ] **Cuentas por Pagar ( Modulo Pago a Proveedores):**
  - [ ] Registro y seguimiento de facturas de proveedores.
  - [ ] Estas Facturas Vienen de las importaciones a inventario en dado caso de que dichas importaciones tengan factura asignada.
  - [ ] Programación y procesamiento de pagos a proveedores.
  - [ ] Historial de pago a Proveedores.
  - [ ] Gestion de Proveedores.
- [ ] **Gestión de Gastos (Anclado a Cuentas del Catalogo Financiero):**
  - [ ] Registro de gastos operativos (alquiler, servicios, combustible, etc.).
  - [ ] Categorización de gastos.
  - [ ] Reportes de gastos.
- [ ] **Gestión de Créditos (a Clientes - Mayoreo):**
  - [ ] Asignación y gestión de líneas de crédito a clientes.
  - [ ] Registro de pagos de créditos.
  - [ ] Reportes de cuentas por cobrar.
- [ ] **Transferencias de Efectivo entre Tiendas:**
  - [ ] Registro y seguimiento de movimientos de efectivo entre diferentes ubicaciones (Cuentas Financieras).
  - [ ] Ingreso manual de efectivo a las tiendas.
- [ ] **Apertura y Cierre de Caja:**
  - [ ] Conciliación de saldos de caja.
- [ ] **Boletas de Compra:**
  - [ ] Registro detallado de todas las compras realizadas por la empresa.
  - [ ] Asociación de compras con proveedores y categorías.
- [ ] **Acreedores:** (Gestion de deudas bancarias, creditod y/o prestamos Bancarios a las tiendas o empresas)
  - [ ] Registro de acreedores.
  - [ ] Control y manejo de acreedores en tiempo real.
- [ ] **Otros Acreedores:** (Gestion de deudas Minuristas, Creditos y/o prestamos de terceros a las tiendas o empresas)
  - [ ] Registro de otros acreedores.
  - [ ] Control y manejo de otros acreedores en tiempo real.
- [ ] **Control de Arrendamientos:**
  - [ ] Registro de arrendamientos.
  - [ ] Control de arrendamientos en tiempo real.
- [ ] **Control de Permisos Operativos:**
  - [ ] Registro de permisos operativos.(Municipalidad, Seguridad, etc.)
  - [ ] Control digital (subida de imagenes).
  - [ ] Pago Impuestos (Municipalidad, Seguridad, etc.)
  - [ ] Declaraciones, etc.
  - [ ] Alertas y notificaciones de permisos vencidos o por vencer.
- [ ] **Agenda de Pagos:**
  - [ ] Registro de pagos pendientes en los diferentes modulos operativos de finanzas dentro del sistema.
- [ ] **Reportes Financieros:**
  - [ ] Estado de resultados (P&L).
  - [ ] Balance general (B/S).
  - [ ] Flujo de caja.
  - [ ] Reportes de ingresos y egresos.
  - [ ] Uso de Descuentos (Puntos y Vales).
  - [ ] Rpte de Gastos
  - [ ] Rpte Boletas de Compras
  - [ ] Gastos Generales
  - [ ] Rpte de Transferencias Efectivo
  - [ ] Rpte de Transferencias a Bancos
  - [ ] Rpte de Grupos de vendedores ( Rutas )
