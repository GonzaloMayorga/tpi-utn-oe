# Modelado BPMN — Atención de tickets y control de SLA

**Proceso:** Gestión de incidentes y solicitudes de soporte de NexoSoft Soluciones SRL.

**Tipo:** proceso futuro propuesto (TO-BE), académico y no ejecutable (`isExecutable="false"`). No representa una implantación real.

## Participantes y responsabilidades

- **Cliente:** participante externo de caja negra. Sus actividades internas no se modelan; los intercambios se representan mediante flujos de mensaje.
- **NexoSoft:** participante con el proceso principal de registro, configuración SLA, atención, cierre y notificación.
- El subproceso expandido **Atender ticket** contiene cuatro lanes: **Soporte**, **Desarrollo y QA**, **Sistema de Tickets y SLA** y **Gestión de Proyectos**.
- Las tareas automáticas externas al subproceso son tareas de servicio. La rama externa de excepción de resolución identifica expresamente al Sistema y a Gestión de Proyectos en sus actividades.

Los flujos de secuencia permanecen dentro de su proceso o subproceso. Los siete flujos de mensaje conectan al Cliente con actividades o eventos de NexoSoft, nunca dos elementos del mismo participante.

## Flujo principal

1. La solicitud del Cliente inicia el proceso mediante un evento de mensaje.
2. El Sistema registra el ticket y su fecha de creación; consulta el AcuerdoSLA aplicable y calcula las fechas límite configuradas.
3. Comienza el subproceso de atención. Soporte envía el acuse y registra la primera respuesta. Para este modelo académico, ese acuse constituye la primera respuesta; su equivalencia con una respuesta válida debe definirse en el acuerdo de una eventual implementación.
4. Soporte valida cliente, producto y datos. Si están incompletos, solicita información, espera la respuesta del Cliente y vuelve a validar.
5. Soporte clasifica, prioriza y asigna responsable.
6. Una compuerta exclusiva determina si se necesita intervención técnica. Soporte resuelve los casos que no la requieren; Desarrollo y QA analiza, corrige y verifica los demás.
7. Si la verificación técnica no es conforme, el trabajo regresa a análisis y corrección. Si lo es, converge con la ruta de Soporte.
8. Soporte comunica la propuesta de solución y **espera explícitamente** la aceptación o el rechazo del Cliente mediante una tarea de recepción.
9. La aceptación termina la ruta principal de atención. El rechazo se registra y vuelve a la decisión de intervención técnica; no fuerza la nueva atención exclusivamente por Soporte.
10. Una vez terminado el subproceso, el Sistema cierra el ticket y actualiza historial e indicadores, notifica el cierre y finaliza el proceso.

Las compuertas divergentes tienen una condición conceptual para la rama afirmativa y una rama predeterminada negativa. La compuerta de convergencia unifica rutas exclusivas sin sincronizarlas como si fueran paralelas.

## Intercambios con el Cliente

| Mensaje | Origen | Destino |
|---|---|---|
| Solicitud de soporte | Cliente | Evento de inicio de NexoSoft |
| Acuse de recibo | Enviar acuse y registrar primera respuesta | Cliente |
| Solicitud de información | Solicitar información | Cliente |
| Información adicional | Cliente | Recibir información adicional |
| Propuesta de solución | Comunicar propuesta de solución | Cliente |
| Aceptación o rechazo | Cliente | Recibir aceptación o rechazo |
| Confirmación de cierre | Notificar cierre | Cliente |

## Control de SLA y excepciones

Se eliminaron la duración fija de una hora y el prefijo XML no declarado. Los dos temporizadores usan `bpmn:tFormalExpression` con el prefijo declarado y expresiones de fecha absoluta (`timeDate`):

| Control | Expresión conceptual | Actividad supervisada |
|---|---|---|
| Primera respuesta | `sla.fechaLimitePrimeraRespuesta` | Enviar acuse y registrar primera respuesta |
| Resolución | `sla.fechaLimiteResolucion` | Todo el subproceso Atender ticket, incluidas sus esperas y caminos alternativos |

Las fechas límite se obtienen del acuerdo aplicable y de la creación del ticket; no se reinicia el plazo al derivar a Desarrollo ni al solicitar más información. Calendario hábil, pausas, exclusiones, severidades y reaperturas pertenecen a las reglas configurables del SLA. El modelo no fija valores ni presupone que las esperas del Cliente suspendan el reloj. No modela reprogramación dinámica de temporizadores ni sintaxis ejecutable de un motor; esos aspectos corresponden a una eventual implementación.

Ambos eventos límite son **no interruptivos**: el vencimiento inicia una rama adicional sin cancelar la actividad supervisada. La atención puede continuar y la alerta no cierra el ticket ni sustituye la aceptación del Cliente. Un evento de fin normal consume únicamente el token que llega a él; no cancela las demás ramas activas.

