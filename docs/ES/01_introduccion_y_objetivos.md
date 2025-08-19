# 1. Introducción y Objetivos

## Propósito

El alcance de este proyecto se centra exclusivamente en la creación de una aplicación web para gestionar las operaciones internas de KMMotos. No se contempla el desarrollo de aplicaciones móviles (iOS/Android) ni aplicaciones de escritorio y dado que es un dashboard privado para uso interno de la empresa, no es necesario implementar estrategias de SEO (Search Engine Optimization). Sin embargo, se prioriza la facilidad de uso y la optimización para el usuario final, garantizando una experiencia intuitiva y eficiente

## Principales Partes Interesadas

| Parte Interesada                                      | Rol                                                                          | Expectativas                                                                                                                                                                                                                      |
| ----------------------------------------------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Osman Garrido** (CEO)                               | Patrocinador del Proyecto / Líder Ejecutivo                                  | Retorno de inversión (ROI) positivo, cumplimiento de objetivos estratégicos, crecimiento y estabilidad de la empresa, y una visión clara del progreso del proyecto.                                                               |
| **Saul Cruz** (Coordinador de SAC)                    | Líder de Área / Usuario Clave                                                | Un sistema que mejore la eficiencia y calidad del servicio al cliente (SAC), fácil integración con procesos existentes y herramientas que optimicen la gestión de SAC.                                                            |
| **Eysthen Roney** (Coordinador de IT y Seguridad)     | Líder de Área / Experto en Seguridad                                         | Robustas medidas de ciberseguridad, cumplimiento de normativas de seguridad de la información, protección de datos sensibles, y planes de contingencia para cualquier incidente.                                                  |
| **Luis Arroyo** (Desarrollador)                       | Líder Técnico / Ejecutor de propuesta actual en base a propuestas anteriores | Requisitos claros y bien definidos, herramientas y recursos adecuados, soporte técnico cuando sea necesario, un ambiente de trabajo colaborativo que fomente la innovación, y el cumplimiento de los hitos técnicos del proyecto. |
| **Rod Rodriguez, Alexis Hernandez** (Desarrolladores) | Ejecutores del Proyecto / Equipo Técnico                                     | Requisitos claros y bien definidos, herramientas y recursos adecuados, soporte técnico cuando sea necesario, y un ambiente de trabajo colaborativo que fomente la innovación.                                                     |

### Antiguos Colaboradores del Proyecto

| Parte Interesada | Rol                   | Logros                                                                                                              |
| :--------------- | :-------------------- | :------------------------------------------------------------------------------------------------------------------ |
| Erick Zelaya     | Líder Técnico inicial | Elaboró la propuesta inicial del sistema multi-inquilino (multitenancy) en base a Laravel.                          |
| David Delcid     | Segundo Líder Técnico | Ejecutó la propuesta de infraestructura utilizando Docker y planteó la arquitectura del frontend en Sakai PrimeVue. |
| Jesus Peña       | Desarrollador         | Realizó contribuciones como desarrollador en el proyecto.                                                           |

## Principales Objetivos de Calidad

1. **Fiabilidad**: Asegurar que la aplicación funcione de manera consistente y sin errores, garantizando la disponibilidad de inventario, el procesamiento de pedidos y las transacciones financieras en todo momento. Esto incluye la capacidad de manejar picos de demanda sin fallos.
2. **Seguridad**: Proteger toda la información sensible de la empresa y los clientes, como datos financieros, inventarios y detalles personales. Se debe prevenir el acceso no autorizado, ataques maliciosos y garantizar la integridad de los datos para evitar fraudes o pérdidas.
3. **Mantenibilidad**: Diseñar la aplicación para que sea fácil de actualizar, depurar y adaptar a nuevas funcionalidades o cambios en los procesos de negocio. Esto permitirá incorporar rápidamente nuevos módulos, integrar futuras tecnologías o ajustar la normativa sin interrupciones significativas.
4. **Usabilidad**: Ofrecer una interfaz intuitiva y fácil de usar para todos los empleados (ventas, almacén, administración). El objetivo es minimizar la curva de aprendizaje, reducir errores operativos y agilizar las tareas diarias, lo que contribuirá a una mayor eficiencia y satisfacción del usuario

