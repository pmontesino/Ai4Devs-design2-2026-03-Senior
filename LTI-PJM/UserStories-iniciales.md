# User Stories iniciales de LTI-PJM

Este documento recoge un backlog inicial de historias de usuario derivado del PRD en [LTI-PJM/LTI-PJM.md](LTI-PJM/LTI-PJM.md).

## Criterios aplicados

- Historias redactadas desde la perspectiva del usuario final o del rol operativo.
- Formato estándar: `Como [rol], quiero [acción], para [beneficio]`.
- Priorización por valor de negocio y valor para el usuario.
- Estimación relativa en `S`, `M` y `L`.
- Criterios de aceptación en formato BDD: `Dado que`, `Cuando`, `Entonces`.
- Revisión explícita con criterios INVEST.

## Backlog inicial priorizado

### US-01 - Crear una vacante en borrador

- Prioridad: P1
- Estimación: M
- Historia: Como técnico de selección, quiero crear una vacante en borrador con sus datos obligatorios, para preparar una oferta antes de publicarla.
- Valor: Permite iniciar el proceso de captación de talento y construir el flujo base del ATS.

**INVEST**

- Independent: Puede entregarse y validarse sin depender de la publicación externa.
- Negotiable: El detalle visual del formulario o el orden de campos puede ajustarse sin perder el valor.
- Valuable: Permite a RRHH comenzar a trabajar una vacante real.
- Estimable: El alcance funcional y las validaciones principales están claras.
- Small: Se limita al alta en borrador con campos obligatorios.
- Testable: Puede verificarse por guardado exitoso, validaciones y persistencia del estado.

**Criterios de aceptación**

1. Dado que un técnico de selección activo ha iniciado sesión, cuando completa los campos obligatorios de una vacante y guarda, entonces el sistema registra la vacante en estado `Borrador`.
2. Dado que falta algún campo obligatorio, cuando el usuario intenta guardar la vacante, entonces el sistema muestra los errores por campo y no crea el borrador.
3. Dado que la vacante se ha guardado correctamente, cuando el usuario vuelve a consultarla, entonces visualiza la información persistida y su estado `Borrador`.

### US-02 - Completar beneficios y adjuntos de la vacante

- Prioridad: P1
- Estimación: S
- Historia: Como técnico de selección, quiero añadir beneficios, enlaces y documentos a una vacante, para enriquecer la oferta antes de publicarla.
- Valor: Mejora la calidad de la oferta y reduce dudas de los candidatos.

**INVEST**

- Independent: Aporta valor sobre una vacante ya creada sin requerir publicación.
- Negotiable: La forma de presentar beneficios o adjuntos puede refinarse.
- Valuable: Hace la oferta más clara y atractiva para los candidatos.
- Estimable: Los tipos de adjunto y beneficios admitidos están definidos.
- Small: Se concentra en información complementaria de la vacante.
- Testable: Puede verificarse por alta, edición y recuperación de beneficios y adjuntos.

**Criterios de aceptación**

1. Dado que existe una vacante en borrador, cuando el técnico añade beneficios predefinidos y guarda, entonces el sistema asocia esos beneficios a la vacante.
2. Dado que existe una vacante en borrador, cuando el técnico adjunta un PDF o registra un enlace web válido, entonces el sistema lo guarda en la vacante.
3. Dado que una vacante tiene beneficios y adjuntos guardados, cuando el usuario abre de nuevo el detalle, entonces visualiza toda la información complementaria registrada.

### US-03 - Previsualizar y aprobar una vacante para publicar

- Prioridad: P1
- Estimación: S
- Historia: Como supervisor de RRHH, quiero previsualizar una vacante tal como la verá el candidato y aprobarla, para asegurar su calidad antes de publicarla.
- Valor: Reduce errores de publicación y protege la calidad de la comunicación pública.

**INVEST**

- Independent: Puede demostrarse sin ejecutar aún la publicación multicanal.
- Negotiable: El diseño exacto de la vista previa puede variar.
- Valuable: Añade control de calidad previo a una acción sensible.
- Estimable: El alcance es claro: resumen, vista previa y confirmación.
- Small: Se limita a la revisión previa y aprobación explícita.
- Testable: Puede validarse por acceso, visualización y confirmación de aprobación.

**Criterios de aceptación**

1. Dado que un supervisor activo accede a una vacante lista para publicar, cuando pulsa la acción de publicar, entonces el sistema muestra un resumen de la oferta y su vista previa.
2. Dado que la vacante no cumple las condiciones para publicarse, cuando el supervisor intenta iniciar la publicación, entonces el sistema bloquea la acción e informa los faltantes.
3. Dado que el supervisor revisa la vista previa, cuando confirma la aprobación, entonces el sistema registra que la vacante ha sido aprobada para publicación.