**Efecto sobre la finalización:** «no interruptivo» no significa «sin efecto sobre el cierre». En la estructura del editable recuperado y de sus exportaciones:

- La alerta de primera respuesta incluye una revisión humana dentro del subproceso **Atender ticket**. Aunque el Cliente acepte la solución, el subproceso no termina mientras esa revisión continúe activa; por tanto, puede demorarse el cierre del ticket, ubicado después del subproceso.
- La alerta de resolución incluye una revisión humana en el proceso principal. El flujo del ticket puede llegar a su cierre, pero la instancia completa del proceso permanece activa hasta finalizar también esa rama.

Un subproceso permanece activo mientras tenga elementos activos, conforme a la [documentación de subprocesos BPMN de Camunda](https://docs.camunda.io/docs/components/modeler/bpmn/embedded-subprocesses/). Tener un camino hasta un evento de fin no garantiza que una tarea humana se complete. Por eso, los recorridos estáticos anteriores no demuestran ausencia de bloqueos operativos: una revisión pendiente puede retener la finalización indefinidamente, aunque no exista un bloqueo circular de conexiones.

**Límite del modelo académico:** no se garantiza independencia entre las alertas y la finalización. Se conserva esta característica expresamente documentada, sin rediseñar el proceso en esta revisión. Si una futura implementación exigiera independencia, debería desacoplar la atención humana de las alertas del ciclo de vida del ticket. No corresponde reemplazar los fines por terminaciones globales, porque cancelarían trabajo activo.

La falta de respuesta del Cliente mantiene activa la recepción y puede producir una alerta de resolución; no existe cierre por silencio. Un rechazo o una verificación técnica fallida vuelven a puntos consistentes de tratamiento.

## Datos e indicadores relacionados

| Elemento del proceso | Entidad preliminar de la Entrega 3 |
|---|---|
| Solicitante y servicio | Cliente, Producto |
| Identificación, estado y fechas | Ticket |
| Responsable asignado | Usuario |
| Reglas y fechas límite | AcuerdoSLA |
| Cambios, rechazos y cierre | HistorialTicket |

Los nombres usados en las expresiones son referencias conceptuales, no un esquema implementado. No se presume una entidad adicional para alertas. El flujo respalda [HU-01, HU-02 y HU-03](../gestion/historias-usuario.md) y las fuentes previstas en los [indicadores](../gestion/indicadores-control.md).

## Comprobaciones ejecutadas

Archivos disponibles: [editable BPMN](gestion-tickets.bpmn), [SVG](gestion-tickets.svg), [PNG](gestion-tickets.png) y [PDF del diagrama](gestion-tickets.pdf).

Antes de modificar archivos se revisaron el estado de Git, las ramas, los commits y el reflog. El commit `9b8de01` conserva la versión inicial. La versión corregida se recuperó del objeto local de Git `c1b39332f3d0ed896d325ee264bd2aa16945258d`, no asociado a un commit de las ramas actuales. Se comprobó que su huella SHA-256 coincide con la registrada durante la revisión técnica anterior y que las tres exportaciones son exactamente las de esa misma versión. No se generó un modelo nuevo ni se modificaron las exportaciones.

Se ejecutaron comprobaciones con herramientas temporales fuera del repositorio académico:

| Comprobación | Resultado |
|---|---|
| XML y esquemas oficiales BPMN 2.0 | Sin errores |
| Namespaces, identificadores y referencias | Sin errores |
| Flujos de secuencia dentro de su ámbito y mensajes entre participantes distintos | Sin errores |
| Compuertas exclusivas, conexiones, caminos a fin y temporizadores configurables | Sin errores |
| Cobertura gráfica BPMN DI | 40 formas y 41 conexiones, sin referencias inexistentes ni cobertura faltante |
| Recorridos estáticos del proceso | Ocho comprobados: Soporte, atención técnica, datos incompletos, retrabajo QA, rechazo del Cliente, dos alertas y registro a cierre |
| Pruebas del validador temporal | Once aprobadas |
| Editable y exportaciones frente a la revisión anterior | Huellas coincidentes |

En la revisión anterior, bpmn-js importó este mismo modelo sin advertencias y generó sus exportaciones con Chromium; Codex inspeccionó las imágenes renderizadas. En esta revisión se recuperó y verificó la misma versión, por lo que no se repitió la exportación.

Estos resultados se documentan aquí; no se incluyen herramientas de automatización ni informes técnicos separados como entregables. La comprobación estructural y los recorridos estáticos no son una simulación de ejecución ni demuestran que una tarea humana termine. Se mantiene la limitación de las ramas de alerta indicada anteriormente.

La autorrevisión conceptual comunicada por el autor no equivale a revisión independiente de pares ni acredita una validación manual completa en bpmn.io. El PDF histórico entregado por Moodle se conserva sin cambios y no se presume actualizado con estas correcciones posteriores.