Estos objetivos son cruciales para el diseño y desarrollo del ERP Final, y servirán como guía para todas las decisiones técnicas y funcionales que se tomen.

# Fases de Desarrollo de KMMotos

El desarrollo de KMMotos se estructurará en seis fases interconectadas, cada una construyendo sobre la anterior para entregar funcionalidades más complejas y un sistema más robusto.

---

## Fase 1: Arquitectura e Infraestructura Básica

Esta fase sienta las bases técnicas del proyecto, estableciendo el entorno de desarrollo y las herramientas fundamentales.

**Propósito:**
El objetivo principal es crear un entorno de desarrollo reproducible y escalable que permita la ejecución de la aplicación. Se busca establecer una arquitectura e infraestructura sólida desde el inicio para facilitar el crecimiento futuro y la integración de nuevas funcionalidades.

**Componentes Clave:**

- **Docker:** Se utilizará Docker para contenerizar todas las aplicaciones y servicios. Esto garantiza un entorno de desarrollo consistente, facilita el despliegue y aísla las dependencias. Se tendrán contenedores separados para el **backend (Laravel)**, la **base de datos relacional (PostgreSQL)**, el **almacenamiento en caché (Redis)**, la **base de datos documental (MongoDB)**, el **frontend (Node.js para Vue.js)** y un **proxy inverso (Nginx)**. Todos estos contenedores operarán dentro de la misma red Docker.
- **Laravel 11 (Backend Monolítico Modular):** Será el framework principal para el desarrollo del backend. Se opta por una arquitectura monolítica modular para optimizar la interacción con los datos, lo cual es crucial para la eficiencia de la aplicación.
- **Tenancy for Laravel:** Permite soportar múltiples tiendas o sucursales dentro de una misma instancia de la aplicación, manteniendo los datos segregados pero utilizando una base de código común. Esto es fundamental ya que KMMotos planea expandirse con múltiples ubicaciones.
- **Laravel Octane con Swoole:** Mejorará significativamente el rendimiento del backend al mantener la aplicación en memoria, reduciendo la sobrecarga de arranque de cada solicitud HTTP. Esto es vital para garantizar una experiencia de usuario fluida, especialmente a medida que la aplicación crezca en funcionalidades y usuarios.
- **Laravel Sanctum:** Se encargará de la autenticación de la API y la gestión de sesiones para el SPA (Single Page Application) de Vue.js, proporcionando un mecanismo de autenticación ligero y seguro.
- **Vue.js (Frontend):** Se utilizará Vue.js para construir el lado del cliente de la aplicación.
- **Plantilla PrimeVue (Sakay):** Para optimizar el tiempo de desarrollo en UX/UI, se implementará la plantilla Sakay de PrimeVue. Esta plantilla ofrece una amplia gama de componentes pre-construidos y bien documentados, lo que permite enfocarse en la lógica del negocio sin invertir tiempo significativo en el diseño de la interfaz o la creación de componentes desde cero.
- **Elección sobre Nuxt.js:** Se opta por Vue.js directamente sobre frameworks como Nuxt.js porque no se requiere Server-Side Rendering (SSR) para esta aplicación interna. Esta decisión busca reducir la complejidad y la dependencia de un segundo backend (que Nuxt.js a menudo implica para SSR), manteniendo el frontend lo más ligero y ágil posible.
- **PostgreSQL:** Será la base de datos relacional principal para almacenar la mayoría de los datos transaccionales, como información de empleados, clientes, productos, inventario, facturación, etc.
- **Redis:** Se utilizará como caché de alta velocidad para mejorar el rendimiento de las consultas frecuentes y para la gestión de sesiones.
- **MongoDB:** Se utilizará para el resguardo y optimización de reportes e información financiera. Su naturaleza de base de datos de documentos flexible es ideal para almacenar datos agregados, logs de transacciones detallados o información financiera que podría requerir esquemas variables y consultas analíticas complejas, sin impactar el rendimiento de la base de datos transaccional principal.
- **Nginx (Proxy Inverso):** Actuará como el servidor web y proxy inverso, dirigiendo las solicitudes al contenedor de Laravel (para la API) y al contenedor de Node.js (para servir los archivos estáticos de Vue.js).