### US-04 - Programar y publicar una vacante en canales seleccionados

- Prioridad: P1
- Estimación: L
- Historia: Como supervisor de RRHH, quiero programar la publicación de una vacante en el tablero público de empleo y en canales externos seleccionados, para difundir la oferta en la fecha adecuada.
- Valor: Habilita la captación real de candidatos y aporta alcance al proceso de selección.

**INVEST**

- Independent: Entrega valor directo aunque otras historias de revisión aún no existan.
- Negotiable: La lista exacta de integraciones puede ampliarse en iteraciones posteriores.
- Valuable: Convierte una vacante interna en una oportunidad visible para candidatos.
- Estimable: Reglas de fecha, canal obligatorio y reintentos están definidas.
- Small: Se centra en una publicación programada y controlada, no en todas las capacidades del ecosistema.
- Testable: Puede verificarse por programación, publicación en board y resultado por canal.

**Criterios de aceptación**

1. Dado que una vacante está lista y aprobada para publicar, cuando el supervisor define una fecha y selecciona canales externos, entonces el sistema agenda la publicación y registra la configuración.
2. Dado que llega la fecha programada, cuando el sistema ejecuta la publicación, entonces la vacante se publica obligatoriamente en el tablero público de empleo y en los canales externos seleccionados.
3. Dado que falla la publicación en un canal externo, cuando el sistema procesa la incidencia, entonces mantiene la publicación en el resto de canales y registra el resultado individual por canal.

### US-05 - Ocultar una vacante publicada sin invalidar candidaturas

- Prioridad: P2
- Estimación: S
- Historia: Como técnico de selección, quiero ocultar una vacante publicada, para detener nuevas postulaciones sin perder las candidaturas ya recibidas.
- Valor: Permite controlar el volumen de entrada sin romper el flujo de selección ya iniciado.

**INVEST**

- Independent: Puede operar sobre vacantes ya publicadas de forma autónoma.
- Negotiable: La forma de notificar el cambio o mostrar el estado puede ajustarse.
- Valuable: Protege el proceso ante sobrecaptación o cambios operativos.
- Estimable: El estado objetivo y sus efectos están bien definidos.
- Small: Se limita al cambio a `Oculto` y sus consecuencias directas.
- Testable: Puede comprobarse por cambio de visibilidad y conservación de candidaturas vigentes.

**Criterios de aceptación**

1. Dado que una vacante está publicada, cuando un técnico o supervisor cambia su estado a `Oculto`, entonces la vacante deja de mostrarse en el tablero público de empleo.
2. Dado que una vacante ha pasado a `Oculto`, cuando el sistema sincroniza los canales externos, entonces pausa la publicación en portales de trabajo donde aplique.
3. Dado que la vacante ha sido ocultada, cuando RRHH consulta sus candidaturas existentes, entonces las candidaturas recibidas siguen vigentes y accesibles.

### US-06 - Consultar una vacante y presentar candidatura

- Prioridad: P1
- Estimación: M
- Historia: Como candidato, quiero consultar vacantes publicadas y presentar mi candidatura, para participar en procesos de selección alineados con mi perfil.
- Valor: Sin candidaturas no existe flujo de selección ni valor de negocio para el ATS.

**INVEST**

- Independent: Puede entregarse como flujo completo del lado candidato.
- Negotiable: El detalle del formulario puede ajustarse sin cambiar el objetivo.
- Valuable: Genera el insumo principal del proceso de selección.
- Estimable: El flujo y la información requerida están acotados.
- Small: Se centra en consulta de oferta y envío de candidatura.
- Testable: Puede validarse por visualización de la oferta, envío y registro de la candidatura.

**Criterios de aceptación**

1. Dado que una vacante está publicada, cuando un candidato accede al tablero público de empleo, entonces puede consultar el detalle de la oferta visible.
2. Dado que el candidato completa la información requerida para postularse, cuando envía la candidatura, entonces el sistema la registra asociada a la vacante.
3. Dado que la candidatura ha sido enviada correctamente, cuando el sistema finaliza el proceso, entonces deja trazabilidad del alta y pone la candidatura disponible para revisión interna.

### US-07 - Revisar una candidatura y tomar una decisión inicial

- Prioridad: P1
- Estimación: M
- Historia: Como técnico de selección, quiero revisar una candidatura y decidir si continúa o no en el proceso, para filtrar candidatos de forma eficiente.
- Valor: Permite avanzar desde la captación hacia la selección efectiva.

**INVEST**

