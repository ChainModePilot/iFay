# 2. Definición y concepto

## Términos específicos del producto

### iFay
Individual Fay. Un avatar digital vinculado a una persona natural (llamada **Human Prime**, o **Prime** para abreviar), comprometido a alinearse con la persona natural (Human Prime) a la que está vinculado en términos de valores, personalidad y hábitos. iFay es una Instanciación (réplica) de la personalidad del Human Prime, fusionando los rasgos de personalidad del Prime con capacidades digitales, con el objetivo de asumir el trabajo mecánico, repetitivo, peligroso y las tareas auxiliares tediosas del Prime, mejorar la seguridad, salud y calidad de vida del Prime, y amplificar el valor social del Prime.

### coFay
Common Fay, un avatar digital que asume roles públicos, aproximadamente equivalente al concepto actual de un Agent. Posee conocimientos y habilidades generales en un dominio específico y puede servir a múltiples personas a través de conversación. coFay es un proyecto independiente; la especificación iFay solo lo referencia cuando es necesario.

### Fay
Término colectivo para iFay y coFay, un término general para agentes de IA personificados. Puede convertirse en un nodo importante en nuevos tipos de relaciones sociales.

### FayID
Un identificador persistente globalmente único asignado a cada Fay, legible por humanos y por máquinas. FayID utiliza un mecanismo unificado de generación y gestión de identificadores tanto para iFay como para coFay, soportando una capacidad de identificadores que excede la escala de la población mundial.

### FayGer
Un contenedor que proporciona un entorno de ejecución virtual para Fay (iFay y coFay), similar a Docker. Esto asegura que Fay pueda Inhabit diferentes hardware y software multiplataforma, imbuiéndolos con la voluntad personal del Human Prime. FayGer proporciona herramientas de compilación multilenguaje y contenedores de ejecución multiplataforma, permitiendo que cualquier Fay (independientemente del lenguaje de desarrollo) sea empaquetado y ejecutado.

### Modelo Ego
El micro-modelo personalizado de iFay, alineado con el perfil de un individuo específico. Ego es un modelo pequeño de borde conectable e intercambiable que puede cargarse en cualquier dispositivo terminal para darle la personalidad del Human Prime. Ego restringe a iFay para alinearse con el Prime en dimensiones como orientación de valores, preferencias de interés, hábitos, límites cognitivos, límites de habilidades, límites de permisos y estilo de trabajo. Opera independientemente de los modelos grandes externos, asegurando la estabilidad de la personalidad. Soporta gestión multiversión y cambio de personalidad para acomodar las necesidades de personalidad multifacética del Prime en diferentes escenarios.

> ⚠️ **Restricción ética**: El cambio de versión de Ego debe seguir el principio de transparencia. Todas las versiones de Ego deben compartir el mismo conjunto de valores fundamentales; las diferencias se limitan al estilo de expresión y preferencias de interacción. Al cambiar, el identificador de la versión de Ego actualmente activa debe anotarse en los metadatos de interacción para garantizar la auditabilidad.

### Perfil iFay
El modelo de datos unificado de iFay, una tabla de atributos semánticamente interpretable. Usado para que humanos y sistemas identifiquen a iFay, así como para que los Fays se identifiquen entre sí — es la "tarjeta de identidad" completa de iFay. Contiene seis dimensiones: Identidad iFay (FayID + metadatos), Modelo Ego (referencia a la versión activa actual de Ego), Faying Thinking, Faying Skills, Faying Hardware, Faying Permissions. El perfil del Human Prime (Conciencia alineada) es un subconjunto y fuente de entrada del Perfil.

### FayManifest
El archivo de configuración de ensamblaje declarativo de iFay, similar a package.json. Declara los componentes, protocolos, modos de control (control por comando / control Ego / control autónomo) y configuraciones requeridas para una implementación de iFay. Los desarrolladores solo necesitan declarar "qué se necesita" en lugar de "cómo implementarlo". Soporta declaraciones mínimas — declarar solo un subconjunto de componentes es suficiente para salir al mercado, y el sistema complementa automáticamente las dependencias de infraestructura requeridas.