---

## Fase 2: Sistema POS (Punto de Venta) MVP (Producto Mínimo Viable)

Esta fase marca el inicio de la funcionalidad central del negocio: la capacidad de registrar ventas y gestionar la información básica de la empresa.

**Propósito:**
Se prioriza la creación de un sistema POS sobre cualquier otra fase, porque es el núcleo operacional de una empresa donde su modelo de negocio se centra en ventas. Sin la capacidad de registrar ventas, la información de inventario, clientes o finanzas carece de sentido práctico. Un POS funcional permite a la empresa comenzar a operar, generar ingresos y recopilar datos esenciales desde el día uno, sentando las bases para futuras expansiones.

**Módulos Clave:**

- **Gestión de Usuarios:**

  - Registro de Usuarios (nombre, información general, etc.).
  - Asignación de roles y permisos (integrado con Spatie Laravel Permission para seguridad).
  - Gestión de credenciales de acceso.

- **Gestión de Empleados:**

  - Registro de empleados (nombre, información de contacto, perfiles).

- **Gestión de Clientes:**

  - Registro de clientes (nombre, dirección, información de contacto, NIF/CI).
  - Gestión de datos de contacto y generales.
  - Clubes

- **Gestión de Mecanicos:**

  - Registro de Mecanicos (nombre, informacion de contacto, NIF/CI).

- **Gestión de Productos:**

  - Bodegas (Almacen)
  - Catálogo de productos (nombre, descripción, precio de venta, costo, SKU).
  - Categorización de productos
    - categorías, subcategorías, Rotacion, Aplicaciones.
  - Gestión de variantes de productos
    - marca, aplicaciones, modelo de motocicleta, Equivalencias.
  - Asociación de productos con imágenes (Libreria Media Library).

- **Gestión de Inventario (Básico):**

  - Registro inicial de existencias.
  - Importaciones de productos a inventario.
  - Visualización del nivel de existencias por producto.

- **Facturación (Ventas):**

  - Creación de nuevas ventas (selección de empleados, selección de clientes, selección de productos, descuentos, cálculo de totales).
  - Registro de métodos de pago (efectivo, tarjeta, transferencia, etc).
  - Generación de facturas (impresión).
  - Devoluciones y anulaciones de ventas.

- **Documentos (Ventas)**

  - Cotización.
  - Proforma.
  - Convercion de documentos a facturas (Cotizacion a proforma -proforma afecta inventario-, proforma a factura -Ya el inventario se modifico en la proforma-).

- **módulo de pagos.**

  - ver pagos
  - abono cliente

- **Gestión del manejo entre el tenancy central y los tenancies foraneos:**

  - Gestión del manejo entre el tenancy central y los tenancies foraneos.

---

## Fase 3: Sistema CRM (Customer Relationship Management)

Esta fase se enfoca en expandir la interacción con los clientes para mejorar la retención y las oportunidades de venta.

**Propósito:**
Una vez que las ventas básicas están operativas, es crucial comenzar a gestionar las relaciones con los clientes. Un CRM permite a la empresa entender mejor a sus clientes, anticipar sus necesidades y ofrecer un servicio más personalizado, lo que conduce a una mayor lealtad y ventas repetidas.

**Módulos Clave:**

- **módulo de Devoluciones.**

  - ver Devoluciones
  - Gestionar Devoluciones
  - Gestion de Devoluciones como metodo de pago.