- Independent: Puede probarse con candidaturas ya recibidas sin depender de entrevistas u otras fases posteriores.
- Negotiable: La presentación del expediente puede refinarse iterativamente.
- Valuable: Reduce carga operativa y facilita la selección inicial.
- Estimable: El expediente visible y los estados permitidos están definidos.
- Small: Se limita a la revisión inicial y decisión de estado.
- Testable: Puede verificarse por consulta de expediente, cambio de estado y registro de decisión.

**Criterios de aceptación**

1. Dado que existe una candidatura recibida, cuando un técnico o supervisor abre su expediente, entonces visualiza CV, carta, respuestas del formulario, experiencia, estudios y disponibilidad.
2. Dado que el revisor decide continuar con el candidato, cuando cambia el estado a `Preseleccionada` y guarda, entonces el sistema registra la decisión con su justificación.
3. Dado que el revisor decide descartar o dejar en espera una candidatura, cuando guarda la decisión, entonces el sistema actualiza el estado y mantiene trazabilidad del cambio.

### US-08 - Solicitar información adicional al candidato

- Prioridad: P2
- Estimación: M
- Historia: Como técnico de selección, quiero solicitar información adicional a un candidato con fecha límite y recordatorios, para completar la evaluación de su candidatura.
- Valor: Reduce decisiones prematuras y mejora la calidad de la revisión.

**INVEST**

- Independent: Puede funcionar como flujo autónomo sobre una candidatura existente.
- Negotiable: Los canales exactos o la redacción del mensaje pueden ajustarse.
- Valuable: Permite recuperar información faltante sin sacar al candidato del proceso.
- Estimable: La interacción y sus reglas principales están definidas.
- Small: Se enfoca en solicitud, respuesta y seguimiento básico.
- Testable: Puede verificarse por creación de solicitud, recepción de respuesta y recordatorios.

**Criterios de aceptación**

1. Dado que una candidatura está siendo revisada, cuando el técnico solicita información adicional, entonces el sistema registra la solicitud con su fecha límite y deja la candidatura en estado `En espera`.
2. Dado que existe una solicitud activa, cuando el sistema procesa las notificaciones, entonces envía recordatorios diarios por los canales seleccionados hasta la fecha límite.
3. Dado que el candidato accede al enlace recibido, cuando aporta texto libre y adjunta documentación, entonces el sistema incorpora esa respuesta al expediente de la candidatura.

### US-09 - Avanzar una candidatura preseleccionada a pruebas

- Prioridad: P2
- Estimación: S
- Historia: Como supervisor de RRHH, quiero que una candidatura preseleccionada avance a la etapa de pruebas, para continuar el proceso con los perfiles mejor ajustados.
- Valor: Conecta la revisión inicial con la siguiente fase de evaluación del proceso de selección.

**INVEST**

- Independent: Puede entregarse sobre decisiones ya tomadas en la revisión inicial.
- Negotiable: El detalle operativo de la etapa de pruebas puede ampliarse después.
- Valuable: Permite materializar el avance del pipeline de selección.
- Estimable: La regla principal de negocio está clara.
- Small: Se limita al traspaso de estado y continuidad del flujo.
- Testable: Puede validarse por la transición correcta tras una preselección válida.

**Criterios de aceptación**

1. Dado que una candidatura ha sido marcada como `Preseleccionada`, cuando el revisor guarda la decisión, entonces el sistema la deja lista para la etapa de pruebas.
2. Dado que una candidatura no está en estado `Preseleccionada`, cuando un usuario intenta avanzarla a pruebas, entonces el sistema bloquea la acción.
3. Dado que una candidatura ha avanzado a pruebas, cuando RRHH consulta su estado, entonces visualiza el cambio de fase con su trazabilidad asociada.

### US-10 - Proteger operaciones por rol y registrar trazabilidad completa

- Prioridad: P1
- Estimación: M
- Historia: Como supervisor de RRHH, quiero que el sistema respete roles y registre toda visualización o modificación, para operar con seguridad y trazabilidad completa.
- Valor: Asegura control operativo, cumplimiento interno y capacidad de auditoría.

**INVEST**

- Independent: Puede validarse transversalmente sobre funcionalidades ya disponibles.
- Negotiable: El formato exacto de las evidencias o pantallas puede ajustarse.
- Valuable: Protege operaciones sensibles y mejora la gobernanza del sistema.
- Estimable: Las reglas de acceso y auditoría están claramente descritas en el PRD.
- Small: Se centra en control de acceso y registro de acciones, no en administración avanzada.
- Testable: Puede comprobarse por restricciones de acceso y generación de eventos de auditoría.

**Criterios de aceptación**