### GMChain
**Global Merit Chain (GMC)**, el libro de contribución social del ecosistema iFay — una infraestructura blockchain que construye reputación y voz mediante el registro y la medición de contribuciones sociales identificables. GMChain abarca todos los niveles del framework CPE+M, proporcionando mecanismos unificados de rastreo de contribuciones e incentivos para humanos, iFay, coFay y proveedores de servicios. A diferencia de la mayoría de los proyectos blockchain, GMChain depende enteramente del reconocimiento del valor social para acumular puntos, en lugar de consumir poder de cómputo para completar tareas computacionales. GMChain no acepta inyección monetaria, y MeriToken no es intercambiable con moneda fiat. Pertenece al componente de visión a largo plazo de la Fase 5 de la Hoja de ruta, pero las definiciones de interfaz necesitan ser reservadas en fases tempranas.

### MeriToken
**MeriToken**, la unidad de medición de contribución social en GMChain. MeriToken no es moneda — es una credencial cuantificada para reputación, voz e incentivos de colaboración. La adquisición se basa en crear valor social (como completar tareas colaborativas, proporcionar servicios API, contribuir poder de cómputo, etc.), en lugar de consumir poder de cómputo para completar trabajo técnico de blockchain. El Libro mayor de MeriToken registra las contribuciones acumuladas, la puntuación de reputación y el peso de voz de cada participante.

### μ (MU)
Merit Unit, la unidad de medida para MeriToken.

### iFACTS
iFay Architecture Conformance Test Suite, un conjunto de pruebas de conformidad estandarizado. Cubre puntos clave de la especificación incluyendo interacciones de protocolo, interfaces de módulos y comportamientos de seguridad, comprendiendo cuatro niveles de prueba: L1 Conformidad de Componente Individual, L2 Conformidad de Interfaz, L3 Conformidad de Integración, L4 Conformidad Conductual. Las implementaciones de los proveedores deben pasar las pruebas iFACTS para afirmar que su producto es "iFay Ready".

### iFay Ready
El estándar de certificación que los productos de aplicación deben cumplir para ser operados por iFay, dividido en tres niveles:
- **Bronce**: Soporta que iFay opere la aplicación mediante operaciones simuladas (Rastreador en primera persona + Operación simulada)
- **Plata**: Soporta que iFay controle directamente la aplicación vía protocolo CAP, soporta intercambio de datos por protocolo DTP
- **Oro**: Soporta que iFay comparta habilidades vía protocolo SSP, soporta integración completa de arquitectura C/F/S

### Tutor
Una persona natural designada para asumir los derechos de gestión de iFay cuando el Human Prime fallece o no puede gestionar iFay. Nota: deliberadamente no se usa el término "heredero". El Tutor completa la verificación de identidad mediante activación de frase mnemónica o métodos de autenticación de identidad preespecificados por el Prime.

### Tutela
El proceso y estado del Human Prime transfiriendo los derechos de gestión de iFay a un Tutor. Después de que la transferencia de tutela se completa, iFay se vincula al nuevo Tutor y actualiza la relación de emparejamiento del protocolo Faying.

### Cementerio digital
Un entorno sandbox dedicado donde iFay continúa operando como una identidad independiente después del fallecimiento del Human Prime. El Cementerio digital restringe el alcance conductual de iFay, evitando que iFay continúe ejecutando tareas preestablecidas por el Prime que podrían causar confusión y pérdidas, asegurando seguridad y aislamiento.

***

## Aclaraciones de conceptos generales

### Contexto
El entorno externo en el que Fay opera, incluyendo objetivos de comunicación, modos de interacción, mensajes transmitidos, el significado expresado por los mensajes, hardware y software controlable, recursos y habilidades invocables, etc.

### Protocolo
Incluye definiciones de anotación para almacenamiento de datos, cuerpos de mensajes, parámetros y estructuras de interfaz, así como convenciones de flujo de interacción para propósitos específicos.

### Credenciales
Un concepto amplio que se refiere a cualquier identificador digital usado para identificar de forma única personas, cosas u objetos, que no puede ser manipulado ni negado. Incluye FayID, contraseñas de cuentas, certificados, autorizaciones, tokens de acceso, contratos inteligentes y tokens digitales (MeriToken).

### Human Prime
La persona natural cuya personalidad es replicada por iFay. iFay está profundamente vinculado al Human Prime, instanciando los rasgos de personalidad del Prime y fusionándolos con capacidades digitales.

