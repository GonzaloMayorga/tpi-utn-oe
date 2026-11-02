# Registro de evidencias — GitHub, Jira y revisión del TPI

**Proyecto:** NexoSoft Soluciones SRL — Módulo Unificado de Tickets y SLA.  
**Autor del trabajo académico:** Gonzalo Gabriel Mayorga.  
**Actualización documental:** 2 de noviembre de 2026 (Argentina).  
**Propósito:** registrar acciones realizadas, fuentes y evidencias disponibles para la Entrega 4. Se distinguen comprobaciones técnicas, información aportada por el autor y verificaciones pendientes.


## 1. Accesos

| Recurso | Enlace o ubicación | Verificación |
|---|---|---|
| Repositorio GitHub | [tpi-utn-oe](https://github.com/GonzaloMayorga/tpi-utn-oe) | Repositorio identificado como público y PR consultado. |
| Tablero Kanban Jira | [Tablero NEXO](https://gonzalomayorga1408.atlassian.net/jira/software/projects/NEXO/boards/2) | Enlace aportado por el autor. La herramienta web no pudo acceder al tablero; esto no demuestra que sea inexistente ni confirma permisos del docente. |
| Pull Request | [PR #1](https://github.com/GonzaloMayorga/tpi-utn-oe/pull/1) | El autor efectuó una autorrevisión del Pull Request. Esta acción no constituye una revisión independiente de pares y, por lo tanto, ese requisito académico permanece pendiente. |
| Modelo BPMN | [Editable](../bpmn/gestion-tickets.bpmn), [SVG](../bpmn/gestion-tickets.svg), [PNG](../bpmn/gestion-tickets.png) y [PDF del diagrama](../bpmn/gestion-tickets.pdf) | Versión corregida recuperada de Git, validada técnicamente y correspondiente a las exportaciones conservadas. |
| PDF consolidado final | [TPI_Final_Organizacion_Empresarial_Mayorga_Gonzalo.pdf](../entregas/TPI_Final_Organizacion_Empresarial_Mayorga_Gonzalo.pdf) | Archivo presente y legible por `pdfinfo`: 27 páginas. Esta comprobación no acredita una revisión completa de su contenido ni de los enlaces de portada. |

## 2. Historial de versionado

Datos obtenidos del historial Git local. Las fechas de los commits corresponden al huso horario de Argentina. La rama indicada es una referencia actual que contiene el commit, no un dato de creación almacenado en el commit.

| Fecha | Rama de referencia | Commit | Descripción del cambio | Evidencia |
|---|---|---|---|---|
| 2026-11-01 | `main` | `92d45b6` | Commit inicial (`first commit`). | [Commit](https://github.com/GonzaloMayorga/tpi-utn-oe/commit/92d45b6) |
| 2026-11-01 | `docs/NEXO-4-bpmn` | `9b8de01` | Incorporación del modelo BPMN, exportaciones y documentación del proceso. | [Commit](https://github.com/GonzaloMayorga/tpi-utn-oe/commit/9b8de01) |

Las correcciones posteriores a la entrega están en el espacio de trabajo de `docs/NEXO-4-bpmn` y aún no tienen un commit propio. No se realizó push, merge ni modificación del PR. La rama coincide con el origen del PR #1; se preparó una [propuesta local de título y descripción](propuesta-pr.md).

### Pull Request y revisión de pares

- **PR:** [#1 — Documentación BPMN](https://github.com/GonzaloMayorga/tpi-utn-oe/pull/1).
- **Rama de origen y destino:** `docs/NEXO-4-bpmn` → `main`.
- **Autorrevisión:** Gonzalo Gabriel Mayorga informó que realizó una autorrevisión del PR y aprobó conceptualmente los cinco Markdown para su incorporación, con los ajustes documentales solicitados. Esta autorrevisión **no constituye una revisión independiente de pares** ni acredita una aprobación formal registrada en GitHub.
- **Revisor/a independiente:** no hay revisión de pares confirmada.
- **Comentarios de revisión:** no se dispone de observaciones de pares documentadas.
- **Ajustes derivados de la autorrevisión:** nombre y enlace del PDF existente, distinción entre autorrevisión y revisión de pares, alcance de las ramas de alerta, definición de tasa de reapertura y comprobación de enlaces locales. No se atribuyen a un revisor independiente.
- **Resultado:** abierto en la última consulta; aprobación conceptual de los Markdown por el autor, sin aprobación independiente ni merge acreditados.
- **Fecha de revisión independiente o resolución:** no registrada; esos hitos no están confirmados. La autorrevisión se registra a partir de la confirmación del autor en esta conversación, sin inventar una fecha de evento en GitHub.

El trabajo es individual. La revisión de pares y su resolución siguen pendientes como evidencia académica; la inspección asistida por Codex no sustituye esa revisión.

## 3. Gestión ágil en Jira

Los enlaces se construyen con el dominio del tablero y las claves confirmadas por el autor. Los estados proceden de su información, no de una consulta directa de Jira.

| Historia / tarea | Clave Jira | Último estado informado | Evidencia / fuente |
|---|---|---|---|
| HU-01 — Registro y clasificación de tickets | NEXO-1 | Por hacer | [Issue](https://gonzalomayorga1408.atlassian.net/browse/NEXO-1); informado por el autor. |
| HU-02 — Asignación y seguimiento | NEXO-2 | Por hacer | [Issue](https://gonzalomayorga1408.atlassian.net/browse/NEXO-2); informado por el autor. |
| HU-03 — Gestión de SLA y alertas | NEXO-3 | Por hacer | [Issue](https://gonzalomayorga1408.atlassian.net/browse/NEXO-3); informado por el autor. |
| Documentación BPMN | NEXO-4 | En curso en la última captura informada; estado actual no comprobado | [Issue](https://gonzalomayorga1408.atlassian.net/browse/NEXO-4); referencia a captura aportada por el autor, no incorporada como archivo en este registro. |

**Indicadores y consolidación del PDF:** no está confirmada la existencia de tareas Jira para estas actividades. No se les asignan claves ni estados ficticios. La documentación de indicadores existe y el autor informó que generó el PDF final; esto no acredita su seguimiento en Jira.

**Comprobación de enlaces:** se contrastaron dominio, tablero y claves NEXO-1 a NEXO-4 con los datos aportados por el autor. La herramienta web no pudo consultar esas cinco direcciones el 2 de noviembre de 2026; no se verificaron sus contenidos ni estados actuales.

**Acceso docente:** aún no confirmado en este registro, aunque la entrega ya se realizó. Para completar las evidencias publicadas debe asegurarse un medio de consulta de las historias y el tablero. Si Jira requiere autenticación, se deberá facilitar acceso al docente y/o aportar una exportación o capturas conforme a lo admitido por la cátedra, indicando la restricción.

## 4. Observaciones docentes

**Entrega 3:** según el autor, recibió una devolución completamente positiva. El profesor destacó el organigrama, las seis entidades del diccionario de datos, sus relaciones y la coherencia con las entregas anteriores.

**Entregas 1 y 2:** sus devoluciones no están disponibles para este registro. Esto no implica que no hayan existido.

## 5. Transparencia y criterio sobre IA

**Herramientas utilizadas:** ChatGPT y Codex, confirmadas por el autor.

Las siguientes solicitudes se describen por su finalidad; no son transcripciones literales de prompts. No se atribuyen correcciones humanas específicas que no estén documentadas.

| Herramienta y finalidad de la solicitud | Aporte | Validación respaldada / límite | Documento o evidencia |
|---|---|---|---|
| ChatGPT: organizar y consolidar las entregas académicas | Asistencia en la organización documental y consolidación | Uso y generación del PDF confirmados por el autor; archivo final presente, con comprobación de apertura y número de páginas. | [Entregas disponibles](../entregas/); nombre del consolidado registrado en la sección 1. |
| ChatGPT: redactar y estructurar historias de usuario | Formalización de HU-01, HU-02 y HU-03 | Documento local disponible; aprobación conceptual del autor en su autorrevisión, sin atribuir correcciones humanas específicas. | [Historias de usuario](../gestion/historias-usuario.md). |
| ChatGPT: definir indicadores coherentes con el proyecto | Propuesta de metas, fórmulas, fuentes y responsables | Documento local aprobado conceptualmente por el autor; las metas no son mediciones reales. | [Indicadores de control](../gestion/indicadores-control.md). |
| ChatGPT: generar el modelo BPMN del proceso de tickets | Modelo editable y exportaciones | Versión inicial asistida por ChatGPT; corregida posteriormente con Codex. No se atribuye una validación humana en bpmn.io. | [Proceso, archivos y comprobación técnica](../bpmn/proceso-gestion-tickets.md). |
| Codex: corregir el BPMN, revisar coherencia y preparar el repositorio | Corrección de temporizadores, mensajes, rutas y DI; regeneración de exportaciones y actualización documental | Editable corregido recuperado de un objeto local de Git. Se repitieron validación XSD, comprobaciones estructurales, ocho recorridos estáticos y once pruebas con herramientas temporales externas a la entrega; sin errores. Se comprobó correspondencia con las exportaciones anteriores. No constituye aprobación independiente. | [Comprobaciones BPMN y alcance](../bpmn/proceso-gestion-tickets.md#comprobaciones-ejecutadas). Los resultados se documentan en Markdown, sin informes técnicos separados como entregables. |

La selección final, la validación conceptual, la exactitud del BPMN y la autoría del proyecto corresponden al estudiante. La devolución docente positiva de la Entrega 3 no se extiende automáticamente a los nuevos documentos, al BPMN ni al PDF consolidado.

## 6. Límites y evidencias no disponibles

La validación humana en bpmn.io, las devoluciones de las Entregas 1 y 2, las tareas Jira de indicadores/PDF y las mediciones operativas no están acreditadas. No se presentan como realizadas ni se convierten en requisitos adicionales para publicar esta revisión técnica. La revisión independiente de pares y el acceso a Jira continúan pendientes de acreditación. El PDF entregado ya está incorporado; su revisión integral permanece pendiente. El editable y las exportaciones están disponibles; el alcance académico no incluye un sistema de validación automatizada. Las limitaciones de finalización de las alertas permanecen documentadas.