1. Dado que un usuario no tiene el rol adecuado para una acción sensible, cuando intenta ejecutarla, entonces el sistema bloquea el acceso.
2. Dado que un usuario está inactivo, cuando intenta operar en el sistema, entonces el sistema impide el uso de funcionalidades.
3. Dado que un usuario visualiza o modifica una vacante o candidatura, cuando la acción se completa, entonces el sistema registra el evento en la auditoría con usuario, fecha, acción y entidad afectada.

## Observaciones

- Estas historias constituyen un backlog inicial y pueden refinarse o descomponerse en nuevas historias en sesiones posteriores.
- La gestión administrativa detallada de usuarios no se ha expandido como épica separada en este primer backlog, aunque parte de sus reglas ya se reflejan en la historia transversal de seguridad y trazabilidad.

## Tickets de trabajo generados

Estos tickets se han regenerado basándose directamente en las 10 historias de usuario de este mismo fichero.

### Resumen por fases

#### Fase 1 - Preparación

- [ ] T001 Crear la estructura base de backend, frontend-admin, frontend-public y shared en backend/, frontend-admin/, frontend-public/ y shared/
  Tipo: tarea técnica
  Descripción: Preparar la estructura inicial del repositorio para separar la API, el portal interno, el tablero público de empleo y las librerías compartidas.
  Criterios de aceptación:
  - Existen los directorios base definidos por el plan.
  - La estructura soporta desarrollo paralelo de backend y frontends.
  Prioridad: Alta
  Estimación: 2 puntos
  Asignación sugerida: Arquitectura
  Etiquetas: [tarea-técnica, preparación, monorepo, arquitectura]
  Referencias: plan.md, research.md
  Notas: Base para todos los tickets siguientes.

- [ ] T002 Inicializar la configuración de TypeScript y los paquetes raíz en package.json, tsconfig.base.json y shared/package.json
  Tipo: tarea técnica
  Descripción: Configurar el workspace de TypeScript común y los paquetes raíz para compartir tipos, contratos y utilidades.
  Criterios de aceptación:
  - Existe una configuración de TypeScript reutilizable en todo el repositorio.
  - Backend y frontends pueden consumir el paquete `shared`.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Plataforma
  Etiquetas: [tarea-técnica, preparación, typescript, compartido]
  Referencias: plan.md
  Notas: Mantener alineación con Node.js 22 y Next.js 15.

- [ ] T003 [P] Preparar la base de contratos y esquemas compartidos en shared/src/contracts/, shared/src/schemas/ y shared/src/types/
  Tipo: tarea técnica
  Descripción: Crear la base de DTO, esquemas y tipos compartidos para vacantes, publicaciones y candidaturas.
  Criterios de aceptación:
  - Existen puntos de entrada para contratos y tipos en `shared/src/`.
  - La librería compartida permite reutilizar contratos entre capas.
  Prioridad: Media
  Estimación: 2 puntos
  Asignación sugerida: Arquitectura
  Etiquetas: [tarea-técnica, preparación, contratos, compartido]
  Referencias: plan.md, contracts/recruitment-api.yaml
  Notas: Puede ejecutarse en paralelo con T002.

#### Fase 2 - Fundacional

- [ ] T004 Implementar usuarios, roles y autenticación base en backend/src/modules/auth/ y backend/src/modules/users/
  Tipo: tarea técnica
  Descripción: Implementar usuarios internos, roles, autenticación y comprobación de usuario activo para todas las operaciones privadas.
  Criterios de aceptación:
  - Existen entidades y servicios para usuarios y roles.
  - El acceso interno requiere autenticación y valida `isActive`.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Backend
  Etiquetas: [tarea-técnica, backend, auth, rbac]
  Referencias: data-model.md, plan.md
  Notas: Bloquea todas las historias internas.

- [ ] T005 [P] Implementar migraciones y entidades nucleares del ATS en backend/src/modules/jobs/entities/, backend/src/modules/applications/entities/ y backend/src/database/migrations/
  Tipo: tarea técnica
  Descripción: Modelar las entidades principales del ATS y dejar listas las migraciones iniciales de base de datos.
  Criterios de aceptación:
  - Existen entidades persistentes para vacantes, candidaturas, publicaciones y solicitudes.
  - Las migraciones iniciales se ejecutan sin errores.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Backend
  Etiquetas: [tarea-técnica, backend, base-de-datos, typeorm]
  Referencias: data-model.md, plan.md
  Notas: Base común para US-01 a US-09.