### Instanciación (réplica)
El proceso de generar un iFay alineado con el Human Prime. La Instanciación no es una simple copia de datos, sino el proceso de inyectar estructuralmente la personalidad, datos y permisos del Human Prime en iFay.

### Inhabit
El proceso de inyectar iFay en un dispositivo de hardware terminal o aplicación de software para que iFay pueda controlar ese terminal. Después de Inhabit, el terminal se convierte en la "extremidad" de iFay, y iFay puede controlar directamente las funciones de hardware y software del terminal mediante el protocolo CAP.

### Host
El hardware terminal o aplicación de software que es habitado y controlado por iFay. Nota: Host se refiere al dispositivo terminal o aplicación, no al Human Prime.

### Faying
El proceso y estado de iFay estableciendo una conexión con el Human Prime o un terminal, similar al emparejamiento Bluetooth. Cuando iFay está en estado Faying con el Prime, iFay permanece activado. Faying debe seguir las condiciones de emparejamiento seguro especificadas por el Protocolo Faying, asegurando que iFay solo esté autorizado a ejecutarse bajo la intención explícita del Prime.

### Separating
El proceso de iFay desconectándose del Human Prime y entrando en hibernación. Cuando iFay está en estado Separating con el Prime, iFay cambia al modo de hibernación, guarda una instantánea del estado actual y completa la separación.

***

## Nombres de módulos

iFay adopta una arquitectura de cuatro capas que comprende 12 módulos centrales:

### Capa Social

| Módulo | Descripción |
|--------|-------------|
| **Gestión de Credenciales** | Gestiona siete tipos de credenciales (FayID, contraseñas de cuentas, certificados, autorizaciones, tokens de acceso, contratos inteligentes, tokens digitales), soportando delegación segura y mecanismos de copia para las credenciales del Human Prime |

### Capa de Interacción — Percepción

| Módulo | Descripción |
|--------|-------------|
| **Rastreador en primera persona** | Simula la perspectiva en primera persona del Human Prime, capturando información visual y auditiva en la pantalla o interfaz, priorizando la percepción visual sobre el análisis de documentos estructurados |
| **Sensor** | El sistema nervioso generalizado de iFay, conectando sensores de dispositivos terminales basándose en los protocolos CAP y DTP, soportando ajuste dinámico de sensibilidad |
| **Autoconciencia** | Un módulo que monitorea las reacciones del Human Prime hacia adentro para inferir intención, similar a la capacidad de un asistente hábil para leer las expresiones faciales del jefe |

### Capa de Interacción — Acción

| Módulo | Descripción |
|--------|-------------|
| **Operación simulada** | Simula operaciones de interacción humana con UI (clic, arrastre, desplazamiento, gestos, etc.), explorando adaptativamente interfaces a través de la retroalimentación del Rastreador en primera persona |
| **Invocación de habilidades** | Un módulo de acción que activa directamente habilidades registradas o ejecuta tareas específicas, similar a llamadas a funciones o llamadas API |
| **Comportamiento autónomo** | Un módulo de comportamiento activado autónomamente que soporta tres fuentes de activación: tareas programadas, inferencia de autoconciencia y habilidades persistentes, formando un bucle "acción → retroalimentación → re-acción" |

### Capa de Cognición — Pensamiento

| Módulo | Descripción |
|--------|-------------|
| **Montón de datos personales** | Gestión unificada de todos los datos privados de iFay, soportando múltiples formatos y ubicaciones de almacenamiento, proporcionando una interfaz unificada de lectura/escritura a los módulos internos |
| **Conocimiento externo** | Un módulo de acceso a bases de conocimiento y modelos externos, integrando inteligencia externa como un tipo de habilidad, accediendo a servicios abiertos mediante el protocolo SSP |
| **Conciencia alineada** | Una descripción completa del perfil personal del Human Prime, soportando establecimiento y actualizaciones a través de tres métodos: minería de datos, ajuste en tiempo real vía autoconciencia y definición manual por el Prime |

### Capa de Cognición — Habilidades

