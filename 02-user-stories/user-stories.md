# Historias de usuario: Warmly (incremento 1, módulos M1–M5)

Formato: *Como [rol], quiero [funcionalidad], para [beneficio]*. Criterios de aceptación en formato Dado / cuando / entonces. Prioridad MoSCoW y estimación en puntos de historia (Fibonacci).

## M1. Usuarios y acceso

### HU-01 · Invitar usuarios y asignar rol

Como **administrador de sistemas**, quiero invitar a un nuevo usuario por correo electrónico y asignarle un rol, para que solo el personal autorizado acceda al CRM con los permisos que le corresponden.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado que tengo el rol sistemas, cuando ingreso un correo, elijo un rol (ventas, técnico, gerencia, contabilidad o sistemas) y confirmo, entonces el sistema envía la invitación y el usuario queda en estado «pendiente».
  2. Dado que el correo ya pertenece a un usuario registrado, cuando intento invitarlo, entonces el sistema muestra un aviso y no crea una cuenta duplicada.
  3. Dado que no tengo el rol sistemas, cuando intento acceder a la administración de usuarios, entonces el sistema me niega el acceso.

### HU-02 · Iniciar sesión

Como **usuario interno**, quiero iniciar sesión con mi correo y contraseña en la web y en la app móvil, para acceder a la información de mi trabajo desde cualquier lugar.

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado que mis credenciales son válidas, cuando inicio sesión, entonces el sistema me lleva a la pantalla de inicio correspondiente a mi rol.
  2. Dado que ingreso una contraseña incorrecta, cuando intento iniciar sesión, entonces el sistema muestra un mensaje genérico sin indicar qué dato es incorrecto.
  3. Dado que fallo cinco intentos seguidos, cuando intento de nuevo, entonces la cuenta se bloquea temporalmente durante 15 minutos.

### HU-03 · Recuperar contraseña

Como **usuario interno**, quiero recuperar mi contraseña mediante un enlace enviado a mi correo, para no depender del área de sistemas si la olvido.

- **Prioridad:** Should
- **Estimación:** 2 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado que mi correo está registrado, cuando solicito recuperar la contraseña, entonces recibo un enlace válido por 60 minutos.
  2. Dado que el enlace ya expiró o fue usado, cuando lo abro, entonces el sistema me indica que debo solicitar uno nuevo.

### HU-04 · Desactivar usuario

Como **administrador de sistemas**, quiero desactivar la cuenta de un usuario que dejó la empresa, para que pierda el acceso sin borrar el historial de lo que registró.

- **Prioridad:** Must
- **Estimación:** 1 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un usuario activo, cuando lo desactivo, entonces ya no puede iniciar sesión y sus sesiones abiertas se cierran.
  2. Dado un usuario desactivado, cuando consulto los registros que creó, entonces siguen visibles con su nombre como autor.

### HU-05 · Permisos por rol

Como **gerente**, quiero que cada rol vea solo los módulos y datos que le corresponden, para proteger información sensible, como montos de propuestas y datos personales de los clientes.

- **Prioridad:** Must
- **Estimación:** 5 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado que tengo el rol ventas, cuando consulto leads y oportunidades, entonces solo veo los que tengo asignados.
  2. Dado que tengo el rol gerencia, cuando consulto leads y oportunidades, entonces veo los de todo el equipo.
  3. Dado que tengo el rol técnico, cuando abro una propuesta aprobada, entonces no veo los montos económicos.

## M2. Leads

### HU-06 · Registrar lead manualmente

Como **asesor de ventas**, quiero registrar un lead con sus datos de contacto y el canal por el que llegó, para no perder ningún prospecto, aunque llegue por teléfono, referido o en una feria.

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado que ingreso nombre, al menos un teléfono o correo y el canal de origen, cuando guardo, entonces el lead queda en estado «Nuevo» y asignado a mí.
  2. Dado que falta un dato obligatorio, cuando intento guardar, entonces el sistema señala el campo faltante y no guarda el registro.
  3. Dado que estoy en la app móvil, cuando registro un lead, entonces el formulario solo pide los datos obligatorios para hacerlo en menos de un minuto.

### HU-07 · Captura desde el sitio web