- [ ] T006 [P] Implementar la infraestructura de auditoría en backend/src/modules/audit/ y backend/src/shared/interceptors/
  Tipo: tarea técnica
  Descripción: Preparar la persistencia y la infraestructura común de auditoría para registrar lecturas y modificaciones.
  Criterios de aceptación:
  - Existe la entidad `AuditEvent` y un servicio para registrar eventos.
  - La infraestructura puede reutilizarse desde módulos de vacantes y candidaturas.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [tarea-técnica, backend, auditoría, observabilidad]
  Referencias: data-model.md, plan.md
  Notas: Requisito transversal para US-10.

- [ ] T007 [P] Implementar la infraestructura de colas y scheduling en backend/src/modules/notifications/, backend/src/modules/publications/ y backend/src/shared/queue/
  Tipo: tarea técnica
  Descripción: Configurar Redis y BullMQ para publicaciones programadas, reintentos y recordatorios diarios.
  Criterios de aceptación:
  - Existen colas y workers base para publicaciones y notificaciones.
  - El sistema puede registrar jobs diferidos con trazabilidad mínima.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Plataforma
  Etiquetas: [tarea-técnica, backend, colas, scheduling, bullmq]
  Referencias: research.md, plan.md
  Notas: Base para US-04 y US-08.

#### Fase 3 - US-01 Crear una vacante en borrador

- [ ] T008 [P] [US1] Implementar el dominio y la API de creación de vacantes en borrador en backend/src/modules/jobs/entities/, backend/src/modules/jobs/jobs.controller.ts y backend/src/modules/jobs/jobs.service.ts
  Tipo: funcionalidad
  Descripción: Crear el soporte de backend para dar de alta vacantes en estado `Borrador` con validación de campos obligatorios.
  Criterios de aceptación:
  - Existe soporte para crear vacantes en estado `Borrador`.
  - El backend bloquea las altas con campos obligatorios incompletos.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, vacantes, borrador, us1]
  Referencias: data-model.md, contracts/recruitment-api.yaml
  Notas: Depende de T004 y T005.

- [ ] T009 [US1] Implementar el formulario de alta de vacantes en frontend-admin/src/features/jobs/job-form.tsx y frontend-admin/src/services/jobs.ts
  Tipo: funcionalidad
  Descripción: Construir la interfaz para que un técnico cree una vacante en borrador y vea errores de validación por campo.
  Criterios de aceptación:
  - El formulario cubre todos los campos obligatorios de la vacante.
  - El usuario puede guardar un borrador y reabrirlo posteriormente.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Frontend interno
  Etiquetas: [funcionalidad, frontend-interno, vacantes, formulario, us1]
  Referencias: contracts/recruitment-api.yaml, quickstart.md
  Notas: Puede integrarse con mocks mientras se cierra T008.

#### Fase 4 - US-02 Completar beneficios y adjuntos de la vacante

- [ ] T010 [P] [US2] Implementar beneficios y adjuntos de vacantes en backend/src/modules/jobs/entities/job-benefit.entity.ts, backend/src/modules/jobs/entities/job-attachment.entity.ts y backend/src/modules/jobs/jobs.service.ts
  Tipo: funcionalidad
  Descripción: Añadir soporte de backend para beneficios predefinidos, enlaces web y documentos PDF asociados a una vacante.
  Criterios de aceptación:
  - La API guarda beneficios y adjuntos ligados a la vacante.
  - El detalle de la vacante devuelve la información complementaria persistida.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, vacantes, adjuntos, us2]
  Referencias: data-model.md, contracts/recruitment-api.yaml
  Notas: Depende de T008.

- [ ] T011 [US2] Extender la interfaz de vacantes para gestionar beneficios y adjuntos en frontend-admin/src/features/jobs/job-benefits.tsx, frontend-admin/src/features/jobs/job-attachments.tsx y frontend-admin/src/app/jobs/[jobId]/page.tsx
  Tipo: funcionalidad
  Descripción: Permitir al técnico enriquecer la vacante con beneficios, enlaces y PDF desde el portal interno.
  Criterios de aceptación:
  - El usuario puede añadir, editar y recuperar beneficios y adjuntos.
  - La vacante muestra la información complementaria al reabrirse.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Frontend interno
  Etiquetas: [funcionalidad, frontend-interno, vacantes, adjuntos, us2]
  Referencias: quickstart.md, contracts/recruitment-api.yaml
  Notas: Depende de T009 y T010.

#### Fase 5 - US-03 Previsualizar y aprobar una vacante para publicar

