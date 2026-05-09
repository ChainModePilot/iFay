# 10. Capa de Interacción — Acción

El subsistema de Acción de la Capa de Interacción son los "efectores" de iFay — permite a iFay operar interfaces, invocar servicios y actuar proactivamente.


---

## 10.1 Operación simulada

## Definición en una línea

La Operación simulada son las **manos** de iFay — puede hacer clic, arrastrar, desplazar y escribir como un humano, operando cualquier interfaz de software existente sin que el software necesite modificaciones específicas para IA.

## Por qué es necesario

Imagina que has contratado un nuevo asistente y quieres que maneje varias tareas en tu computadora y teléfono. Pero el problema es: el software que usas — sitios web bancarios, sistemas de seguros, plataformas de servicios gubernamentales — están todos diseñados para humanos, y ninguno proporciona una "entrada exclusiva para IA".

¿Qué hacer? El enfoque más directo: **hacer que el asistente opere estas aplicaciones de software igual que tú lo harías**. Ver un botón, hacer clic. Ver un formulario, llenarlo. Ver una página, desplazarla.

Esa es la importancia de la Operación simulada. Permite a iFay ayudarte a hacer las cosas **ahora mismo**, sin esperar a que cada pieza de software en el mundo sea rediseñada para IA.

Pero la Operación simulada es fundamentalmente diferente de los "scripts de automatización" tradicionales (como RPA). RPA es como un actor que solo puede recitar líneas memorizadas — sigue un guión preescrito paso a paso, y se atasca si la interfaz cambia ligeramente. La Operación simulada de iFay es **guiada por percepción**: "ve" la pantalla a través del Rastreador en primera persona, entiende el estado actual de la interfaz, luego decide qué hacer a continuación. Igual que un usuario humano real — incluso si un sitio web se rediseña, puedes encontrar intuitivamente la nueva ubicación del botón.

## Su posición en la arquitectura

```
Arquitectura de cuatro capas de iFay
├── Capa Social
├── Capa de Interacción          ← La Operación simulada está aquí
│   ├── Percepción (Sentido)
│   │   ├── Rastreador en primera persona   ← Ojos: ve lo que hay en pantalla
│   │   ├── Sensor                          ← Sistema nervioso: percibe el entorno
│   │   └── Autoconciencia                  ← Corazón: lee tu intención
│   └── Acción
│       ├── 👉 Operación simulada           ← Manos: clic, arrastre, escritura
│       ├── Invocación de habilidades       ← Boca: "llama" directamente a servicios
│       └── Comportamiento autónomo         ← Voluntad: decide cuándo actuar
├── Capa de Cognición
└── Capa Ego
```

La Operación simulada se encuentra en el **subsistema de Acción de la Capa de Interacción**, una de las tres formas en que iFay interactúa con el mundo externo. Su relación con el Rastreador en primera persona es la más estrecha — el Rastreador son los "ojos", la Operación simulada son las "manos", y juntos logran la **coordinación ojo-mano**.

## Cómo funciona

El flujo de trabajo central se puede resumir en tres palabras clave: **Percibir, Operar, Retroalimentar**.

**1. Percibir — Mirar primero, luego actuar**

Antes de realizar cualquier operación, iFay primero "ve" la interfaz actual a través del Rastreador en primera persona. No analiza el código HTML de la página web — **ve lo que se muestra en pantalla** como un humano: dónde están los botones, dónde están los campos de entrada, dónde están los menús desplegables.

**2. Operar — Interactuar como un humano**

iFay soporta todas las operaciones que los humanos pueden realizar en interfaces:
- **Clic**: Clic izquierdo en botones, clic derecho para abrir menús
- **Arrastre**: Arrastrar archivos, redimensionar ventanas
- **Desplazamiento**: Desplazar páginas arriba y abajo para ver más contenido
- **Escritura**: Ingresar texto en campos de entrada
- **Gestos de borde**: Deslizar desde los bordes de la pantalla para invocar barras laterales
- **Gestos multitáctiles**: Zoom con dos dedos, cambio de app con tres dedos

