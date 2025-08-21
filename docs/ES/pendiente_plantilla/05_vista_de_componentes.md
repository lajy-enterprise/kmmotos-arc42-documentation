# 5. Vista de Bloques de Construcción

## Descripción General

La Vista de Bloques de Construcción proporciona una descomposición estática del sistema de gestión empresarial KMMotos, mostrando la estructura jerárquica de sus componentes principales. Esta sección desglosa la aplicación en "cajas blancas" (componentes de alto nivel) que contienen "cajas negras" (subcomponentes) organizados según las fases de desarrollo establecidas y la arquitectura monolítica modular.

## Componentes de Alto Nivel

1. **Sistema POS (Punto de Venta) MVP**: Núcleo operacional para el registro de ventas y gestión básica de la empresa.
   - *Módulo de Facturación*: Gestiona la creación de ventas, selección de productos, cálculo de totales y métodos de pago.
   - *Gestión de Productos*: Maneja el catálogo de productos, categorización, variantes, marcas y aplicaciones para motocicletas.
   - *Gestión de Inventario Básico*: Controla las existencias, importaciones de productos y visualización de niveles de stock.
   - *Gestión de Clientes*: Registra y mantiene información de clientes, mecánicos y clubes.

2. **Sistema CRM (Customer Relationship Management)**: Gestiona las relaciones con clientes y optimiza las oportunidades de venta.
   - *Módulo de Devoluciones*: Procesa devoluciones de productos y gestiona créditos por devolución.
   - *Gestión de Créditos de Tienda*: Administra créditos de clientes y métodos de pago alternativos.
   - *Gestión de Rutas (Grupos de Vendedores)*: Coordina vendedores, clientes en rutas y cálculo de comisiones.
   - *Marketing y Promociones*: Gestiona descuentos, promociones y comunicaciones con clientes.

3. **Sistema de RRHH (Recursos Humanos)**: Centraliza la gestión del personal y automatiza procesos administrativos.
   - *Gestión de Empleados*: Maneja perfiles detallados, documentación y historial laboral.
   - *Gestión de Nóminas*: Calcula salarios, beneficios, deducciones y genera recibos de pago.
   - *Control de Asistencias*: Registra horarios, turnos y reportes de asistencia.
   - *Gestión de KPIs*: Asigna tareas, supervisa empleados y evalúa rendimiento.

4. **Sistema ERP (Gestión Avanzada de Inventario)**: Maneja el movimiento de productos entre múltiples ubicaciones.
   - *Gestión Multi-Tenancy*: Controla inventario entre el tenancy central y tenancies foráneos.
   - *Transferencias de Inventario*: Gestiona movimientos entre tiendas, bodegas y conversión a compras/ventas internas.
   - *Gestión de Compras*: Administra órdenes de compra, recepción de productos y relaciones con proveedores.
   - *Auditoría de Tiendas*: Supervisa apertura de tiendas, auditorías de inventario y control de stock.

5. **Sistema de Finanzas**: Integra operaciones financieras y proporciona visión económica completa.
   - *Contabilidad Básica*: Maneja plan de cuentas, libro diario y asientos contables automáticos.
   - *Cuentas por Pagar*: Gestiona facturas de proveedores, pagos y relaciones comerciales.
   - *Gestión de Gastos*: Registra y categoriza gastos operativos vinculados al catálogo financiero.
   - *Reportes Financieros*: Genera estados de resultados, balances y análisis de flujo de caja.

6. **Infraestructura Técnica**: Base tecnológica que soporta todos los sistemas operativos.
   - *Backend Laravel*: Monolito modular con patrón Servicio-Repositorio, eventos y colas de procesos.
   - *Frontend Vue.js*: SPA con plantilla PrimeVue (Sakay) para interfaces de usuario eficientes.
   - *Bases de Datos*: PostgreSQL para datos transaccionales, MongoDB para reportes, Redis para caché.
   - *Contenedores Docker*: Orquestación de servicios con Nginx como proxy inverso.

## Diagrama

> **TODO:** _(Incluir un diagrama jerárquico que muestre estos componentes de alto nivel y sus subcomponentes para dar una representación visual de la arquitectura monolítica modular de KMMotos, organizados por las 6 fases de desarrollo.)_

## Motivación

Descomponer la arquitectura de KMMotos en bloques de construcción permite una mejor modularidad, mantenibilidad y escalabilidad dentro del marco monolítico modular. Al organizar los sistemas según las fases de desarrollo establecidas (POS MVP, CRM, RRHH, ERP, Finanzas e Infraestructura), es más fácil gestionar y actualizar componentes individuales sin interrumpir las operaciones del sistema completo. Esta estructura facilita el desarrollo incremental y la coordinación del equipo pequeño, optimizando el uso de recursos y manteniendo la coherencia transaccional crítica para un sistema de gestión empresarial.
