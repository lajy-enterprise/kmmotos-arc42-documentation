## 3. Contexto y Alcance

### Descripción General

Esta sección define los límites del sistema de gestión interno de **KMMotos**. Su alcance es la creación de una aplicación web para la gestión de las operaciones de las empresas que componen el conglomerado, identificando a las diferentes áreas y perfiles de empleados como los principales usuarios del sistema. No se contemplan aplicaciones móviles ni de escritorio. La aplicación es un _dashboard_ privado para uso interno, priorizando la usabilidad y la eficiencia para el usuario final.

---

### Contexto de Negocio

El sistema está diseñado para KMMotos, un conglomerado de seis empresas con múltiples sucursales (_tenancies_) distribuidas en diversas zonas geográficas de Honduras. La aplicación debe ser capaz de soportar a estas múltiples tiendas o sucursales dentro de una misma instancia, manteniendo los datos segregados pero utilizando una base de código común.

#### Distribución de Sucursales por Empresa

La distribución de las sucursales por empresa se organiza de la siguiente manera:

| Empresa                  | Sucursales                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| :----------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **KM Motos**             | KM Motos - SABA, KM Motos - LA PAZ, KM Motos - TOCOA, KM Motos - SIGUATEPEQUE, KM Motos - EL PROGRESO, KM Motos - CATACAMAS #1, KM Motos - EL PROGRESO #1, KM Motos - TELA, KM Motos - KENNEDY, KM Motos - FINANZAS, KM Motos - COMAYAGUA #1, KM Motos - EL PROGRESO #2, KM Motos - TELA BLANCA, KM Motos - COMAYAGUELA, KM Motos - CATACAMAS #1, KM Motos - JUTICALPA, KM Motos - JUTICALPA #1, BODGAS - KM MOTOS, KM MOTOS - GUACO, KM MOTOS - CULCUM |
| **ALL IN ONE**           | ALL IN ONE - SPS #1, ALL IN ONE - LA ESPERANZA #2, ALL IN ONE - SIGUATEPEQUE #2, ALL IN ONE - SALAMANCA, ALL IN ONE - SANTA BARBARA, ALL IN ONE - SANTA ANA, ALL IN ONE - SANTA ROSA #1, ALL IN ONE - CUEVA, ALL IN ONE - COMAYAGUA #5, ALL IN ONE - CHOLUTECA #2, ALL IN ONE - CHOLUTECA #3, ALL IN ONE - LA ESPERANZA #1, ALL IN ONE - SAN LORENZO, ALL IN ONE - SIGUATEPEQUE #1, ALL IN ONE - COMAYAGUA #2                                           |
| **KM CARS**              | KM CARS - YORO YORO, KM CARS - CHOLUTECA #2, KM CARS - MORAZAN YORO, KM CARS - LA ENTRADA COPAN #2, KM CARS - LA ENTRADA COPAN #1, KM CARS - MARCALA #1, KM CARS - GRACIAS LEMPIRA, KM CARS - LA CEIBA, KM CARS - VILLANUEVA, KM CARS - LA LIBERTAD #1, KM CARS - PUERTO CORTES, KM CARS - LA LIMA #1, KM CARS - DANLI #1, KM CARS - EL PORVENIR, KM CARS - CHOLOMA, KM CARS - COMAYAGUA #3                                                             |
| **GRUPO KM MOTOS HN**    | GRUPO KM MOTOS HN - CRUZ DE YOJOA, GRUPO KM MOTOS HN - MARCALA #2, GRUPO KM MOTOS HN - MONTO ORIENTAL, GRUPO KM MOTOS HN - SAN ESTEBAN, GRUPO KM MOTOS HN - COMAYAGUA #8, GRUPO KM MOTOS HN - SAN JUAN PUEBLO, GRUPO KM MOTOS HN - TEGUCIGALPA, GRUPO KM MOTOS HN - SAN MARCOS DE COLON, GRUPO KM MOTOS HN - VILLANUEVA #2                                                                                                                              |
| **GRUPO KM CARS HN**     | GRUPO KM CARS HN - SPS #3, GRUPO KM CARS HN - JUTICALPA #2, GRUPO KM CARS HN - COMAYAGUA #5, GRUPO KM CARS HN - SAN MARCOS DE OCOTEPEQUE, GRUPO KM CARS HN - DANLI #2, GRUPO KM CARS HN - S. DE R.L. DE C.V. - LA LIBERTAD #2, GRUPO KM CARS HN - LA ENTRADA COPAN #3, GRUPO KM CARS HN - COMAYAGUA #6, GRUPO KM CARS HN - MARCALA #3, GRUPO KM CARS HN - YORO YORO, GRUPO KM CARS HN - TEPAERA                                                         |
| **GRUPO TODO EN UNO HN** | GRUPO TODO EN UNO HN - COMAYAGUA #4, GRUPO TODO EN UNO HN - SANTA ROSA COPAN #2, GRUPO TODO EN UNO HN - JESE DE OTORO, GRUPO TODO EN UNO HN - TALIGUA #1, GRUPO TODO EN UNO HN - SIGUATEPEQUE #3, GRUPO TODO EN UNO HN - SAN JUAN, GRUPO TODO EN UNO HN - SAN MARCOS DE COLON                                                                                                                                                                           |

