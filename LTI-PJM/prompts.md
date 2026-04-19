# Registro de prompts

## 2026-04-19

1. Todos los prompts que vaya escribiendo guárdalos en #file:prompts.md. Por favor, pon la fecha de hoy y debajo los prompts de hoy. Fíjate en el esquema que ya existe en el fichero. Importante: el orden debe ser siempre con las sesiones de trabajo más recientes antes, de forma que se vean en la parte superior del archivo.
2. Esa regla verifica si está en copilot-instructions.md y si no está agrégala para futuras sesiones.
3. Modifica el agente de especificación de spec-kit para que cree las historias de usuario según la información disponible en #file:2.Gestión de producto y User Stories.md, donde se exponen un conjunto de criterios y buenas prácticas para hacer las historias de usuario.
4. Follow instructions in #prompt:speckit.specify.prompt.md with these arguments: Basado en el PRD (documento funcional) #file:LTI-PJM.md por favor crea en el fichero #file:UserStories-iniciales.md.
5. Follow instructions in #prompt:speckit.plan.prompt.md with these arguments: basado en #file:UserStories-iniciales.md.
6. Incorpora los criterios de #file:4.Tickets de trabajo.md en el agente de generación de tareas (tasks).
7. Follow instructions in #prompt:speckit.tasks.prompt.md with these arguments: Genera los tickets con el agente tasks, que ya tiene los criterios, en una sección del fichero #file:UserStories-iniciales.md
8. Verifica en estos 3 ficheros ortografía y gramática. Que esten en español (salvo terminos técnicos) y en formato UTF-8.
9. Vamos con 1: Revisar LTI-PJM.md para hacer una pasada adicional de estilo y homogeneizar términos como board, dashboard y scoring.
10. Continua con:  1.Homogeneizar en UserStories-iniciales.md otros tecnicismos como feature, technical-task, Frontend Admin o Frontend Public.

### PROMPTS PROPUESTOS

1. Actúa como Product Owner senior. A partir de #file:LTI-PJM.md, genera historias de usuario en español con formato "Como [rol], quiero [acción], para [beneficio]", prioridad, estimación S/M/L, criterios de aceptación en BDD e inspección INVEST. Escríbelas en #file:UserStories-iniciales.md.

2. Basado en el PRD de #file:LTI-PJM.md, crea un backlog inicial de user stories orientadas a MVP. Deben ser pequeñas, independientes, priorizadas por valor, sin detalles técnicos y con 3 criterios Dado/Cuando/Entonces por historia. Guarda el resultado en #file:UserStories-iniciales.md.

3. Lee #file:LTI-PJM.md y transforma sus casos de uso en historias de usuario de estilo ágil. Quiero títulos, historia en formato estándar, valor, prioridad, estimación e INVEST breve. No generes tareas técnicas. Escribe el resultado en #file:UserStories-iniciales.md.

### Justificación del uso de specify

Se usó `specify` porque ofrece un marco más robusto y repetible que un prompt libre. Obliga a trabajar con una estructura consistente, incorpora validaciones de calidad, limita ambigüedades y deja el resultado listo para continuar con las siguientes fases del flujo de Spec Kit.

Además, reduce la variabilidad entre sesiones. Un prompt libre puede producir una buena salida, pero no garantiza uniformidad ni trazabilidad entre artefactos. `specify` está pensado precisamente para encadenar especificación, aclaración, planificación y tareas sin reinterpretaciones manuales.



## 2026-04-13

1. Crea un copilot-instructions.md y agrega las siguientes instrucciones:
   - Genera los Markdown en español.
   - Registra los prompts (incluido este) que escribo en un fichero con el nombre prompts.md dentro de la carpeta #folder:LTI-PJM
   - Dentro de la carpeta #folder:LTI-PJM se deben guardar en un fichero con el nombre LTI-PJM.md todas las especificaciones iniciales del proyecto.

2. Crea una breve descripción del software LTI basándote en esto que te voy a contar: El software de LTI es un Applicant-Tracking System, una herramienta que permite a los departamentos de Recursos Humanos (RRHH) hacer seguimiento del proceso de contratación de personal. El proceso inicia cuando el departamento de RRHH publica en un board digital y público una solicitud de empleo. Asimismo, esa oferta de empleo es publicada en redes sociales y portales de empleo asociados, de forma automática.

3. Continúo describiendo lo que hace el sistema: Los candidatos ven las ofertas en los medios antes mencionados y proceden a presentar solicitudes. Dichas solicitudes son revisadas por un técnico de selección, miembro del departamento de Recursos Humanos. Seguidamente, el técnico hace una preselección e inicia el proceso de pruebas a los candidatos. A partir de los resultados de las pruebas, se seleccionan los candidatos que han de continuar el proceso. El siguiente paso es agendar las entrevistas, hacerlas y, finalmente, a partir del resultado de esta fase, se contrata al candidato o a los candidatos seleccionados. Esa última fase implica la preparación de la documentación para el cierre de la contratación.