- **Gestión de Otros metodos de pagos de Clientes:**

  - Creditos de tienda
  - Creditos por Devolucion
  - Listado de Creditos de Clientes

- **Gestión de Grupo de vendedores (Rutas):**

  - Gestion de clientes en rutas (Grupo de vendedores)
  - Clientes Atendidos.
  - Comisiones en rutas (Grupo de vendedores)

- **Gestión Detallada de Clientes:**

  - Segmentación de clientes (ej. por tipo de motocicleta, frecuencia de compra).
  - Campos personalizados para perfiles de clientes, (mapas de ubicaciones, preferencias, interaccion con otros modulos, etc).

- **Gestión de Interacciones con Clientes:**

  - Registro de llamadas, correos electrónicos, visitas, etc.
  - Historial de comunicaciones.

- **Tareas y Actividades para Empleados (Calendario):**

  - Asignación de tareas a empleados relacionadas con clientes (ej. seguimiento de cotizaciones, llamadas de post-venta).
  - Calendario de actividades.
  - Recordatorios y notificaciones de tareas pendientes.

- **Marketing Básico:**

  - Gestión de promociones y descuentos.

---

## Fase 4: Funciones de RRHH (Recursos Humanos)

Esta fase integra la gestión del personal directamente en el sistema, simplificando procesos administrativos internos.

**Propósito:**
Una vez que el negocio está operando y la base de clientes está siendo gestionada, es lógico incorporar la gestión de recursos humanos. Esto centraliza la información del personal y automatiza tareas administrativas, liberando tiempo para enfocarse en el crecimiento del negocio.

**Módulos Clave:**

- **Gestión Detallada de Perfiles de Empleados:**

  - Información personal, datos de contacto de emergencia, datos bancarios.
  - Historial laboral dentro de la empresa.
  - Documentos adjuntos (contratos, identificaciones, foto, etc).

- **Gestión de Planillas/Nóminas:**

  - DL Decimotercero
  - DL Decimocuarto
  - Registro de salarios y beneficios.
  - Cálculo de nóminas (sueldo base, horas extras, deducciones).
  - Generación de recibos de pago.
  - Gestión de impuestos y contribuciones.

- **Gestión de Horarios y Asistencias:**

  - Registro de entrada y salida (check-in/check-out).
  - Gestión de turnos.
  - Reportes de asistencia.

- **Vacaciones y Ausencias:**

  - Solicitudes y aprobación de vacaciones.
  - Registro de bajas por enfermedad u otras ausencias.

- **Acciones de Personal:**

  - Registro de ascensos, cambios de puesto, amonestaciones.
  - Evaluaciones de desempeño.
  - Gestión de capacitaciones.

- **Gestión de KPIS:**
  - Calendario de Tarea (Calendarios para que los empleados marquen sus tareas de trabajo)
  - Tareas de Perfiles (Asignacion de Tareas por sus respectivos perfiles)
  - Supervisar (Vista para que los supervisores puedan supervisar a los empleados)
  - Gestion de Supervisores (asignacion de supervisores y Configuración de Perfiles)

---

**Nota:** En este apartado Se deben abarcar modulos de trabajos administrativos para con los empleados y tiendas como los siguientes:

- **Solicitudes:**

  - Solicitar constancias
  - CheckList (De tiendas)
  - Documentacion Administrativas
  - Solicitudes y Seguimientos (Tickets de clientes para tareas dentro del sistema)
  - Solicitar Viáticos

---

---

## Fase 5: Gestión Avanzada de Inventario (Movimiento entre Tiendas) ERP (Enterprise Resource Planning)

Esta fase se enfoca en la complejidad de mover productos entre diferentes ubicaciones, crucial para empresas con múltiples sucursales. En este punto ya se comienza a transformar la aplicación en un ERP más completo y funcional.

**Propósito:**
A medida que KMMotos crece y potencialmente opera múltiples tiendas o bodegas, el movimiento de inventario se convierte en un proceso crítico. Esta fase asegura que los productos estén disponibles donde se necesitan, optimizando los niveles de stock y reduciendo pérdidas.