#### Distribución por Zonas y Áreas

Las sucursales de estas empresas están distribuidas en las siguientes zonas del país:

- Zona Norte
- Zona Sur
- Zona Centro
- Zona Occidente
- Zona Centro-Occidente
- Zona Nor-Oriente
- Zona 1 Mayoreo
- Zona 2 Mayoreo
- Zona Gerencial
- Zona Centro-Oriente
- Zona 3 Mayoreo

Cada empresas distribuye sus tiendas en varias zonas, estando las diferentes empresas distribuidas por todo el país.

#### Distribución Administrativa del personal

Internamente, la empresa posee una estructura administrativa con diversas áreas, cada una con perfiles específicos, organizadas jerárquicamente:

- **Gerencia General**: Perfil: **Gerente General**.
- **Gerencia Administrativa**: Perfil: **Gerente Administrativo**.
- **Supervisión de Ventas Tiendas**: Perfiles: **Gerente Comercial**, **Supervisor de Ventas**, **Asistente de Gerencia Comercial**.
- **Supervisión de Ventas Mayoreo**: Perfiles: **Jefe de Ventas de Mayoreo**, **Supervisor de Mayoreo**, **Gerente de Ventas de Mayoreo**.
- **Auditoría**: Perfiles: **Gerente de Auditoría**, **Auditor Operativo de Zona**, **Auditor Operativo de Estación**, **Auditor Operativo de Tienda**, **Auditor Operativo I de Almacén**, **Auditor Operativo II de Almacén**, **Auditor de Procesos**, **Comodín de Auditoría**.
- **Recursos Humanos**: Perfiles: **Gerente de Recursos Humanos**, **Coordinadora de Recursos Humanos**, **Técnico en Recursos Humanos**, **Psicóloga /Técnico en Recursos Humanos**, **Auxiliar de Recursos Humanos**, **Comodín - RRHH**.
- **Operaciones**: Perfiles: **Jefe de Operaciones**, **Coordinador de Mantenimiento**, **Auxiliar de Mantenimiento**, **Auxiliar de Suministros y Equipo**.
- **Finanzas**: Perfiles: **Director Financiero**, **Oficial Financiero**, **Cajera de Finanzas**, **Auxiliar Administrativo**, **Oficial Finanzas**, **Auxiliar Contable**, **Auxiliar Contable Mayoreo**, **Auxiliar Financiero**.
- **Mercadeo**: Perfiles: **Jefe de Mercadeo**, **Directora de Publicidad**, **Jefe de Mercadeo**, **Promotor de Marca**, **Gestor de Contenido**, **Diseñador Gráfico**, **Auxiliar de Mercadeo**, **Auxiliar de SAC y Mercadeo**.
- **IT y Seguridad**: Perfiles: **Coordinador de Tecnología de la Información y Seguridad**, **Auxiliar de Monitoreo y Seguridad**, **Auxiliar de Soporte Técnico**.
- **Gestión y Procesos**: Perfil: **Capacitación, Manuales y Procesos**.
- **Compras**: Perfiles: **Jefe de Compras**, **Supervisor de Compras**, **Analista de Compras**, **Auxiliar de Compras**.
- **Almacén**: Perfiles: **Coordinador General de Almacén**, **Jefe de Almacén**, **Coordinador de Despacho**, **Coordinador de Recepción**, **Analista de Gestión de Pedidos**, **Auxiliar de Almacén-Despacho**, **Auxiliar de Facturación**, **Auxiliar de Documentación**, **Auxiliar de Almacén-Empaque**, **Auxiliar de Almacén-Recepción**, **Conserje-Almacén**, **Comodín de Almacén**, **Auxiliar de Despacho**, **Auxiliar Almacén-Recepción**.
- **Créditos y Cobranza**: Perfiles: **Jefe de Crédito y Cobranza**, **Asistente de Jefe de Crédito y Cobranza**.
- **Servicio de Atención al Cliente (SAC)**: Perfiles: **Coordinador de Servicio al Cliente**, **Oficial Servicio al Cliente**, **Auxiliar de Servicio al Cliente**.
- **Administradores de Tienda**: Perfil: **Administrador de Tienda**.
- **Asesores de Ventas Mayoreo**: Perfiles: **Vendedor de Mayoreo**, **Auxiliar de SAC Mayoreo**.
- **Asesores de venta de Tienda**: Perfil: **Asesor de Ventas de Tienda**.
- **Cajeras Tiendas**: Perfil: **Cajera de Tienda**.
- **Auxiliar de Tienda y Conserjería**: Perfiles: **Auxiliar de Tienda**, **Conserje de Tienda**.

