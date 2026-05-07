# 7. Perfil iFay

El Perfil iFay es la "tarjeta de identidad" completa de iFay — una tabla de atributos de seis dimensiones semánticamente interpretable. No solo permite a los humanos identificar un iFay, sino que también permite a los sistemas analizarlo y, lo más importante, permite a los Fays reconocerse entre sí.

El perfil del Human Prime (Conciencia alineada) es un subconjunto y fuente de entrada del Perfil iFay. El perfil del Human Prime describe "qué tipo de persona es el Human Prime", mientras que el Perfil iFay describe "qué tipo de entidad es este iFay" — incluye los rasgos de personalidad del Prime, pero también los atributos independientes propios de iFay como habilidades, hardware y permisos.

El perfil del Human Prime es mantenido por el módulo de [Conciencia alineada](./11.3-Conciencia-alineada). La dimensión de habilidades es gestionada por [Habilidades registradas](./12.2-Habilidades-registradas), la dimensión de hardware por [Hub de controladores](./12.1-Hub-de-controladores) y la dimensión de permisos por [Gestión de Credenciales](./8.1-Gestión-de-credenciales).

---

## Identidad iFay

La Identidad iFay consiste en FayID y metadatos. FayID es un identificador persistente globalmente único, legible por humanos y por máquinas — la base para que iFay sea identificado y rastreado en todos los escenarios de interacción.

La Identidad iFay soporta migración de identidad fluida — cuando iFay evoluciona de un asistente personal a un rol social autónomo, el FayID no necesita cambiar; la identidad continúa naturalmente.

---

## Modelo Ego

La dimensión Ego en el Perfil registra la referencia a la versión de Ego actualmente activa.

El Modelo Ego es un modelo pequeño de borde conectable e intercambiable que puede cargarse en cualquier dispositivo terminal para darle la personalidad del Prime. iFay soporta tener múltiples versiones de Ego para acomodar la personalidad multifacética del Human Prime — pero solo una versión está activa en un momento dado, previniendo la "personalidad dividida".

Hay dos métodos de cambio: activado manualmente por el Human Prime, o determinado automáticamente por iFay basándose en el contexto. Después del cambio, la referencia a la versión activa de Ego en el Perfil se actualiza sincrónicamente.

### Escenario

> Zhang Lei es un gerente de producto que configuró dos versiones de Ego para su iFay: "Modo profesional" y "Modo casual".
>
> En las mañanas de días laborables, iFay cambia automáticamente a "Modo profesional" — las respuestas de correo tienen redacción rigurosa, las reuniones se programan con eficiencia como prioridad, y los documentos de requisitos se manejan con énfasis en la completitud lógica.
>
> En las noches de fin de semana, iFay detecta que Zhang Lei está navegando recomendaciones de comida y cambia automáticamente a "Modo casual" — las recomendaciones de restaurantes se centran más en el ambiente y preferencias de sabor, y el tono se vuelve relajado e informal.
>
> Dos versiones, el mismo Zhang Lei.

---

## Faying Thinking

Faying Thinking son los activos cognitivos de iFay, conteniendo cuatro subtipos:

| Subtipo | Descripción | Ejemplos |
|---------|-------------|----------|
| **Contenido** | Activos de contenido estructurado o no estructurado | Colección de fotos del Human Prime, artículos escritos, música compuesta, videos grabados |
| **Datos** | Datos personales | Datos de monitoreo de salud, registros de gastos, hábitos de uso de apps, historial de ubicación |
| **Base de conocimiento** | Sistemas de conocimiento organizados | Notas de dominio profesional, bibliotecas de materiales de estudio, resúmenes de experiencia laboral, informes de investigación de la industria |
| **Info Feed** | Suscripciones de información en tiempo real | Fuentes de noticias seguidas, feeds de actualizaciones de la industria, actualizaciones de redes sociales, cotizaciones de acciones |

Los datos en la dimensión Thinking provienen de la inicialización y acumulación continua del Montón de datos personales, formando la base para que iFay entienda el mundo y tome decisiones.

---

## Faying Skills

Faying Skills son las capacidades de acción de iFay, conteniendo seis tipos de habilidades:

| Tipo | Descripción |
|------|-------------|
| **API** | Interfaces de programación directamente invocables, como API de consulta meteorológica, API de traducción |
| **Workflow** | Procesos automatizados de múltiples pasos, como "generar informe semanal cada lunes y enviar al equipo" |
| **Bot** | Bots conversacionales para escenarios específicos, como Bot de atención al cliente, Bot de citas |
| **Agent** | Agentes inteligentes con toma de decisiones autónoma, como Agent de análisis de inversiones |
| **APP** | Aplicaciones completas, como APP de gestión de calendario, APP de seguimiento de salud |
| **Microservicio** | Unidades de servicio desplegadas independientemente, como servicio de reconocimiento de imágenes, servicio de voz a texto |

