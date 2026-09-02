# Integración Investigar → Workspace

## Objetivo
Conectar evidencia aceptada desde Investigar con Workspace sin modificar automáticamente PESTEL, DOFA ni Objetivos/Indicadores.

## Regla de gobierno
**Recuperar ≠ generar ≠ aceptar ≠ aplicar.**

Una evidencia aceptada por un Proyecto Vivo queda **disponible para informar** el análisis. Su aceptación no crea, edita ni confirma factores estratégicos.

## Estados
1. `hallazgo` — fuente recuperada y guardada con procedencia.
2. `evidencia_disponible` — hallazgo valorado y calificado.
3. `propuesta_pendiente` — evidencia propuesta a un Proyecto Vivo.
4. `evidencia_aceptada` — una persona acepta su disponibilidad para el proyecto.
5. `aplicacion_pendiente` — Workspace puede mostrarla como evidencia contextual, pero aún no existe relación con un objeto estratégico.
6. `aplicada` — una persona vincula explícitamente la evidencia a un factor/decisión/objetivo existente o crea un nuevo borrador relacionado.

## Contrato mínimo de evidencia
```json
{
  "evidenceId": "E-00001",
  "findingId": "H-00001",
  "sourceId": "K-REG-01",
  "projectId": "selva-circular",
  "status": "accepted",
  "acceptedBy": "Carlos · Estudiante",
  "acceptedAt": "ISO-8601",
  "valuation": {
    "relevance": 1,
    "current": 1,
    "trust": 1,
    "note": ""
  },
  "application": {
    "status": "pending",
    "targetType": null,
    "targetId": null,
    "relation": null
  }
}
```

## Comportamiento en Workspace
- El panel **Evidencia contextual** muestra evidencias aceptadas del Proyecto Vivo.
- Cada evidencia muestra procedencia, valoración y estado de aplicación.
- Acciones disponibles: `Examinar`, `Vincular a objeto activo`, `Crear borrador relacionado`.
- `Vincular a objeto activo` requiere confirmación humana y crea una relación (`informed_by`, `supports`, `contradicts`), nunca copia ni reemplaza el objeto.
- `Crear borrador relacionado` crea un objeto nuevo en estado borrador y conserva la evidencia como origen.
- JARVIS puede explicar, contrastar y sugerir; no puede ejecutar `aceptar` ni `aplicar`.

## Regla de rechazo
Rechazar una propuesta al Proyecto Vivo cambia únicamente el estado de la propuesta. El hallazgo y la evidencia permanecen en Investigar/Biblioteca con su procedencia intacta.

## Criterios de regresión
- Aceptar evidencia no modifica PESTEL, DOFA u Objetivos.
- Aplicar evidencia requiere una acción humana explícita.
- La relación creada conserva `sourceId`, `findingId` y `evidenceId`.
- Una evidencia puede informar más de un objeto sin duplicar su identidad.
- Rechazar una aplicación no elimina la evidencia.
- OBJ-01 continúa como borrador hasta revisión humana.