**3. Retroalimentar — Verificar resultados después de cada acción**

Después de cada operación, iFay vuelve a "mirar" la interfaz a través del Rastreador en primera persona para confirmar si la operación tuvo éxito. Si se hizo clic en un botón pero la página no cambió, iFay se da cuenta de que "este botón podría no haber respondido" e intenta otro enfoque.

Este bucle "operar → observar → ajustar" es la diferencia fundamental entre la Operación simulada y los scripts RPA. RPA es un ciego palpando un elefante — ejecutando scripts sin importar los resultados. iFay trabaja con los ojos abiertos — viendo, pensando y ajustando en cada paso.

**¿Qué pasa con interfaces desconocidas?**

Cuando iFay encuentra una interfaz que nunca ha visto, **explora** como un humano: intenta hacer clic en un botón para ver qué pasa, pasa el ratón sobre un icono para verificar si hay texto de tooltip, desplaza la página para ver qué hay debajo. A través de esta exploración, iFay gradualmente entiende la estructura y funcionalidad de la interfaz.

## Relaciones con otros módulos

| Módulo relacionado | Relación | Analogía con el cuerpo humano |
|-------------------|----------|-------------------------------|
| **Rastreador en primera persona** | Los "ojos" de la Operación simulada — percibe el estado de la interfaz antes y después de cada operación | Manos ↔ Ojos (coordinación ojo-mano) |
| **Invocación de habilidades** | Ambos en el subsistema de Acción, pero enfoques diferentes: la Operación simulada trabaja a través de interfaces, la Invocación de habilidades llama APIs directamente | Operar a mano vs. hacer una llamada telefónica |
| **Comportamiento autónomo** | El Comportamiento autónomo decide "cuándo actuar", la Operación simulada maneja "cómo actuar" | La voluntad decide la acción → las manos ejecutan |
| **Modelo Ego** | Ego restringe el estilo de comportamiento de la Operación simulada (ej., velocidad de operación, nivel de cautela) | La personalidad influye en cómo se hacen las cosas |
| **Gestión de Credenciales** | La Operación simulada necesita credenciales de la Gestión de Credenciales al iniciar sesión | Las manos toman llaves para abrir puertas |

## Historias de escenarios

### Escenario 1: Llenar un formulario complejo de reclamación de seguro

Tuviste un accidente de coche menor y necesitas llenar una reclamación en el sitio web anticuado de la compañía de seguros. El sitio probablemente fue diseñado hace una década — el formulario tiene más de 30 campos distribuidos en 5 páginas, con varios menús desplegables y selectores de fecha.

Le dices a iFay: "Ayúdame a llenar la reclamación del seguro del coche — la del miércoles pasado por la tarde en la intersección de la calle Zhongshan y la calle Jianshe."

iFay se pone a trabajar:
1. "Ve" la página de inicio de sesión del sitio web de la aseguradora a través del Rastreador en primera persona, inicia sesión con tus credenciales delegadas
2. Encuentra la entrada "Solicitud de reclamación" y hace clic
3. Ve el formulario de la primera página: fecha del accidente, ubicación, tipo… iFay extrae información de tu descripción y del Montón de datos personales, llenando cada campo
4. Encuentra un botón "Subir fotos del accidente" — iFay hace clic, encuentra tus fotos de la escena en el selector de archivos y las sube
5. En la tercera página, descubre un menú desplegable con opciones diferentes a las esperadas (el sitio puede haberse actualizado) — iFay no se atasca; en cambio, lee cuidadosamente el texto de cada opción y selecciona la mejor coincidencia
6. En la página final de confirmación, iFay revisa cada elemento llenado, confirma que todo es correcto y hace clic en "Enviar"

Durante todo el proceso, iFay no está ejecutando un script preescrito — está trabajando como un asistente hábil, **mirando la pantalla, entendiendo el contenido, haciendo juicios**. Incluso si este sitio web se rediseña mañana, iFay aún puede completar la tarea — porque opera "viendo", no "memorizando".

