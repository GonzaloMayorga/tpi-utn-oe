# Mecanismos de control — NexoSoft

## Objetivo

Definir estándares, responsables y fuentes de verificación para evaluar la aceptación y el desempeño de la primera versión del Módulo Unificado de Gestión de Tickets y SLA. **Los valores son metas propuestas para una empresa ficticia; no se presentan como resultados efectivamente medidos.**

## Indicadores de aceptación del proyecto

| ID | Indicador / fórmula | Meta | Evidencia prevista | Responsable propuesto | Momento de control |
|---|---|---|---|---|---|
| M1 | Puesta en funcionamiento de primera versión (sí/no) | Al cierre de semana 10 | Acta de aceptación y verificación de despliegue interno | Gestión de Proyectos y Soporte | Semana 10 |
| M2 | Registros correctos / casos ensayados × 100 | ≥95% en 100 casos representativos | Planilla y ejecución de pruebas | QA | Semanas 8–9 |
| M3 | Percentil 95 (p95) del tiempo de respuesta en listado/detalle | ≤2 segundos, con 20 usuarios concurrentes | Informe de prueba de rendimiento reproducible | QA y Desarrollo | Semanas 8–9 |
| M4 | Escenarios de alerta SLA correctos / escenarios ensayados × 100 | ≥95% en 40 escenarios (≥38 correctos) | Matriz de reglas, logs y resultados de pruebas | QA y Soporte | Semanas 8–9 |
| M5 | Usuarios piloto capacitados / usuarios designados × 100 | ≥90% | Registro de asistencia y comprobación de tareas | Soporte | Antes de la puesta en marcha |

## Indicadores operativos complementarios (propuestos)

Estos indicadores agregan una perspectiva de control después de la puesta en marcha, **sin atribuirles objetivos históricos que no fueron definidos en las entregas anteriores**.

| Indicador | Fórmula / descripción | Uso | Frecuencia sugerida |
|---|---|---|---|
| Cumplimiento de primera respuesta SLA | Tickets respondidos dentro del plazo / tickets evaluables × 100 | Detectar demoras de atención | Semanal |
| Cumplimiento de resolución SLA | Tickets resueltos dentro del plazo / tickets resueltos evaluables × 100 | Evaluar eficacia del servicio | Mensual |
| Tasa de reapertura de la cohorte mensual de primer cierre | Tickets con primer cierre en el mes y al menos una reapertura posterior dentro de ese mismo mes / tickets con primer cierre en ese mes × 100 | Identificar reaperturas de la misma cohorte y período | Mensual, al cierre del mes |
| Tickets pendientes por severidad | Recuento de tickets sin cierre por severidad | Priorizar capacidad y escalamiento | Semanal |

Las fórmulas definitivas requieren acordar calendario hábil, pausas de reloj, exclusiones, severidades y reglas de reapertura durante el relevamiento (A1). No se inventan valores ni resultados.

**Criterio de la tasa de reapertura:** el período es un mes calendario, desde su inicio inclusive hasta el inicio del siguiente mes exclusive, usando una misma zona horaria de registro. El denominador cuenta tickets distintos cuyo **primer cierre** ocurrió dentro de ese período. El numerador cuenta únicamente tickets de esa misma cohorte con al menos una transición de cerrado a abierto posterior a su primer cierre y anterior al fin del mes. Cada ticket se cuenta una sola vez, aunque tenga varias reaperturas.

Las reaperturas de tickets cerrados por primera vez en meses anteriores no se mezclan con este denominador. Tampoco se incorporan retrospectivamente reaperturas ocurridas después del mes observado: este indicador mide reaperturas dentro del mes de primer cierre, no una tasa de reapertura de toda la vida del ticket, y los cierres cercanos al fin del mes tienen menos tiempo de observación. Si el denominador es cero, el resultado es **no aplicable**, no 0 %. Un rechazo del Cliente antes del cierre no se cuenta como reapertura. Esta definición no fija una meta ni presenta mediciones reales.

## Correspondencia con el BPMN corregido

La revisión del 2 de noviembre de 2026 es posterior a la entrega académica. El [modelo BPMN](../bpmn/proceso-gestion-tickets.md) registra la creación, la primera respuesta al enviar el acuse, el rechazo del Cliente y el cierre con actualización de historial e indicadores. Las fechas límite de primera respuesta y resolución proceden del AcuerdoSLA configurado; los dos temporizadores generan alertas de vencimiento sin interrumpir la atención. No se fija una duración contractual de una hora ni se presupone una pausa por espera del Cliente.

Para medir cumplimiento debe definirse qué evento acredita resolución y qué respuesta es válida según el acuerdo; no debe confundirse aceptación, finalización del subproceso y cierre. El rechazo antes del cierre se modela como retorno a atención; la tasa de reapertura debe distinguirlo de reabrir un ticket previamente cerrado. El modelo no produce resultados medidos ni sustituye la matriz de pruebas de M4. El objetivo M3 de dos segundos es una meta de rendimiento propuesta, no un plazo de SLA de tickets.

## Circuito de control y retroalimentación

1. **Estándar:** Dirección y Gestión de Proyectos aprueban metas, responsables y reglas.
2. **Medición:** QA y Soporte recopilan resultados de pruebas y registros operativos.
3. **Comparación:** se contrastan resultados contra estándares definidos.
4. **Corrección:** si hay desvíos, se revisan causas (capacidad, reglas, datos, fallas técnicas o capacitación).
5. **Retroalimentación:** se ajustan prioridades, procesos, capacitación y, si corresponde, acuerdos comerciales.

## Criterio de implantación

Como se estableció en la Entrega 2, los defectos críticos identificados en pruebas deben corregirse antes de la puesta en marcha, aun cuando esto desplace la fecha objetivo de la semana 10.

## Evidencia y seguimiento documental

Este documento está disponible en el repositorio local. No se ha confirmado una tarea Jira para indicadores ni se dispone de resultados medidos. El estado de las evidencias y el uso de ChatGPT y Codex se registran en el [registro de colaboración](../evidencias/registro-colaboracion.md).

## Referencias internas

- Entrega 1: organización como sistema abierto y retroalimentación.
- Entrega 2: objetivo general, M1–M5, Gantt e hitos.
- Entrega 3: organigrama, responsables y seis entidades del modelo preliminar.
