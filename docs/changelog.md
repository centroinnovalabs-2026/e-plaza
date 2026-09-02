# Changelog — e-Plaza MARK I

## Inicio del repositorio persistente

- Se establece GitHub como fuente persistente del proyecto.
- Se crea la estructura documental del Plan Maestro.
- La incorporación del prototipo funcional se realizará desde el último maestro verificable, sin declarar versiones históricas como recuperadas hasta comprobar su contenido.

## Recuperación de fuentes históricas y corrección Retro 72

- Se recuperaron dos referencias funcionales del usuario: una versión donde el menú de usuario operaba correctamente y el último prototipo Avance 72.
- Se identificó la causa de la regresión del menú de usuario: Avance 72 incorporó varios contenedores `.user-menu-wrap`, pero conservó un listener de cierre basado solo en el primer contenedor; al pulsar Carlos/CM el menú se abría y se cerraba inmediatamente.
- Se identificó la causa del fallo de ayuda: el modal `helpModal` había quedado insertado dentro del HTML generado para la ventana de impresión, por lo que no existía en el DOM principal cuando `openHelp()` intentaba utilizarlo.
- Se generó localmente `e-plaza_MARK-I-maestro-avance73-retro72-corregida.html` conservando el Avance 72 acumulativo y corrigiendo ambos comportamientos.
- Validación realizada: JavaScript sin errores de sintaxis, presencia estructural de menú/mensajes/notificaciones/modal de ayuda y pruebas de comportamiento para apertura/alternancia/cierre de menús y contenido de ayuda específico para PESTEL, DOFA y Objetivos/Indicadores.
- El HTML completo de Avance 73 todavía debe incorporarse a `prototype/` antes de considerarlo fuente oficial en `main`.

## Investigar · vertical slice funcional

- Se añadió `prototype/investigar-vertical-slice.html` como primera pieza funcional persistente del flujo Investigar.
- Implementa la cadena: pregunta → recuperación en Biblioteca / E-data → hallazgo → valoración → evidencia → propuesta al Proyecto Vivo → revisión humana.
- La valoración separa relevancia, vigencia y confianza de la fuente antes de permitir convertir un hallazgo en evidencia.
- La evidencia puede existir sin estar aceptada por un Proyecto Vivo; rechazar una propuesta no elimina la evidencia original.
- La aceptación humana habilita la evidencia para informar Workspace, pero no modifica automáticamente PESTEL, DOFA u objetivos.
- Se añadió persistencia local del proceso y trazabilidad visible entre fuente, hallazgo, evidencia y propuesta.
- JARVIS contextual orienta el siguiente paso sin aceptar decisiones por el usuario.
- La pieza fue escrita en `main` y verificada mediante lectura posterior desde GitHub.