### Escenario 2: Pedir comida a domicilio en el teléfono, adaptándose a actualizaciones de la app

Dices: "Pídeme lo mismo de la última vez en Meituan — el arroz con pollo estofado, entregar a la oficina."

iFay abre la app de Meituan pero encuentra que la interfaz se ve diferente — la app acaba de actualizarse, el diseño de la página principal cambió y la barra de búsqueda se movió.

Si esto fuera un script RPA, daría error y se detendría. Pero iFay no:
1. Escanea el nuevo diseño de la página principal a través del Rastreador en primera persona, encuentra que el icono de búsqueda se movió a la esquina superior derecha
2. Hace clic en el icono de búsqueda, escribe "arroz con pollo estofado"
3. En los resultados de búsqueda, identifica visualmente el restaurante donde pediste la última vez (coincidiendo nombre y logo de la tienda)
4. Entra a la página de la tienda, encuentra que el menú ha sido reorganizado — iFay desplaza el menú y encuentra "Arroz con Pollo Estofado"
5. Hace clic para añadir al carrito, confirma que la dirección de entrega es tu oficina
6. Completa el pedido

iFay demostró **exploración adaptativa** durante todo el proceso: no depende de diseños de interfaz fijos sino que entiende la interfaz actual a través de percepción visual y ajusta flexiblemente su estrategia de operación. Esta es la diferencia esencial entre "guiado por percepción" y "guiado por script".

## Para desarrolladores

La Operación simulada pertenece a la **Fase 1 (Simulación de operaciones humanas)** como módulo central.

- **ID de requisito**: Requisito 5 (Operación simulada)
- **Especificación de interfaz**: Interfaz `SimulatedOperation` con tres métodos centrales: `execute()`, `explore()` y `getPostActionState()`
- **Tipos de operación soportados**: `click`, `drag`, `scroll`, `gesture` (gestos de borde y multitáctiles), `type`
- **Módulos relacionados**: Rastreador en primera persona (`FirstPersonTracer`) proporciona retroalimentación visual; Gestión de Credenciales (`CredentialManager`) proporciona credenciales de inicio de sesión
- **Diseño central**: Guiado por percepción, no por script; después de cada operación, percibe cambios de estado a través del Rastreador, formando un bucle cerrado "operar → percibir → ajustar"; soporta exploración adaptativa de interfaces desconocidas
- **Pruebas de conformidad**: iFACTS L1 verifica la capacidad de ejecución para cada tipo de operación; L2 verifica la interfaz de coordinación ojo-mano con el Rastreador en primera persona
- **Relevancia iFay Ready**: La certificación Bronce requiere que las aplicaciones soporten la operación de iFay a través de Operación simulada


---

## 10.3 Comportamiento autónomo

## Definición en una línea

El Comportamiento autónomo es la **voluntad autónoma** de iFay — la Operación simulada son las manos, la Invocación de habilidades es la boca, y el Comportamiento autónomo es iFay decidiendo por sí mismo "cuándo actuar y cuándo hablar." Transforma a iFay de un ejecutor pasivo a un actor proactivo.

## Por qué es necesario

Imagina que tienes un excelente asistente. Si este asistente solo actúa cuando das comandos, entonces aún tienes que pensar en todo y dar cada instrucción tú mismo — esto no alivia verdaderamente tu carga, solo cambia "hacerlo tú mismo" por "decirle a alguien que lo haga".

¿Cómo es un asistente verdaderamente bueno? **Proactivamente** hace cosas:
- Prepara automáticamente tu resumen semanal de trabajo cada lunes por la mañana (**tarea programada**)
- Nota que frunces el ceño y suspiras, y proactivamente pregunta si has encontrado dificultades (**actuar después de leer el ambiente**)
- Una vez dijiste "revisa la logística cada vez que reciba una notificación de entrega", y siempre recuerda hacerlo automáticamente (**ejecutar hábitos continuamente**)

