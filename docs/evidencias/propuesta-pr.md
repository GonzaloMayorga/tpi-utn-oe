# Propuesta local para el PR #1

Texto preparado para el [PR existente](https://github.com/GonzaloMayorga/tpi-utn-oe/pull/1), desde `docs/NEXO-4-bpmn` hacia `main`. No se publicó ni se modificó el estado del PR. La revisión es posterior a la entrega académica; el PDF histórico entregado por Moodle se conserva sin modificaciones.

## Título propuesto

NEXO-4: conservar BPMN corregido y completar documentación académica del TPI

## Descripción propuesta

Se recupera de los objetos locales de Git el editable BPMN corregido, conservando las exportaciones SVG, PNG y PDF correspondientes. El modelo usa fechas SLA configurables, representa los intercambios con el Cliente y contempla retornos por datos incompletos, rechazo y verificación técnica fallida. Se documenta expresamente que las revisiones humanas de las alertas no interruptivas pueden demorar la finalización.

El repositorio reúne README, historias de usuario, indicadores, documentación del proceso, registro de colaboración y las entregas académicas. Las historias y metas M1–M5 se conservan; la tasa de reapertura utiliza una cohorte y un período definidos. El autor aprobó conceptualmente los cinco Markdown mediante autorrevisión, que no constituye revisión independiente de pares.

Comprobaciones realizadas: XML/XSD, referencias, conexiones, cobertura gráfica, ocho recorridos estáticos y once pruebas con herramientas temporales externas al repositorio, sin errores. Las huellas del editable y sus exportaciones coinciden con la versión anteriormente importada en bpmn-js sin advertencias. También se comprobaron enlaces relativos y conservación del PDF histórico. Los resultados y límites se describen en la documentación académica, sin publicar un sistema de automatización ni informes técnicos separados.