- [ ] T012 [P] [US3] Implementar la vista previa y la validación de vacantes listas para publicar en backend/src/modules/publications/publication-preview.service.ts y backend/src/modules/jobs/jobs.controller.ts
  Tipo: funcionalidad
  Descripción: Generar una previsualización fiel de la vacante y determinar si cumple las condiciones mínimas antes de aprobar su publicación.
  Criterios de aceptación:
  - El backend expone una vista previa de vacante para publicación.
  - El sistema informa con claridad los faltantes cuando la vacante no está lista.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, publicaciones, vista-previa, us3]
  Referencias: contracts/recruitment-api.yaml, quickstart.md
  Notas: Depende de T010.

- [ ] T013 [US3] Implementar la pantalla de previsualización y aprobación en frontend-admin/src/app/jobs/[jobId]/publish/page.tsx y frontend-admin/src/services/publications.ts
  Tipo: funcionalidad
  Descripción: Permitir al supervisor revisar cómo verá el candidato la vacante y registrar su aprobación explícita.
  Criterios de aceptación:
  - La pantalla muestra un resumen y la vista previa de la vacante.
  - La aprobación queda registrada antes de la programación de la publicación.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Frontend interno
  Etiquetas: [funcionalidad, frontend-interno, publicaciones, aprobación, us3]
  Referencias: quickstart.md, contracts/recruitment-api.yaml
  Notas: Depende de T012.

#### Fase 6 - US-04 Programar y publicar una vacante en canales seleccionados

- [ ] T014 [P] [US4] Implementar la programación y la publicación multicanal en backend/src/modules/publications/publications.service.ts, backend/src/modules/publications/workers/publish-job.worker.ts y backend/src/modules/publications/channel-clients/
  Tipo: funcionalidad
  Descripción: Gestionar la publicación programada en el tablero público de empleo y en canales externos, incluyendo la persistencia por canal.
  Criterios de aceptación:
  - La vacante puede programarse con fecha y lista de canales.
  - El tablero público de empleo se publica siempre cuando la vacante ha sido confirmada.
  Prioridad: Alta
  Estimación: 8 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, publicaciones, scheduling, us4]
  Referencias: research.md, contracts/recruitment-api.yaml
  Notas: Depende de T007 y T013.

- [ ] T015 [US4] Implementar reintentos, trazabilidad por canal y monitorización de la publicación en frontend-admin/src/app/jobs/[jobId]/publication-status/page.tsx y backend/src/modules/publications/publication-attempts.service.ts
  Tipo: funcionalidad
  Descripción: Registrar el resultado individual por canal, soportar tres reintentos y mostrar el estado operativo al supervisor.
  Criterios de aceptación:
  - Cada canal conserva su propio historial de intentos y estado.
  - Un fallo en un canal no bloquea la publicación en el resto.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, frontend-interno, publicaciones, reintentos, us4]
  Referencias: data-model.md, quickstart.md
  Notas: Depende de T014.

#### Fase 7 - US-05 Ocultar una vacante publicada sin invalidar candidaturas

- [ ] T016 [P] [US5] Implementar el cambio a estado `Oculto` y la pausa por canal en backend/src/modules/publications/hide-job.service.ts y backend/src/modules/publications/channel-sync.service.ts
  Tipo: funcionalidad
  Descripción: Permitir ocultar vacantes publicadas sin eliminar candidaturas ni romper la trazabilidad de canales.
  Criterios de aceptación:
  - La vacante deja de ser visible en el tablero público de empleo al pasar a `Oculto`.
  - Las candidaturas existentes permanecen activas y accesibles.
  Prioridad: Media
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, vacantes, ciclo-de-vida, us5]
  Referencias: data-model.md, contracts/recruitment-api.yaml
  Notas: Depende de T014.

- [ ] T017 [US5] Implementar la acción de ocultar vacantes en frontend-admin/src/app/jobs/[jobId]/actions/hide-job.ts y frontend-admin/src/app/jobs/[jobId]/page.tsx
  Tipo: funcionalidad
  Descripción: Añadir al portal interno la acción para ocultar vacantes publicadas y confirmar su efecto operativo.
  Criterios de aceptación:
  - Técnicos y supervisores autorizados pueden ocultar la vacante.
  - La interfaz refleja el nuevo estado sin perder acceso a las candidaturas asociadas.
  Prioridad: Media
  Estimación: 2 puntos
  Asignación sugerida: Frontend interno
  Etiquetas: [funcionalidad, frontend-interno, vacantes, ciclo-de-vida, us5]
  Referencias: quickstart.md, contracts/recruitment-api.yaml
  Notas: Depende de T016.

#### Fase 8 - US-06 Consultar una vacante y presentar candidatura