El registro de habilidades es un prerrequisito para que iFay realice cualquier acción. Las habilidades registradas completan la preautorización, asegurando que no se necesite autenticación adicional durante la ejecución.

---

## Faying Hardware

El hardware son las "extremidades" de iFay. iFay es una entidad de personalidad y cognición; el hardware es su vehículo para interactuar con el mundo físico.

### Tres subtipos de hardware

| Subtipo | Descripción | Ejemplos |
|---------|-------------|----------|
| **Dispositivo** | Dispositivos de hardware terminal | Teléfono, computadora, smartwatch, dron, dispositivos de hogar inteligente |
| **Almacenamiento** | Recursos de almacenamiento de datos | Almacenamiento en la nube, disco duro local, NAS, base de datos vectorial |
| **Computación** | Recursos de computación | GPU, nodos de computación en la nube, dispositivos de computación de borde |

### Mecanismo de descubrimiento de hardware

Cuando iFay migra a un nuevo entorno, el dispositivo terminal es responsable de escanear hardware compatible con Faying en el entorno actual — similar a cómo Bluetooth o WiFi escanean dispositivos cercanos. iFay en sí no realiza directamente el escaneo de hardware; en cambio, realiza coincidencia de capacidades basándose en los resultados del escaneo.

Hay una distinción clave aquí:

- **Qué hardware puede operar iFay** depende de sus capacidades cognitivas (habilidades registradas, habilidades internas)
- **A qué hardware puede conectarse iFay** depende de los dispositivos realmente disponibles en el entorno actual

### Escenario

> Imagina a una persona que sabe jugar bádminton entrando a un pabellón deportivo.
>
> "Saber jugar bádminton" es su **habilidad** — es su propia capacidad que lleva a donde vaya. Pero si realmente puede jugar depende de si el pabellón tiene **raquetas** — ese es el hardware proporcionado por el entorno.
>
> iFay funciona de la misma manera. Podría tener la habilidad de controlar un dron (registró una API de control de vuelo), pero si no hay un dron conectable en el entorno actual, esa habilidad no puede ejercerse. Por el contrario, incluso si hay una impresora 3D en el entorno, si iFay no ha registrado la habilidad de operación relevante, solo puede "ver" el dispositivo pero no puede usarlo.

---

## Faying Permissions

Los permisos son las "relaciones" de iFay — definen los límites de confianza entre iFay y el mundo externo.

### Tres ciclos de vida de permisos

| Ciclo de vida | Descripción | Ejemplos |
|---------------|-------------|----------|
| **Inherente** | Permisos poseídos desde la creación | Acceso al calendario del Human Prime, lectura de configuraciones de preferencias del Prime |
| **Persistente** | Permisos válidos a largo plazo | Acceso de lectura/escritura al correo del Prime, acceso a la intranet corporativa |
| **Efímero** | Solicitados cuando se necesitan, liberados después del uso | Acceso único a registros médicos, derechos temporales de llamada API |

### Métodos de autenticación extensibles

Los métodos de autenticación de iFay son extensibles, soportando SSO, OAuth, Fingerprint y otros métodos. "Fingerprint" aquí es un término colectivo que cubre cualquier identificador reconocible de identidad — reconocimiento facial, huella de voz, huella del dispositivo, etc. Diferentes tipos de fingerprint tienen diferentes niveles de confianza: el reconocimiento facial puede tener mayor confianza que la huella del dispositivo, mientras que las combinaciones multifactor tienen mayor confianza que los factores individuales.

### Escenario

> El iFay de Wang Fang tiene tres permisos con diferentes ciclos de vida:
>
> **Inherente**: Cuando iFay fue creado, automáticamente ganó acceso al calendario de Wang Fang — esta es una capacidad básica de cada iFay, sin necesidad de solicitud adicional.
>
> **Persistente**: Wang Fang autorizó a iFay para gestionar su correo de trabajo a largo plazo. iFay puede leer correos, redactar respuestas y gestionar etiquetas — este permiso permanece válido hasta que Wang Fang lo revoque activamente.
>
> **Efímero**: Wang Fang necesita ver el informe de examen físico del año pasado. Le pide a iFay que recupere registros del sistema hospitalario. iFay solicita temporalmente permiso de acceso único a datos médicos, y después de obtener el informe, el permiso se libera automáticamente — la próxima vez que se necesite, se requiere una nueva solicitud.

---

## Visibilidad del Perfil

La visibilidad del Perfil es una preocupación de la capa de aplicación, determinada por escenarios de aplicación específicos y métodos de interacción.

El mismo Perfil iFay muestra diferentes dimensiones en diferentes escenarios: durante la colaboración entre Fays, la otra parte puede solo necesitar ver las dimensiones de habilidades y permisos; en la interfaz de gestión del Human Prime, las seis dimensiones son completamente visibles; en escenarios sociales públicos, solo se puede mostrar la identidad e información parcial de habilidades.

El Perfil en sí no define "quién puede ver qué" — esa decisión se deja a la aplicación que usa el Perfil.