**Módulos Clave:**

- **Auditoria:**

  - Apertura de Tiendas (Gestion del proceso de creacion y Apertura de nuevas tiendas)
  - Auditoria de Tiendas (Gestion de la auditoria de tiendas para el manejo de inventario y control de stock)

- **Gestión de Inventario Dañado/Faltante:**

  - Productos dañados
  - Productos faltantes

- **Catalogo:**

  - Base imagenes
  - Galeria.

- **Múltiples Ubicaciones/Tiendas:** (Tenancy Central / Tenancies Foraneos)

  - Configuración y gestión de diferentes almacenes y tiendas.
  - Control de inventario por ubicación (Visualizacion de inventario de tenancies Foraneos).

- **Compras Locales (a Proveedores):**

  - Creación de órdenes de compra.
  - Recepción de productos y actualización de inventario.
  - Gestión de proveedores.

- **Packing:**

  - Preparación de pedidos para transferencia entre ubicaciones.
  - Generación de listas de empaque.

- **Pedidos de Productos a Bodega:**

  - Creación de solicitudes de reabastecimiento por parte de las tiendas.
  - Creación de solicitudes de reabastecimiento por parte de Grupos de Vendedores (Rutas).
  - Procesamiento y envío de pedidos desde la bodega central.

- **Solicitud de Complementos:**

  - Gestión de accesorios y piezas que complementan las motocicletas.
  - Pedidos específicos de complementos a la bodega o proveedores.

- **Solicitud de Surtidos:**

  - Procesos para solicitar una variedad de productos para mantener el stock adecuado en las tiendas.

- **Transferencias de Inventario:**

  - Gestión de transferencias entre Tiendas y Bodegas del mismo tenancy.
    - Convercion de transferencia a compra y venta local (Interna) entre empresas para el manejo de inventario y procesos financieros entre Empresas.
  - Seguimiento del estado de las transferencias.
  - Conciliación de inventario.

- **Gestión de Equipos / Materiales / Vienes de la Empresa:**

  - Registro de equipos y vienes de la empresa.
  - Gestión de equipos y vienes de la empresa.
  - Registro de Materiales e implementos de trabajo
  - Gestion de Surtido de Materiales e implementos de trabajo

- **Gestión de Aplicaciones Esternas:**

  - Integración con Shopify.
  - Integración con Supabase.

- **Importaciones**

  - Manejo de Status de pediodo de Importaciones de China
  - Valor Manual del Dolar

---

## Fase 6: Módulos de Finanzas

La fase final integra las operaciones financieras, proporcionando una visión completa de la salud económica de la empresa.

**Propósito:**
Una gestión financiera sólida es esencial para la sostenibilidad y el crecimiento de cualquier negocio. Esta fase centraliza los aspectos económicos, permitiendo un mejor control de flujos de efectivo, pagos y créditos.

**Módulos Clave:**

- **Optimización de Reportes con MongoDB:** Los datos financieros transaccionales se almacenarán en PostgreSQL para integridad y relaciones. Sin embargo, para la generación de reportes complejos y agregados, y para la optimización de consultas analíticas, se utilizará MongoDB. Esto permitirá pre-calcular y almacenar resúmenes de datos financieros en un formato flexible, facilitando la extracción rápida de información para análisis de tendencias, proyecciones y dashboards financieros, sin sobrecargar la base de datos transaccional.

- **Optimización de Reportes con Queues/Jobs:** Todos estos procesos de pre-cálculo y almacenamiento de resúmenes de datos financieros en un formato flexible deben procurarse realizar en colas de procesos controladas en segundo plano o, en su defecto, en un servidor aparte que ejecute dichas acciones como un servicio secundario que no afecte la operatividad de la empresa.

- **Cuentas Financieras:**

  - Registro de cuentas financieras donde se registran movimientos financieros, saldo guardado en cada tienda en efectivo y saldo en cuentas bancarias.