- [ ] T018 [P] [US6] Implementar el tablero público de empleo y el detalle de vacantes en frontend-public/src/app/jobs/page.tsx, frontend-public/src/app/jobs/[jobId]/page.tsx y backend/src/modules/public-jobs/public-jobs.controller.ts
  Tipo: funcionalidad
  Descripción: Habilitar la consulta pública de vacantes visibles para que el candidato descubra y revise ofertas activas.
  Criterios de aceptación:
  - El sistema lista solo vacantes públicas visibles.
  - El detalle público muestra la información necesaria para postularse.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Frontend público
  Etiquetas: [funcionalidad, frontend-público, backend, tablero, us6]
  Referencias: contracts/recruitment-api.yaml, quickstart.md
  Notas: Depende de T014.

- [ ] T019 [US6] Implementar el formulario y el registro de candidaturas en frontend-public/src/features/applications/application-form.tsx y backend/src/modules/applications/public-applications.controller.ts
  Tipo: funcionalidad
  Descripción: Permitir al candidato enviar su candidatura a una vacante publicada y dejarla disponible para revisión interna.
  Criterios de aceptación:
  - La candidatura se registra asociada a la vacante correcta.
  - El sistema deja trazabilidad suficiente del alta de la candidatura.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Frontend público
  Etiquetas: [funcionalidad, frontend-público, backend, candidaturas, us6]
  Referencias: contracts/recruitment-api.yaml, data-model.md
  Notas: Depende de T018.

#### Fase 9 - US-07 Revisar una candidatura y tomar una decisión inicial

- [ ] T020 [P] [US7] Implementar el expediente de candidatura y la API de revisión en backend/src/modules/applications/applications.controller.ts, backend/src/modules/reviews/reviews.controller.ts y backend/src/modules/reviews/reviews.service.ts
  Tipo: funcionalidad
  Descripción: Exponer la consulta del expediente de candidatura y registrar decisiones iniciales con justificación cuando aplique.
  Criterios de aceptación:
  - Técnicos y supervisores pueden consultar el expediente completo.
  - El sistema registra cambios de estado y la justificación de la preselección.
  Prioridad: Alta
  Estimación: 8 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, candidaturas, revisiones, us7]
  Referencias: data-model.md, contracts/recruitment-api.yaml
  Notas: Depende de T019.

- [ ] T021 [US7] Implementar la pantalla interna de revisión y decisión inicial en frontend-admin/src/app/applications/[applicationId]/page.tsx y frontend-admin/src/features/applications/review-panel.tsx
  Tipo: funcionalidad
  Descripción: Construir la interfaz de revisión para consultar el expediente, tomar decisiones y guardar la justificación operativa.
  Criterios de aceptación:
  - La pantalla muestra CV, carta, respuestas y demás datos del expediente.
  - El usuario puede cambiar el estado a `Preseleccionada`, `Descartada` o `En espera`.
  Prioridad: Alta
  Estimación: 5 puntos
  Asignación sugerida: Frontend interno
  Etiquetas: [funcionalidad, frontend-interno, candidaturas, revisiones, us7]
  Referencias: quickstart.md, spec.md
  Notas: Depende de T020.

#### Fase 10 - US-08 Solicitar información adicional al candidato

- [ ] T022 [P] [US8] Implementar solicitudes de información adicional y su persistencia en backend/src/modules/additional-info/additional-info.controller.ts y backend/src/modules/additional-info/additional-info.service.ts
  Tipo: funcionalidad
  Descripción: Permitir a RR. HH. registrar solicitudes de información adicional con fecha límite sobre una candidatura en revisión.
  Criterios de aceptación:
  - La solicitud queda ligada a la candidatura y cambia el estado a `En espera`.
  - La fecha límite queda persistida y disponible para procesos de recordatorio.
  Prioridad: Media
  Estimación: 5 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, candidaturas, información-adicional, us8]
  Referencias: data-model.md, contracts/recruitment-api.yaml
  Notas: Depende de T020.

- [ ] T023 [US8] Implementar el acceso del candidato, la respuesta documental y los recordatorios diarios en frontend-public/src/app/additional-info/[requestId]/page.tsx, backend/src/modules/notifications/workers/additional-info-reminder.worker.ts y backend/src/modules/additional-info/response.service.ts
  Tipo: funcionalidad
  Descripción: Habilitar el flujo de respuesta del candidato mediante enlace y adjuntos, junto con recordatorios por canales seleccionados.
  Criterios de aceptación:
  - El candidato puede responder con texto libre y documentación adjunta.
  - El sistema programa y envía recordatorios diarios hasta la fecha límite.
  Prioridad: Media
  Estimación: 5 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, frontend-público, notificaciones, us8]
  Referencias: quickstart.md, data-model.md
  Notas: Depende de T007 y T022.

#### Fase 11 - US-09 Avanzar una candidatura preseleccionada a pruebas

