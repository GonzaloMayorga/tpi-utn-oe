# Modelado BPMN — Atención de tickets y control de SLA

**Proceso:** Gestión integral de incidentes y solicitudes de soporte de NexoSoft Soluciones SRL.  
**Tipo:** proceso futuro propuesto (TO-BE), mejorado mediante el Módulo Unificado de Tickets y SLA.  
**Estado:** diseño para modelar y validar; no representa una implantación real.

## Objetivo y alcance

Desde que el cliente comunica un incidente o solicitud hasta que Soporte cierra el ticket, con asignación, resolución, validación, notificaciones y control del SLA. Integra HU-01, HU-02 y HU-03.

## Participantes BPMN

- **Pool 1 — Cliente (externo):** comunica la solicitud, aporta información faltante, recibe respuesta y acepta o rechaza la solución.
- **Pool 2 — NexoSoft (interno):** incluir lanes para **Soporte**, **Sistema de Tickets (automatizado)** y **Desarrollo/QA**. Gestión de Proyectos puede intervenir como lane adicional en el tratamiento de escalaciones, si esa intervención se representa explícitamente.

**Notación:** utilizar *sequence flows* dentro de cada pool y *message flows* para los mensajes entre Cliente y NexoSoft. Los límites de las lanes no impiden secuencias internas. No conectar pools diferentes mediante *sequence flow*.

## Flujo principal propuesto

1. **Cliente:** evento de inicio por necesidad de soporte; envía incidente o solicitud.
2. **Sistema:** recibe y registra ticket, asigna ID y fecha de creación.
3. **Soporte:** valida cliente, producto e información recibida.
4. **Compuerta exclusiva (XOR): ¿Información suficiente?**
   - **No:** Soporte solicita detalles; Cliente aporta datos; el proceso regresa a validación.
   - **Sí:** continuar.
5. **Soporte:** clasifica tipo, severidad y prioridad según reglas establecidas.
6. **Sistema:** identifica el AcuerdoSLA aplicable y calcula plazos.
7. **Soporte:** asigna responsable y determina modalidad de atención.
8. **Compuerta exclusiva (XOR): ¿Requiere intervención técnica?**
   - **Sí:** Desarrollo/QA analiza, corrige y verifica; devuelve resultado a Soporte.
   - **No:** Soporte atiende y prepara respuesta.
9. **Soporte:** comunica propuesta de resolución al cliente.
10. **Cliente:** confirma o rechaza la resolución.
11. **Compuerta exclusiva (XOR): ¿Resolución aceptada?**
    - **No:** Soporte reabre/continúa el caso y vuelve al tratamiento.
    - **Sí:** continuar.
12. **Sistema:** registra cierre, fecha/hora e historial de cambios y actualiza información para indicadores.
13. **Fin:** ticket cerrado.

## Excepción temporal — control de SLA

Mientras el ticket permanece abierto o en atención, debe comprobarse el cumplimiento del tiempo de primera respuesta y de resolución. Modelar un **evento temporizador límite no interruptivo** o un **subproceso de monitoreo con timer** vinculado a la fase de atención, según el nivel de detalle elegido. Ante vencimiento o umbral de alerta:

1. El Sistema registra el evento y genera alerta.
2. Soporte analiza el atraso y, cuando corresponde, escala a Gestión de Proyectos.
3. La atención del ticket continúa; la alerta no equivale a cierre automático.

**Precisión:** el temporizador y sus condiciones se definirán en el relevamiento; no inventar umbrales ni calendarios para el SLA.

## Objetos de datos relacionados

| Elemento del proceso | Entidad preliminar (Entrega 3) |
|---|---|
| Identificación del solicitante y servicio | Cliente, Producto |
| Registración, estado y fechas | Ticket |
| Persona asignada | Usuario |
| Plazos de respuesta y resolución | AcuerdoSLA |
| Trazabilidad de cambios | HistorialTicket |

El diccionario inicial es conceptual; no se presupone persistencia adicional para notificaciones o registros de monitoreo.

## Guía de notación para el archivo .bpmn

- Usar eventos de inicio y fin reconocibles.
- Tareas de usuario para actividades humanas; tareas de servicio o automatizadas para acciones del sistema.
- Compuertas exclusivas etiquetadas con preguntas y salidas claramente rotuladas Sí/No.
- No utilizar compuertas para representar simplemente pasos sucesivos.
- Distinguir los mensajes Cliente↔NexoSoft con líneas discontinuas de mensaje.
- Verificar que las ramas de excepción vuelvan a un punto consistente y que ninguna ruta quede sin continuidad.
- Exportar una imagen legible y conservar el editable `gestion-tickets.bpmn`.

## Entregables y validación

- [✅] `gestion-tickets.bpmn`: archivo estándar editable y validado en un modelador BPMN.
- [✅] `gestion-tickets.png` o `.svg`: exportación legible para incluir en el PDF.
- [✅] Validación de pools, lanes, gateways, eventos y flujos.
- [✅] Referencia al diagrama desde README y documento final.
