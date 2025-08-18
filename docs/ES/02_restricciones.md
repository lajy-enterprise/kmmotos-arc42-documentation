# 2. Restricciones

## Descripción General

Esta sección describe las restricciones que afectan el diseño y desarrollo de la arquitectura de la Aplicacion KmMotos, destacando que la misma se construye (En el Backend) bajo un marco Monolitico Modular basado en un patron de diseño Servicio Repositorio con implementacion de eventos y uso de colas de procesos. Las restricciones incluyen factores externos, así como factores internos.

La elección de la arquitectura actual para la aplicacion es una decisión estratégica que se alinea directamente con las limitaciones y necesidades específicas del proyecto. Esta aproximación no solo es viable, sino que también se presenta como la opción más eficiente y coherente dadas las circunstancias actuales que se expresan a continuación.

## Restricciones Externas

- **Limitaciones Presupuestarias:**

  - El **rechazo de infraestructuras en la nube** (como AWS o Google Cloud) debido a su costo/beneficio es un factor determinante. El **monolito modular se alinea perfectamente con la estrategia de optimización de costos**, ya que puede desplegarse de manera eficiente en un **VPS más económico** (aproximadamente $250 USD/mes), lo que contrasta con los costos significativamente mayores de otras soluciones ($400-$700 USD/mes para Amazon EKS, por ejemplo). Esto maximiza el rendimiento dentro de los límites presupuestarios.

- **Restricciones de Recursos de Infraestructura:**

  - El **entorno de despliegue actual es un VPS**, que por naturaleza tiene **recursos limitados**. El **monolito modular optimiza el uso de estos recursos**, siendo más **eficiente en el consumo de RAM y CPU** al consolidar la aplicación en un solo proceso.
  - La **ausencia de un especialista en DevOps** para plataformas de nube representa una barrera significativa. El **monolito modular requiere menos especialización** para su despliegue y mantenimiento en un VPS, lo que lo hace viable con los recursos humanos disponibles.

- **Operacionalización y Escalabilidad del Despliegue:**
  - La **configuración y el mantenimiento de herramientas de orquestación** como Kubernetes en un VPS es un desafío considerable. El **monolito modular simplifica el proceso de despliegue en un VPS**, pudiendo escalar horizontalmente (mediante múltiples instancias detrás de un balanceador de carga como NGINX) de manera efectiva y sin la necesidad de estas herramientas complejas, lo que lo hace más adecuado para el entorno operativo actual.
  - Incluso con la necesidad de **integraciones con APIs de terceros** (como Google Sheet, Google Drive, Contabilidad, Proveedores, SocializerX, Twilio), un monolito modular bien diseñado puede encapsular esta lógica en **módulos o servicios internos dedicados**. Esto permite manejar la volatilidad y los diferentes formatos de datos de estas APIs de forma controlada y robusta, manteniendo la estabilidad del núcleo del POS.

## Restricciones Internas

- **Optimización del Equipo y Recursos Humanos:**

  - Contamos con un **equipo de desarrollo pequeño**. En este contexto, un **monolito modular es considerablemente más manejable y fácil de coordinar**, permitiendo al equipo concentrarse en entregar funcionalidad de valor sin la sobrecarga que implicaría la gestión de arquitecturas distribuidas.
  - La **curva de aprendizaje se minimiza** enormemente, ya que el equipo puede capitalizar su experiencia en un _stack_ tecnológico consolidado (como Laravel). Esto se traduce en un **desarrollo más rápido y con menos errores iniciales**, ya que la atención se centra en la construcción de la aplicación, no en complejidades de infraestructura ajenas al núcleo del problema.

- **Coherencia y Estabilidad Tecnológica y de Datos:**

  - La **mala normalización de la base de datos** en la aplicación de producción existente (Mi POS Virtual), que ha generado cuellos de botella históricos, se puede **abordar y corregir de manera más controlada** dentro de un monolito modular. Esto facilita la refactorización y asegura la **integridad de los datos**, un aspecto crítico en un sistema POS (que es la Face Inicial del Desarrollo actual).
  - La **naturaleza inherente de un sistema POS (Face Central del Desarrollo Actual)** implica que sus módulos están profundamente interconectados y son transaccionales (por ejemplo, una venta involucra inventario, cliente, factura, pago). Una **arquitectura monolítica modular maneja estas transacciones complejas y atómicas de forma nativa**, lo que garantiza la **consistencia de datos** y simplifica enormemente la depuración, ya que toda la lógica relacionada reside en un mismo contexto.

- **Desafíos Operacionales y de Mantenimiento:**

  - La **gestión del entorno de desarrollo local se simplifica drásticamente**. Los desarrolladores pueden levantar la aplicación con agilidad, lo que incrementa la productividad y elimina barreras iniciales significativas.
  - Aunque existen **cargas _batch_ pesadas** y **solicitudes de implementaciones exigentes** (como las observadas en la aplicación de producción actual, que renderiza el _frontend_ desde el servidor y causa cargas pesadas a la base de datos), un **monolito modular bien estructurado puede incorporar patrones de diseño eficientes** (como servicios, repositorios y sistemas de colas) para manejar estas tareas de forma **asíncrona y optimizada**, sin introducir complejidad innecesaria en la operación general.
  - La **falta histórica de supervisión en el desarrollo** puede mitigarse en un monolito modular, ya que su estructura consolidada facilita la implementación y el cumplimiento de **estándares de codificación y procesos de revisión de código centralizados**, promoviendo una mayor calidad y consistencia a lo largo del tiempo.

- **Gestión de Riesgos y Fallos:**
  - Para un sistema donde la **coherencia de datos es crítica** (inventario, pagos, facturas), el **monolito modular garantiza la coherencia transaccional de forma nativa**. Las llamadas entre módulos son **internas y extremadamente rápidas**, minimizando la latencia y ofreciendo una experiencia de usuario fluida. Esto contrasta con los desafíos de inconsistencia de datos distribuidos y la mayor latencia que surgen al dividir el POS sin una justificación clara.
  - La **depuración se simplifica** notablemente al tener una única base de código y un único punto de entrada, lo que agiliza la identificación y resolución de problemas.

## Justificación de la Arquitectura Monolítica Modular para la Aplicación en Base a las restricciones actuales del Proyecto

La elección de una **arquitectura monolítica modular** para el _backend_ de la aplicación centrada en la funcionalidad de un Punto de Venta (POS - Face Central del Desarrollo) de KMMOTOS no es arbitraria; es una **respuesta estratégica y eficiente a las limitaciones y necesidades específicas** del proyecto. Lejos de ser una imposición, esta elección se alinea perfectamente con los recursos disponibles y los objetivos de desarrollo, destacando sus beneficios inherentes.

En conclusión, la **arquitectura monolítica modular no es solo una opción viable, sino la más sólida y apropiada** para KMMOTOS, dado el conjunto de restricciones internas y externas. Permite una **rápida entrega de valor**, garantiza la **integridad transaccional**, optimiza el **uso de recursos y presupuesto**, y se alinea con la **capacidad operativa del equipo**, sentando una base robusta para el crecimiento futuro.