Como **prospecto interesado**, quiero dejar mis datos en un formulario del sitio web de Warmi Energy, para que un asesor me contacte con información sobre paneles solares.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado que completo el formulario y acepto el tratamiento de mis datos personales, cuando lo envío, entonces se crea un lead con canal «Formulario web» y veo un mensaje de confirmación.
  2. Dado que no acepto el tratamiento de datos, cuando intento enviar, entonces el formulario no se envía (LOPDP).
  3. Dado que se crea el lead, cuando termina el registro, entonces la gerencia recibe una notificación para asignarlo.

### HU-08 · Detección de duplicados

Como **asesor de ventas**, quiero que el sistema me avise si el lead que registro ya existe, para evitar fichas duplicadas del mismo cliente.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado que ya existe un lead o cliente con la misma cédula/RUC, correo o teléfono, cuando registro uno nuevo, entonces el sistema me muestra el registro existente antes de guardar.
  2. Dado el aviso de posible duplicado, cuando elijo «Usar el existente», entonces no se crea un registro nuevo y se abre la ficha encontrada.

### HU-09 · Calificar lead

Como **asesor de ventas**, quiero calificar un lead con su tipo de cliente, consumo mensual aproximado, nivel de interés y presupuesto, para priorizar a los prospectos con mayor probabilidad de compra.

- **Prioridad:** Should
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un lead en estado «Nuevo», cuando registro su calificación, entonces pasa a estado «Calificado» y se guarda quién y cuándo lo calificó.
  2. Dado un conjunto de leads, cuando ordeno la bandeja por calificación, entonces aparecen primero los de mayor interés y consumo.

### HU-10 · Asignar leads a asesores

Como **gerente**, quiero asignar o reasignar leads a los asesores, para repartir la carga de trabajo del equipo comercial.

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un lead sin asesor, cuando lo asigno a un asesor, entonces el asesor recibe una notificación y el lead aparece en su bandeja.
  2. Dado un lead ya asignado, cuando lo reasigno, entonces el cambio queda registrado con fecha y usuario.

### HU-11 · Convertir lead en cliente

Como **asesor de ventas**, quiero convertir un lead calificado en cliente y oportunidad en un solo paso, para iniciar el proceso comercial sin volver a escribir los datos.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un lead calificado, cuando lo convierto, entonces se crean el cliente, su contacto principal y una oportunidad en la etapa «Lead» con los datos del lead.
  2. Dado un lead ya convertido, cuando intento convertirlo otra vez, entonces el sistema no lo permite y muestra el cliente asociado.

### HU-12 · Leads desde WhatsApp

Como **asesor de ventas**, quiero que los mensajes de WhatsApp de contactos nuevos se registren como leads, para atenderlos sin copiar sus datos a mano.

- **Prioridad:** Could
- **Estimación:** 8 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un mensaje de un número que no existe en el sistema, cuando llega a la línea de WhatsApp Business de la empresa, entonces se crea un lead con canal «WhatsApp» y el número del remitente.
  2. Dado un número que ya pertenece a un cliente, cuando llega un mensaje, entonces no se crea un lead nuevo y el mensaje se registra en el historial del cliente.

## M3. Pipeline comercial

### HU-13 · Tablero Kanban de oportunidades

Como **asesor de ventas**, quiero ver mis oportunidades en un tablero organizado por etapa, para saber de un vistazo en qué punto está cada venta.

- **Prioridad:** Must
- **Estimación:** 5 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado que tengo oportunidades activas, cuando abro el pipeline, entonces las veo como tarjetas en columnas con las nueve etapas del proceso.
  2. Dada una tarjeta, cuando la miro, entonces muestra el cliente, la potencia estimada en kWp y los días que lleva en la etapa.
  3. Dado el tablero, cuando filtro por asesor, tipo de cliente o fecha, entonces solo se muestran las oportunidades que cumplen el filtro.

### HU-14 · Cambiar etapa de una oportunidad

Como **asesor de ventas**, quiero mover una oportunidad a la siguiente etapa arrastrando su tarjeta, para mantener su estado actualizado sin pasos adicionales.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado que la oportunidad cumple los requisitos de la etapa destino, cuando suelto la tarjeta en esa columna, entonces la etapa cambia y se registra en el historial.
  2. Dado que intento saltar más de una etapa, cuando suelto la tarjeta, entonces el sistema me pide un motivo antes de confirmar.