Esa es la importancia del Comportamiento autónomo. Le da a iFay "voluntad autónoma" — ya no solo espera a que hables, sino que juzga por sí mismo cuándo hacer qué, y luego proactivamente lo hace.

Pero hay un mecanismo de seguridad importante: si algo que iFay hace autónomamente resulta incorrecto, **pausa y te pregunta**. Como un buen asistente que ayuda proactivamente pero consulta contigo cuando no está seguro, en lugar de seguir adelante con su propio juicio.

## Su posición en la arquitectura

```
Arquitectura de cuatro capas de iFay
├── Capa Social
├── Capa de Interacción          ← El Comportamiento autónomo está aquí
│   ├── Percepción (Sentido)
│   │   └── Autoconciencia    ← Infiere tu intención ──┐
│   └── Acción                                          │
│       ├── Operación simulada   ← Manos                │
│       ├── Invocación de habilidades  ← Boca           │
│       └── 👉 Comportamiento autónomo ← Voluntad ←─────┘
├── Capa de Cognición
│   └── Habilidades
│       ├── Habilidades registradas  ← Fuente de habilidades persistentes
│       └── Habilidades internas     ← Fuente de habilidades persistentes
└── Capa Ego
```

El Comportamiento autónomo se encuentra en el **subsistema de Acción de la Capa de Interacción**, el más "avanzado" de los tres tipos de acción. La Operación simulada y la Invocación de habilidades son "cómo hacerlo"; el Comportamiento autónomo es "cuándo hacerlo y si hacerlo".

Tiene una fuente de entrada particularmente importante: el módulo de **Autoconciencia**. La Autoconciencia es responsable de "leerte", y el Comportamiento autónomo es responsable de "actuar proactivamente basándose en entenderte". Su coordinación transforma a iFay de una herramienta "tú dices, yo hago" a un compañero "te entiendo, te ayudo proactivamente".

## Cómo funciona

El Comportamiento autónomo tiene **tres tipos de activación**, como tres razones por las que los humanos hacen cosas proactivamente:

**1. Tareas programadas — Hacerlo cuando llega el momento**

El activador más simple, como una alarma que configuras. Le dices a iFay: "Genera el informe de trabajo de la semana pasada cada lunes a las 9 AM." iFay ejecutará esta tarea puntualmente cada lunes por la mañana.

**2. Inferencia de Autoconciencia — Sentir que necesitas algo, hacerlo proactivamente**

El activador más "inteligente". iFay observa tu estado y entorno a través del módulo de Autoconciencia, infiere lo que podrías necesitar, luego actúa proactivamente.

**3. Habilidades persistentes — Hábitos ejecutándose continuamente en segundo plano**

Algunas habilidades no son de una sola vez — se ejecutan continuamente. Por ejemplo, le dices a iFay "monitorea esta acción y alértame si baja de 50." Esta tarea se ejecuta continuamente en segundo plano hasta que la condición se activa.

**El bucle Acción → Retroalimentación → Re-acción**

Independientemente del tipo de activación, el Comportamiento autónomo sigue un bucle central:

1. **Acción**: iFay ejecuta una tarea decidida autónomamente
2. **Retroalimentación**: Observa los resultados de ejecución, juzga si cumplen las expectativas
3. **Re-acción**: Si los resultados cumplen las expectativas, continuar al siguiente paso; si no, ajustar estrategia o pausar para preguntar

**Válvula de seguridad: Pausar y confirmar**

Cuando iFay encuentra que los resultados del comportamiento autónomo son inconsistentes con tu intención, **pausa todas las acciones autónomas posteriores** y te pregunta: "Acabo de hacer XX por ti, pero el resultado no parece correcto. ¿Quieres continuar?" Este mecanismo asegura que la autonomía de iFay no se descontrole.

## Historias de escenarios

### Escenario 1: Auto-generar informe semanal cada lunes (Activación por tarea programada)

