# 7. Vista de Despliegue

## Descripción General

La Vista de Despliegue describe la infraestructura técnica necesaria para ejecutar el sistema de gestión empresarial KMMotos, incluyendo los componentes de hardware, distribución geográfica, topología de red y entornos de cómputo. Esta sección también muestra cómo los componentes de software se asignan a los elementos de infraestructura, optimizando costos y recursos según las restricciones del proyecto.

## Entornos

KMMotos opera en varios entornos distintos para garantizar eficiencia, seguridad y estabilidad operativa:
- **Desarrollo**: Utilizado por el equipo de desarrollo para probar y actualizar sistemas antes del despliegue. Ejecutado localmente con Docker para facilitar la colaboración.
- **Pruebas**: Entorno aislado para pruebas rigurosas sin afectar los sistemas operativos. Replica la configuración de producción en escala reducida.
- **Producción**: El entorno operativo principal donde todas las tiendas y usuarios están activos y ejecutando operaciones comerciales en tiempo real.

## Componentes Clave de Infraestructura

1. **VPS Principal (Servidor de Producción)**: Hospeda toda la aplicación monolítica modular, optimizando costos ($250 USD/mes) versus soluciones de nube más costosas ($400-$700 USD/mes).
2. **Contenedores Docker**: Distribuidos en el VPS para gestionar servicios individuales de manera aislada pero coordinada.
3. **Proxy Inverso Nginx**: Ubicado como punto de entrada único, distribuye solicitudes entre el backend Laravel y frontend Vue.js.
4. **Base de Datos PostgreSQL**: Almacena datos transaccionales críticos (ventas, inventario, empleados, clientes) con alta integridad y consistencia.
5. **Base de Datos MongoDB**: Optimiza reportes financieros complejos y análisis de datos agregados sin sobrecargar PostgreSQL.
6. **Redis Cache**: Mejora rendimiento de consultas frecuentes y gestiona sesiones de usuarios de manera eficiente.

## Topología de Red

La infraestructura de KMMotos se distribuye geográficamente para soportar múltiples empresas y sucursales:

### Distribución Multi-Tenancy
- **Tenancy Central**: Hospedado en el VPS principal, gestiona consolidación de datos y administración global.
- **Tenancies Foráneos**: Representan las 6 empresas del conglomerado (KM Motos, All in One, KM Cars, Grupo KM Motos HN, Grupo KM Cars HN, Grupo Todo en Uno HN) distribuidas en zonas geográficas de Honduras.

### Arquitectura de Red
```
Internet
    ↓
Nginx Proxy Inverso
    ↓
┌─────────────────────────────────────┐
│           VPS Principal             │
│  ┌─────────────┐ ┌─────────────┐   │
│  │   Laravel   │ │   Vue.js    │   │
│  │   Backend   │ │  Frontend   │   │
│  └─────────────┘ └─────────────┘   │
│  ┌─────────────┐ ┌─────────────┐   │
│  │ PostgreSQL  │ │   MongoDB   │   │
│  └─────────────┘ └─────────────┘   │
│  ┌─────────────┐                   │
│  │    Redis    │                   │
│  └─────────────┘                   │
└─────────────────────────────────────┘
```

## Topología de Red

La red interna de la Estrella de la Muerte está organizada para garantizar un flujo de datos seguro y eficiente:
- **Red de Comando**: Conecta el comando central con sistemas críticos como el superláser y el núcleo del reactor.
- **Red de Seguridad**: Gestiona la vigilancia y los nodos de control de seguridad.
- **Red de Comunicaciones**: Dedicada a transmisiones externas e informes de estado internos.

### Diagrama

> **TODO:** _(Incluir un diagrama de despliegue que muestre la disposición de los componentes clave de infraestructura y las conexiones de red.)_

## Motivación

Esta estructura de despliegue respalda los objetivos de optimización de costos, eficiencia operativa y mantenibilidad que son esenciales para la viabilidad del proyecto KMMotos. Al consolidar la aplicación en un VPS económico y utilizar una arquitectura monolítica modular, el sistema minimiza la complejidad de infraestructura mientras mantiene la escalabilidad necesaria para soportar múltiples empresas y sucursales. La separación clara de responsabilidades entre contenedores Docker y la gestión centralizada de datos aseguran que el sistema pueda funcionar de manera estable y eficiente sin requerir especialistas en DevOps o infraestructuras costosas de nube.