| Módulo | Descripción |
|--------|-------------|
| **Hub de controladores** | La capa hub para controladores de dispositivos, integrando nuevos controladores a través de interfaces estandarizadas, asegurando la estabilidad de la arquitectura interna cuando se integran nuevos controladores |
| **Habilidades registradas** | Habilidades que iFay ha dominado u obtenido la capacidad de usar, soportando seis tipos de habilidades (API, Workflow, Bot, Agent, APP, Microservicio) |
| **Habilidades internas** | Un módulo de capacidad inherente alineado con la personalidad del Human Prime, proporcionando mecanismos de introspección para asegurar que el conocimiento externo no entre en conflicto con la intención del Prime |

### Capa Ego

| Módulo | Descripción |
|--------|-------------|
| **Modelo Ego** | El micro-modelo personalizado de iFay, un modelo pequeño de borde conectable e intercambiable que opera independientemente de los modelos grandes externos, asegurando la estabilidad de la personalidad |

***

## Nombres de protocolos

El sistema de protocolos de iFay incluye seis protocolos centrales:

| Protocolo | Descripción |
|-----------|-------------|
| **Protocolo Faying** | Un protocolo que especifica las condiciones para el emparejamiento seguro y la activación entre una persona natural e iFay, asegurando que iFay solo esté autorizado a ejecutarse bajo la intención explícita del Human Prime |
| **Protocolo de Conversación Interactiva** | Un protocolo semántico multimodal modular para interfaces de usuario humanas, modularizando y multimodalizando el contenido semántico para que los clientes puedan reconstruir visualizaciones de mensajes legibles y amigables |
| **Protocolo de Telepatía** | Un protocolo de comunicación semántica entre Fays que elimina la capa de traducción de UI (es decir, comunicación directa por vectores semánticos sin interfaz de usuario, también conocido como Protocolo Semántico Directo), permitiendo que el significado y la intención se transmitan directamente entre Fays, usando tokens codificados en vectores acordados en lugar de texto estructurado |
| **Protocolo de Autoridad de Control (CAP)** | Usado para que iFay tome el control del hardware terminal y software específico, llamando directamente a controladores, interfaces locales y comandos |
| **Protocolo de Túnel de Datos (DTP)** | Un protocolo de transmisión bidireccional entre terminales e iFay. La dirección Terminal→iFay soporta almacenamiento persistente de datos de usuario y custodia de datos; la dirección iFay→Terminal soporta enriquecimiento de datos y procesamiento personalizado |
| **Protocolo de Compartición de Habilidades (SSP)** | Abre servicios e interfaces que anteriormente solo estaban disponibles para clientes a toda la red a través de un protocolo remoto estandarizado |

***

## Dimensiones del Perfil iFay

El Perfil iFay contiene seis dimensiones, de las cuales cuatro dimensiones Faying describen las capacidades y recursos de iFay:

### Identidad iFay
FayID + metadatos, el marcador de identidad fundamental de iFay.

### Modelo Ego
Referencia a la versión de Ego actualmente activa; solo una versión está activa en un momento dado.

### Faying Thinking
La dimensión de recursos cognitivos de iFay, conteniendo cuatro subtipos:
- **Contenido** — Activos de contenido estructurado y no estructurado
- **Datos** — Datos personales del Human Prime
- **Base de conocimiento** — Sistemas de conocimiento organizados
- **Info Feed** — Suscripciones de información en tiempo real y notificaciones push

### Faying Skills
La dimensión de capacidades de iFay, conteniendo seis tipos de habilidades:
- **API** — Llamadas a interfaces estandarizadas
- **Workflow** — Orquestación de flujos de trabajo
- **Bot** — Bots conversacionales
- **Agent** — Agentes inteligentes
- **APP** — Aplicaciones
- **Microservicio** — Microservicios

### Faying Hardware
La dimensión de hardware de iFay — las "extremidades" de iFay. Cuando iFay migra, el terminal escanea e intenta conectarse al hardware disponible. Contiene tres subtipos:
- **Dispositivo** — Dispositivos de hardware terminal
- **Almacenamiento** — Recursos de almacenamiento de datos
- **Computación** — Recursos de computación

### Faying Permissions
La dimensión de permisos de iFay — las "relaciones" de iFay. Soporta métodos de autenticación extensibles como SSO, OAuth, Fingerprint (un término colectivo para cualquier identificador reconocible de identidad), etc. Los ciclos de vida de permisos se dividen en tres tipos: inherente, persistente y efímero.