---

### Contexto Técnico

La aplicación web sirve como una plataforma centralizada para que las diferentes áreas y perfiles de KMMotos realicen sus tareas. Cada área utiliza módulos específicos de la aplicación para automatizar sus operaciones diarias.

- **Ventas (Punto de Venta MVP)**: El personal de ventas, incluyendo **Asesores de Venta de Tienda** y **Cajeras de Tienda**, utiliza los módulos de **facturación** y **gestión de productos** para crear ventas, aplicar descuentos, registrar métodos de pago y generar facturas. También se manejan devoluciones y anulaciones de ventas.
- **Almacén y Operaciones (Gestión Avanzada de Inventario)**: Perfiles como el **Coordinador General de Almacén** y los **Auxiliares de Almacén** se encargan de las **importaciones de productos**, la **gestión de inventario básico** y la visualización de existencias. En fases posteriores, utilizarán módulos para **auditoría** de tiendas, **transferencias de inventario** entre sucursales y la bodega central, y la **preparación de pedidos** (_packing_).
- **RRHH (Funciones de RRHH)**: El personal de RRHH, liderado por el **Gerente de Recursos Humanos**, gestiona los perfiles detallados de los empleados, la **nómina** (incluyendo cálculos de salarios y beneficios), los **horarios y asistencias**, y las solicitudes de vacaciones y ausencias.
- **Finanzas (Módulos de Finanzas)**: Los perfiles de esta área, como el **Director Financiero** y los **Auxiliares Contables**, gestionan las **cuentas financieras**, el **catálogo contable**, el **libro diario**, y las **cuentas por pagar** a proveedores. También utilizan el sistema para registrar gastos y gestionar créditos a clientes mayoristas. La optimización de los reportes financieros se realiza a través de **MongoDB** y procesos en segundo plano (_Queues/Jobs_).
- **SAC y Mayoreo (Sistema CRM)**: Equipos como el **Coordinador de Servicio al Cliente** (El Sr Saul Cruz Lider del Proyecto) y los **Vendedores de Mayoreo** gestionan las **devoluciones**, **créditos de tienda**, y las interacciones con los clientes. También utilizan módulos para la segmentación de clientes, el registro de interacciones y la asignación de tareas a empleados.
- **IT y Seguridad**: Su labor, a cargo del **Coordinador de Tecnología de la Información y Seguridad**, (El Sr Eysthen Roney Lider del Proyecto) se centra en la seguridad y el monitoreo, incluyendo la **protección de datos sensibles** y la prevención de accesos no autorizados. El sistema les proporciona una base robusta para implementar estas medidas.