- [ ] T024 [US9] Implementar la transición a `En pruebas` y sus validaciones de negocio en backend/src/modules/reviews/review-state-machine.service.ts y frontend-admin/src/features/applications/progression-actions.tsx
  Tipo: funcionalidad
  Descripción: Permitir avanzar una candidatura preseleccionada a la etapa de pruebas y bloquear intentos desde estados no válidos.
  Criterios de aceptación:
  - Solo las candidaturas `Preseleccionada` pueden pasar a `En pruebas`.
  - El cambio de fase queda visible en el expediente y en la trazabilidad.
  Prioridad: Media
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, frontend-interno, flujo, us9]
  Referencias: data-model.md, quickstart.md
  Notas: Depende de T020 y T021.

#### Fase 12 - US-10 Proteger operaciones por rol y registrar trazabilidad completa

- [ ] T025 [P] [US10] Aplicar guards RBAC y validación de usuario activo en backend/src/shared/guards/, backend/src/modules/jobs/ y backend/src/modules/applications/
  Tipo: funcionalidad
  Descripción: Asegurar que cada operación sensible del sistema solo pueda ser ejecutada por el rol adecuado y por usuarios activos.
  Criterios de aceptación:
  - Los endpoints internos bloquean usuarios sin permiso o inactivos.
  - Las reglas distinguen correctamente los permisos de técnico y supervisor.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, seguridad, rbac, us10]
  Referencias: plan.md, data-model.md
  Notas: Se apoya en T004.

- [ ] T026 [P] [US10] Instrumentar la auditoría de visualizaciones y modificaciones en backend/src/shared/interceptors/audit.interceptor.ts y backend/src/modules/audit/audit.service.ts
  Tipo: funcionalidad
  Descripción: Registrar toda visualización y cambio relevante sobre vacantes y candidaturas con información completa de contexto.
  Criterios de aceptación:
  - Las operaciones clave generan eventos con usuario, fecha, acción y entidad afectada.
  - La instrumentación cubre vacantes, publicaciones y candidaturas.
  Prioridad: Alta
  Estimación: 3 puntos
  Asignación sugerida: Backend
  Etiquetas: [funcionalidad, backend, auditoría, cumplimiento, us10]
  Referencias: data-model.md, quickstart.md
  Notas: Depende de T006.

- [ ] T027 [US10] Exponer la consulta operativa de auditoría en backend/src/modules/audit/audit.controller.ts y frontend-admin/src/app/audit/page.tsx
  Tipo: mejora
  Descripción: Facilitar la consulta interna de evidencias de auditoría para soporte funcional y verificación de la trazabilidad.
  Criterios de aceptación:
  - Existe un endpoint interno para consultar eventos de auditoría.
  - El portal interno muestra una vista básica de auditoría filtrable.
  Prioridad: Media
  Estimación: 3 puntos
  Asignación sugerida: Frontend interno
  Etiquetas: [mejora, frontend-interno, backend, auditoría, us10]
  Referencias: quickstart.md, plan.md
  Notas: Depende de T026.

#### Fase 13 - Cierre

- [ ] T028 [P] Actualizar contratos compartidos y documentación de integración en shared/src/contracts/ y specs/001-lti-ats-mvp/contracts/recruitment-api.yaml
  Tipo: tarea técnica
  Descripción: Alinear los contratos y tipos compartidos con la implementación real del MVP una vez completadas las historias principales.
  Criterios de aceptación:
  - Los contratos OpenAPI y los tipos compartidos reflejan los endpoints implementados.
  - No quedan discrepancias funcionales evidentes entre backend y frontends.
  Prioridad: Media
  Estimación: 2 puntos
  Asignación sugerida: Arquitectura
  Etiquetas: [tarea-técnica, contratos, documentación, cierre]
  Referencias: contracts/recruitment-api.yaml, plan.md
  Notas: Ejecutar al cierre del MVP.

- [ ] T029 Ejecutar y documentar la validación funcional del MVP en specs/001-lti-ats-mvp/quickstart.md
  Tipo: mejora
  Descripción: Validar el recorrido de extremo a extremo del MVP y dejar evidencia funcional en el quickstart del proyecto.
  Criterios de aceptación:
  - El quickstart refleja el estado real de los flujos implementados.
  - Quedan documentadas las comprobaciones mínimas para la demo y el handoff.
  Prioridad: Media
  Estimación: 2 puntos
  Asignación sugerida: Calidad
  Etiquetas: [mejora, calidad, validación, cierre]
  Referencias: quickstart.md, plan.md
  Notas: Ejecutar tras completar las historias seleccionadas para el sprint.