Lunes por la mañana 8:55, aún estás en el metro. La tarea programada de iFay se activa:

1. iFay extrae automáticamente los datos de trabajo de la semana pasada de tu Montón de datos personales — correos, calendario, completación de tareas en herramientas de gestión de proyectos, registros de commits de código
2. A través de la Invocación de habilidades, llama a una API de generación de documentos para organizar estos datos en un informe semanal bien estructurado
3. Después de la generación, iFay verifica si el contenido es razonable (ej., ¿falta algún proyecto importante?)
4. A las 9:00 en punto, llegas a la oficina, abres tu computadora y encuentras que iFay ha colocado el informe semanal en tu escritorio con una nota: "Pasaste más tiempo en el Proyecto A la semana pasada. El Proyecto B tiene dos tareas retrasadas — ¿quieres que ayude a ajustar el plan de esta semana?"

### Escenario 2: Reabastecer proactivamente la compra (Activación por Autoconciencia)

Miércoles por la noche, iFay descubre a través de los datos del sensor de tu refrigerador inteligente: solo queda un cartón de leche, 3 huevos restantes, compartimento de verduras casi vacío.

iFay combina la siguiente información para hacer un juicio:
- Tus hábitos alimenticios (registrados en Conciencia alineada: bebes leche cada mañana, usas unos 12 huevos por semana)
- Tus registros de compras recientes (datos en Montón de datos personales: la última compra fue hace 5 días)
- Hora actual (miércoles por la noche — si no reabasteces, podrías quedarte sin para el fin de semana)

iFay actúa proactivamente:
1. Genera una lista de compras: 2 cartones de leche, 1 caja de huevos, tus verduras habituales
2. A través de la Invocación de habilidades, llama a la API de la app de entrega de frescos para hacer un pedido
3. Antes de pedir, iFay pausa — porque el total excede tu presupuesto habitual de compra individual. Pregunta: "El refrigerador se está quedando vacío. He hecho una lista de compras — 186 yuanes en total, un poco más de lo usual porque añadí las verduras orgánicas que mencionaste querer probar la semana pasada. ¿Hago el pedido?"
4. Respondes "Claro", iFay completa el pedido

Nota el paso de "pausar y confirmar" — iFay encontró que el monto excedía tu presupuesto regular (resultado no completamente consistente con los hábitos del Human Prime), así que no pidió directamente sino que preguntó primero. Este es el mecanismo de seguridad del Comportamiento autónomo en acción.

## Para desarrolladores

El Comportamiento autónomo pertenece a la **Fase 4 (iFay + coFay Personificación completa)** como módulo central.

- **ID de requisito**: Requisito 14 (Comportamiento autónomo)
- **Especificación de interfaz**: Interfaz `SelfDrivenBehavior` con cuatro métodos centrales: `scheduleTask()` (tarea programada), `handleInference()` (manejar inferencia de autoconciencia), `pauseAndConfirm()` (pausar y confirmar) y `getLoopStatus()` (estado del bucle)
- **Tres fuentes de activación**: `scheduled` (tarea programada), `self_awareness` (inferencia de autoconciencia), `registered_skill` / `internal_skill` (habilidades persistentes)
- **Mecanismo central**: Bucle continuo acción → retroalimentación → re-acción; pausa y solicita confirmación cuando los resultados de ejecución son inconsistentes con la intención del Human Prime
- **Módulos relacionados**: Autoconciencia (`SelfAwareness`) proporciona inferencia de intención; Operación simulada e Invocación de habilidades manejan la ejecución real; Conciencia alineada (`AlignedConsciousness`) proporciona la línea base de restricción conductual
- **Pruebas de conformidad**: iFACTS L1 verifica la capacidad de respuesta a las tres fuentes de activación; L2 verifica la interfaz con el módulo de Autoconciencia; L4 verifica las restricciones de seguridad del comportamiento autónomo (mecanismo de pausar y confirmar)
