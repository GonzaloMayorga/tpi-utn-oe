# Historias de usuario — Módulo Unificado de Tickets y SLA

**Caso:** NexoSoft Soluciones SRL (organización ficticia).  
**Alcance:** versión inicial del módulo, orientada a uso interno de Soporte e interacción con Desarrollo, QA y Gestión de Proyectos.  
**Nota:** estas historias formalizan funcionalidades descriptas en las entregas previas; no se encontraban redactadas expresamente en formato de historia de usuario.

## HU-01 — Registro y clasificación de tickets

**Como** integrante del área de Soporte, **quiero** registrar y clasificar incidentes y solicitudes de clientes, **para** centralizar la información y dar seguimiento a cada caso.

### Criterios de aceptación
- El registro identifica cliente, producto/servicio, título, tipo y severidad.
- El sistema asigna un identificador único y establece el estado inicial del ticket.
- Los campos obligatorios se validan y se muestran mensajes adecuados cuando falta información.
- Se registra la fecha y hora de creación.
- El proceso registra el ticket antes de validar su información; si faltan datos, solicita información al Cliente y vuelve a validarla al recibirla.

**Entidades relacionadas:** Cliente, Producto, Ticket.  
**Jira:** [NEXO-1](https://gonzalomayorga1408.atlassian.net/browse/NEXO-1)  
**Estado:** Por hacer, según información del autor; sin consulta directa del issue.

## HU-02 — Asignación y seguimiento de tickets

**Como** responsable de Soporte, **quiero** asignar responsables y registrar cambios de estado, **para** garantizar trazabilidad y coordinación con las áreas técnicas.

### Criterios de aceptación
- Un ticket puede estar inicialmente sin responsable y posteriormente asignarse a un usuario autorizado.
- El responsable puede consultar sus tickets asignados.
- Los cambios relevantes de estado o responsable se registran con fecha, usuario y descripción.
- Un ticket puede pasar por estados definidos de atención y terminar resuelto/cerrado conforme al procedimiento acordado.
- El cierre requiere una respuesta explícita de aceptación del Cliente; un rechazo devuelve el caso a la decisión de atención técnica o de Soporte.
- Una verificación QA no conforme devuelve el trabajo a análisis y corrección antes de comunicar la solución.
- La falta de respuesta del Cliente no implica aceptación ni cierre automático.

**Entidades relacionadas:** Usuario, Ticket, HistorialTicket.  
**Jira:** [NEXO-2](https://gonzalomayorga1408.atlassian.net/browse/NEXO-2)  
**Estado:** Por hacer, según información del autor; sin consulta directa del issue.

## HU-03 — Gestión de SLA y alertas

**Como** responsable de Gestión de Proyectos, **quiero** consultar los compromisos de SLA aplicables a cada ticket y recibir alertas ante vencimientos, **para** anticipar incumplimientos y priorizar la atención.

### Criterios de aceptación
- El ticket queda asociado con un acuerdo SLA aplicable al cliente.
- El sistema determina los plazos de primera respuesta y de resolución según la configuración vigente.
- Las alertas se producen de acuerdo con reglas de anticipación o vencimiento documentadas.
- Los eventos y acciones relevantes se pueden auditar mediante registros de seguimiento.
- Las fechas límite se calculan desde la creación del ticket según el acuerdo aplicable, sin imponer una duración fija ni reiniciar el plazo al derivar el caso.
- El BPMN representa vencimientos de primera respuesta y resolución mediante dos temporizadores no interruptivos; la atención continúa y las alertas se registran, notifican y revisan.
- La primera respuesta se registra al enviar el acuse en este modelo académico; el criterio contractual de respuesta válida y las reglas de pausas y calendario deben definirse al configurar un acuerdo real.

**Entidades relacionadas:** AcuerdoSLA, Ticket, HistorialTicket.  
**Jira:** [NEXO-3](https://gonzalomayorga1408.atlassian.net/browse/NEXO-3)  
**Estado:** Por hacer, según información del autor; sin consulta directa del issue.

## Correspondencia con el BPMN corregido

Los criterios locales se precisaron el 2 de noviembre de 2026, después de la entrega académica, para reflejar el [modelo corregido y sus comprobaciones](../bpmn/proceso-gestion-tickets.md). Esta revisión documental no acredita implementación de software ni actualización de los issues de Jira. El modelo representa alertas de vencimiento; no incorpora un tercer temporizador de anticipación.

## Gestión del backlog

El backlog se administra en Jira. Las tres historias se encuentran **Por hacer**, según la información del autor. La tarea de documentación BPMN, [NEXO-4](https://gonzalomayorga1408.atlassian.net/browse/NEXO-4), figuraba **En curso** en la última captura informada por el autor; no se afirma que ese siga siendo su estado actual. Las historias describen funcionalidades de un sistema propuesto, no software ya implementado. No se ha confirmado la existencia de tareas Jira para indicadores, consolidación del PDF ni revisión del README.

- **Tablero Jira:** [NEXO — tablero Kanban](https://gonzalomayorga1408.atlassian.net/jira/software/projects/NEXO/boards/2). Acceso del docente y acceso sin autenticación no confirmados
- **Repositorio GitHub:** [tpi-utn-oe](https://github.com/GonzaloMayorga/tpi-utn-oe)
- **Responsable del trabajo académico:** Gonzalo Gabriel Mayorga.

## Correspondencia con la planificación previa

| Historia | Actividades del Gantt (Entrega 2) | Entidades (Entrega 3) |
|---|---|---|
| HU-01 | A1, A2, A4, A7 | Cliente, Producto, Ticket |
| HU-02 | A2, A4, A7 | Usuario, Ticket, HistorialTicket |
| HU-03 | A1, A5, A6, A7 | AcuerdoSLA, Ticket, HistorialTicket |

La correspondencia es orientativa: las actividades A1–A9 y el plazo de 10 semanas son parte de la planificación hipotética del desarrollo del módulo, no la duración de preparación de este TPI.