4. A continuación, vamos a describir los 3 casos de uso principales. Para cada caso de uso emplearemos una codificación, una descripción, un actor principal, precondiciones, postcondiciones, flujo principal, flujos alternativos, flujos de excepción, reglas de negocio y criterios de aceptación.
Vamos a trabajar sobre estos 3: Crear empleos, publicar empleos y revisar candidaturas.
Vamos a crear una primera versión y aclaramos detalles sobre la primera iteración.

5. Vamos con CU-01. Hazme las preguntas para clarificar el caso de uso

6. Pueden crear perfiles el técnico y el supervisor.
Los campos que propones me parecen correctos. Incluye beneficios: ticket alimentación, ticket transporte, guardería, seguro de vida, seguro médico, formación, entre otros.
El campo ubicación debe desglosarse en país, provincia, ciudad y dirección. La dirección es opcional. El salario es opcional. La fecha límite es opcional.
Los estados de una publicación son: borrador,oculto, publicado y cerrado
La descripción debe tener un mínimo de 30 caracteres.
Toda modificación y visualización de datos debe ser registrada en el sistema: Historial de cambios, trazabilidad completa.
La aplicación requiere un sistema de autenticación y autorización de usuarios basada en roles. La disponibilidad de una pantalla o funcionalidad dependerá del rol del usuario. El usuario deberá estar activo para poder trabajar con el sistema. Esto también implica tener una gestión de usuarios.
No hay plantillas para este MVP pero se puede añadir como una funcionalidad a construir en el futuro.
Solo los supervisores pueden publicar. El resto de estados puede ser manejado por los técnicos.
Un empleo está listo para publicar cuando se han completado todos los campos obligatorios.
La vacante puede incluir documentos PDF y/o enlaces web.
Justo antes de publicar el usuario debe ver la publicación tal cual la verá un candidato. Una vez revisada debe aprobar la publicación.

7. Continuemos con el CU-02

8. Si, vamos a incluir el campo fecha de publicación, de esa forma el sistema publica directamente en esa fecha. Antes de publicarse cualquier el supervisor puede cambiar la fecha o cambiar el estado de la publicación.
La publicación en el board público es obligatoria. Los demás portales y redes sociales en los que se publicará deberán ser seleccionados por el publicador. Tendrá disponibles aquellos integrados y podrá seleccionarlos.
Si la publicación en portales o redes sociales falla, debe reintentarlo 3 veces con un tiempo entre medias de 4 horas. Si la el último intento falla, debe enviar un correo electrónico al publicador.
Si falla la publicación en un canal, debe de igual forma publicarse en el resto.
Solo el supervisor puede intentar publicar nuevamente en un canal fallido.
De acuerdo con los campos propuestos para trazabilidad en CU-02.
Si, un empleo publicado puede ir a oculto. Un técnico o un supervisor pueden hacer este cambio. Las candidaturas actuales, continuan vigentes. Es una forma de evitar nuevas postulaciones.
La publicación en las redes sociales debe siempre enlazar a la publicación del dashboard.
CA-01: Dado un supervisor activo con sesión activa debe poder acceder a la pantalla de oferta y pulsar el botón publicar.
CA-02: Dado un supervidor activo con sesión activa al pulsar el botón publicar debe ver una pantalla con el resumen de la oferta a publicar y ver un botón de confirmación publicar.
CA-03: Cuando un supervisor o técnico cambia el estado de una publicación a Oculta, esta se debe dejar de ver en el dashboard y se debe pausar la publicación en los portales de trabajo.
CA-04: Cuando un supervisor o técnico accede a la pantalla de la publicación o hace algún cambio, este se registra en la tabla de auditorías.

9. Hagamos lo mismo con CU-03

10. Las candidaturas pueden ser revisadas por técnicos y supervisores.
Esos estados son correctos.
Debe ver esa información. El salario esperado no es obligatorio.
Toda preselección debe tener justificación.
Se puede pedir información adicional: se envía un correo con enlace a la candidatura y allí tiene un campo libre y un adjuntar documentación para añadir la información solicitada. Dicha información se adjunta a la candidatura. La aportación de información tiene fecha límite y tiene recordatorios diarios por el canal o canales seleccionados: WhatsApp, email o SMS.
Para pasar a pruebas basta con que quede en preseleccionado.
No existe sistema de scoring,
No hay revisión colaborativa.
Si dos supervisores evaluan una misma candidatura a la vez, se debe indicar al último en guardar que la candidatura ya ha sido revisada.
Trazabilidad igual que en los CU anteriores.
Las reglas de negocio son correctas.
De acuerdo con los criterios de aceptación

11. Ahora vamos a crear un modelo de datos relacional para soportar esos 3 casos de uso. Debes incluir tambien lo necesario para el sistema de gestión de usuario y login. Crea un diccionario de datos y ademas un diagrama mermaid con el modelo E-R propuesto.

12. Ahora necesito un diseño del sistema a alto nivel. Debes incluir un diagrama.

13. Añade en #file:copilot-instructions.md una regla para que se tenga cuidado de la ortografía en español. La codificación de los Markdown debe ser UTF-8 sin excepción.

14. Revisa la ortografía del fichero #file:LTI-PJM.md

15. Vale, ahora necesito un diagrama C4 en Mermaid que llegue en profundidad al componente de alta de empleos.