### HU-15 · Requisitos de transición

Como **gerente**, quiero que el sistema impida avanzar de etapa si no se cumplen sus requisitos, para asegurar que el proceso comercial se siga correctamente.

- **Prioridad:** Must
- **Estimación:** 5 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una oportunidad sin planillas eléctricas cargadas, cuando intento moverla a «Dimensionamiento preliminar», entonces el sistema lo impide e indica el requisito faltante.
  2. Dado que tengo el rol gerencia, cuando fuerzo una transición permitida, entonces el sistema exige un motivo y lo registra.
  3. Dado un requisito marcado como no forzable, cuando cualquier usuario intenta saltarlo, entonces el sistema lo impide sin excepción.

### HU-16 · Motivo de pérdida

Como **gerente**, quiero que toda oportunidad cancelada registre un motivo de pérdida, para analizar por qué se pierden ventas.

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una oportunidad activa, cuando la marco como cancelada, entonces debo elegir un motivo de una lista (precio, competencia, sin respuesta, no viable técnicamente, otro).
  2. Dado el motivo «otro», cuando lo elijo, entonces debo escribir una descripción.

### HU-17 · Historial de etapas

Como **gerente**, quiero consultar el historial de cambios de etapa de una oportunidad, para auditar cómo avanzó el proceso y cuánto tiempo pasó en cada etapa.

- **Prioridad:** Should
- **Estimación:** 2 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una oportunidad, cuando abro su historial, entonces veo cada cambio de etapa con fecha, usuario y motivo si lo hubo.
  2. Dado un registro del historial, cuando cualquier usuario intenta modificarlo, entonces el sistema no lo permite.

### HU-18 · Consultar oportunidades desde el celular

Como **asesor de ventas**, quiero consultar desde la app móvil el estado de mis oportunidades, para responder a un cliente aunque esté fuera de la oficina.

- **Prioridad:** Should
- **Estimación:** 3 pts
- **Componente:** Móvil
- **Criterios de aceptación:**
  1. Dado que inicio sesión en la app móvil, cuando abro «Mis oportunidades», entonces veo la lista agrupada por etapa.
  2. Dada una oportunidad de la lista, cuando la toco, entonces veo el cliente, la etapa, la última actividad y la propuesta vigente.

## M4. Clientes y contactos

### HU-19 · Registrar cliente por tipo

Como **asesor de ventas**, quiero registrar un cliente indicando si es residencial, comercial o industrial, con los datos propios de cada tipo, para tener información completa y correcta para la propuesta.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado que elijo el tipo «residencial», cuando completo el formulario, entonces el sistema pide cédula y datos personales.
  2. Dado que elijo «comercial» o «industrial», cuando completo el formulario, entonces el sistema pide RUC, razón social y actividad económica.
  3. Dado un RUC o cédula con formato inválido, cuando intento guardar, entonces el sistema muestra el error y no guarda.

### HU-20 · Contactos del cliente

Como **asesor de ventas**, quiero agregar varios contactos a un cliente, con su cargo, teléfono y correo, para saber a quién dirigirme según el tema (decisión de compra, mantenimiento, pagos).

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado un cliente, cuando agrego un contacto, entonces queda asociado y puedo marcarlo como contacto principal.
  2. Dado un cliente con varios contactos, cuando marco uno como principal, entonces el anterior deja de serlo.

### HU-21 · Sitios y medidores

Como **técnico**, quiero registrar los sitios de un cliente con su dirección, número de medidor, empresa eléctrica y tarifa, para dimensionar correctamente cada instalación.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un cliente, cuando agrego un sitio con su número de medidor, entonces queda disponible para asociarlo a oportunidades y planillas.
  2. Dado un número de medidor que ya existe en otro sitio, cuando intento guardarlo, entonces el sistema muestra un aviso.

### HU-22 · Línea de tiempo del cliente

Como **asesor de ventas**, quiero ver en la ficha del cliente una línea de tiempo con sus interacciones, oportunidades y propuestas, para conocer todo su historial antes de contactarlo.