- **Catalogo Contable:**

  - Registro y mantenimiento de cuentas contables.
  - Categorización de cuentas Contables.
  - Configuracion de automatizacion de cuentas Contables.

- **Libro Diario:**

  - Registro de transacciones financieras.
  - Reportes financieros.

- **Contabilidad Básica:**

  - Plan de cuentas simplificado. (Catalogo Contable)
  - Asientos contables automáticos derivados de transacciones (Libro Diario) (ventas, compras, pagos).

- **Cuentas por Pagar ( Modulo Pago a Proveedores):**

  - Registro y seguimiento de facturas de proveedores.
    - Estas Facturas Vienen de las importaciones a inventario en dado caso de que dichas importaciones tengan factura asignada.
  - Programación y procesamiento de pagos a proveedores.
  - Historial de pago a Proveedores.
  - Gestion de Proveedores.

- **Gestión de Gastos (Anclado a Cuentas del Catalogo Financiero):**

  - Registro de gastos operativos (alquiler, servicios, combustible, etc.).
  - Categorización de gastos.
  - Reportes de gastos.

- **Gestión de Créditos (a Clientes - Mayoreo):**

  - Asignación y gestión de líneas de crédito a clientes.
  - Registro de pagos de créditos.
  - Reportes de cuentas por cobrar.

- **Transferencias de Efectivo entre Tiendas:**

  - Registro y seguimiento de movimientos de efectivo entre diferentes ubicaciones (Cuentas Financieras).
  - Ingreso manual de efectivo a las tiendas.

- **Apertura y Cierre de Caja:**

  - Conciliación de saldos de caja.

- **Boletas de Compra:**

  - Registro detallado de todas las compras realizadas por la empresa.
  - Asociación de compras con proveedores y categorías.

- **Acreedores:** (Gestion de deudas bancarias, creditod y/o prestamos Bancarios a las tiendas o empresas)

  - Registro de acreedores.
  - Control y manejo de acreedores en tiempo real.

- **Otros Acreedores:** (Gestion de deudas Minuristas, Creditos y/o prestamos de terceros a las tiendas o empresas)

  - Registro de otros acreedores.
  - Control y manejo de otros acreedores en tiempo real.

- **Control de Arrendamientos:**

  - Registro de arrendamientos.
  - Control de arrendamientos en tiempo real.

- **Control de Permisos Operativos:**

  - Registro de permisos operativos.(Municipalidad, Seguridad, etc.)
    - Control digital (subida de imagenes).
    - Pago Impuestos (Municipalidad, Seguridad, etc.)
    - Declaraciones, etc.
    - Alertas y notificaciones de permisos vencidos o por vencer.

- **Agenda de Pagos:**

  - Registro de pagos pendientes en los diferentes modulos operativos de finanzas dentro del sistema.

- **Reportes Financieros:**

  - Estado de resultados (P&L).
  - Balance general (B/S).
  - Flujo de caja.
  - Reportes de ingresos y egresos.
  - Uso de Descuentos (Puntos y Vales).
  - Rpte de Gastos
  - Rpte Boletas de Compras
  - Gastos Generales
  - Rpte de Transferencias Efectivo
  - Rpte de Transferencias a Bancos
  - Rpte de Grupos de vendedores ( Rutas )

---

## Notas y Consideraciones

Este documento es una guía estratégica y un plan de alto nivel, no un manual de implementación paso a paso. La creación de la aplicación KMMotos es un proceso dinámico, por lo que este plan está sujeto a cambios y evoluciones a medida que avanza el desarrollo y se identifican nuevas necesidades o mejoras.

Por favor, no lo utilice como una guía inmutable. Su propósito es establecer una visión clara, definir las fases, los módulos clave y la arquitectura técnica. Las decisiones específicas de implementación, los detalles técnicos y el orden preciso de las tareas pueden ajustarse para optimizar el proceso de desarrollo y responder a los desafíos que surjan.