- **Prioridad:** Should
- **Estimación:** 5 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un cliente con historial, cuando abro su ficha, entonces veo los eventos ordenados del más reciente al más antiguo, con fecha, tipo y usuario.
  2. Dada la línea de tiempo, cuando filtro por tipo de evento, entonces solo veo los eventos de ese tipo.

### HU-23 · Buscar clientes

Como **asesor de ventas**, quiero buscar clientes por nombre, cédula/RUC, teléfono o ciudad, para encontrarlos rápidamente durante una llamada.

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dado que escribo al menos tres caracteres, cuando busco, entonces el sistema muestra coincidencias en menos de dos segundos.
  2. Dado un resultado, cuando lo selecciono, entonces se abre la ficha del cliente.

## M5. Proyectos y propuestas

### HU-24 · Cargar planillas eléctricas

Como **asesor de ventas**, quiero cargar las planillas eléctricas mensuales de un sitio, para que el área técnica pueda realizar el dimensionamiento.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dado un sitio, cuando subo una planilla en PDF o imagen e indico el mes y el año, entonces queda guardada y asociada al sitio.
  2. Dado que ya existe una planilla para ese mes, cuando subo otra, entonces el sistema me pregunta si deseo reemplazarla.
  3. Dado un sitio, cuando consulto sus planillas, entonces veo cuántos de los últimos doce meses están cargados.

### HU-25 · Ver dimensionamientos

Como **técnico**, quiero ver en la oportunidad los escenarios calculados en el Dimensionador (kWp, producción y cobertura), para no copiar resultados a mano entre sistemas.

- **Prioridad:** Must
- **Estimación:** 5 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una oportunidad con dimensionamientos guardados en la base de datos central, cuando la abro, entonces veo cada escenario con su potencia, producción anual y cobertura.
  2. Dado un escenario marcado como seleccionado en el Dimensionador, cuando lo veo en Warmly, entonces aparece destacado.
  3. Dado un escenario, cuando hago clic en «Abrir en el Dimensionador», entonces se abre ese escenario en la herramienta existente.

### HU-26 · Versiones de propuesta

Como **asesor de ventas**, quiero ver las versiones de la propuesta de una oportunidad e identificar la vigente, para enviar siempre la versión correcta al cliente.

- **Prioridad:** Must
- **Estimación:** 3 pts
- **Componente:** Web y móvil
- **Criterios de aceptación:**
  1. Dada una oportunidad con varias propuestas, cuando abro la sección de propuestas, entonces veo cada versión con su fecha y la vigente destacada.
  2. Dada una versión enviada al cliente, cuando intento modificarla, entonces el sistema no lo permite y sugiere crear una nueva versión.

### HU-27 · Seguimiento de la propuesta

Como **asesor de ventas**, quiero registrar la fecha de envío de la propuesta y la respuesta del cliente, para dar seguimiento oportuno y saber cuándo cerrar la venta.

- **Prioridad:** Must
- **Estimación:** 2 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una propuesta vigente, cuando registro su envío, entonces el sistema guarda la fecha y programa un recordatorio de seguimiento a los tres días.
  2. Dado que el cliente acepta la propuesta, cuando lo registro, entonces la oportunidad puede avanzar a «Aprobado por el cliente».

### HU-28 · Ver visitas técnicas

Como **técnico**, quiero ver en la oportunidad las visitas registradas en la app de visitas y su resultado, para no duplicar la información de la inspección.

- **Prioridad:** Should
- **Estimación:** 5 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una visita técnica registrada en la app de visitas para el sitio de la oportunidad, cuando abro la oportunidad, entonces veo la fecha, el técnico y el resultado de viabilidad.
  2. Dada una visita con hallazgos bloqueantes, cuando la veo en Warmly, entonces aparece una alerta en la oportunidad.

### HU-29 · Expediente del proyecto

Como **gerente**, quiero que los documentos del proyecto se guarden en un expediente único, para encontrarlos en un solo lugar cuando se necesiten.

- **Prioridad:** Could
- **Estimación:** 5 pts
- **Componente:** Web
- **Criterios de aceptación:**
  1. Dada una oportunidad, cuando subo un documento y elijo su tipo (contrato, permiso, planilla, otro), entonces queda guardado en el repositorio de archivos configurado.
  2. Dado el expediente, cuando lo abro, entonces veo los documentos agrupados por tipo con fecha y usuario que los subió.

