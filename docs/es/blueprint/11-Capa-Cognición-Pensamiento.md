# 11. Capa de Cognición — Pensamiento

El subsistema de Pensamiento de la Capa de Cognición es el "centro de memoria y comprensión" de iFay — gestiona la memoria de iFay, adquiere conocimiento externo y mantiene una comprensión profunda de ti.


---

## 11.2 Conocimiento externo

## Definición en una línea

El Conocimiento externo es la **biblioteca y consultor experto** de iFay — el Montón de datos personales es la memoria propia de iFay, mientras que el Conocimiento externo es la biblioteca que iFay puede consultar y los expertos a los que puede preguntar. Le da a iFay conocimiento más allá de las propias capacidades del Human Prime.

## Por qué es necesario

No importa qué tan buena sea tu memoria, no puedes recordar todo. Cuando encuentras un problema que no entiendes, ¿qué haces? Vas a la biblioteca a buscar, o consultas a un profesional.

iFay funciona de la misma manera. El Montón de datos personales almacena tus propios datos y recuerdos, pero tu conocimiento es limitado. El módulo de Conocimiento externo permite a iFay **ir más allá de su propia memoria** para consultar bases de conocimiento externas y consultar modelos inteligentes externos — igual que una persona entrando a una biblioteca o llamando a un experto.

## Su posición en la arquitectura

```
Arquitectura de cuatro capas de iFay
├── Capa Social
├── Capa de Interacción
│   └── ...
├── Capa de Cognición          ← El Conocimiento externo está aquí
│   ├── Pensamiento
│   │   ├── Montón de datos personales   ← Tu propia memoria
│   │   ├── 👉 Conocimiento externo      ← Biblioteca y consultor experto
│   │   └── Conciencia alineada          ← Comprensión de ti
│   └── Habilidades
│       ├── Habilidades registradas      ← Las fuentes de conocimiento externo son también un tipo de "habilidad"
│       └── ...
└── Capa Ego
```

El Conocimiento externo se encuentra en el **subsistema de Pensamiento de la Capa de Cognición**. Lo que lo hace único: las fuentes de conocimiento externo se tratan como un **tipo de habilidad** dentro del sistema de iFay. Esto significa que la integración de conocimiento externo sigue el mismo flujo de registro, autorización e invocación que otras habilidades.

## Cómo funciona

La operación del Conocimiento externo se puede resumir en tres palabras clave: **Conectar, Consultar, Integrar**.

**1. Conectar — Enlazar a fuentes de conocimiento externo**

Las fuentes de conocimiento externo vienen en muchas variedades:
- **Bases de conocimiento**: Bases de conocimiento médico, legal, enciclopedias
- **Modelos de lenguaje grandes**: GPT, Claude y otros modelos de IA generales
- **Sistemas expertos**: Sistemas de razonamiento especializados para dominios específicos
- **Motores de búsqueda**: Información pública en internet

Estas fuentes de conocimiento se conectan a iFay a través de **SSP (Protocolo de Compartición de Habilidades)**.

**2. Consultar — Hacer preguntas como consultar a un experto**

Cuando iFay necesita conocimiento externo, envía una solicitud de consulta a la fuente de conocimiento correspondiente. Cada resultado de consulta viene con una **puntuación de confianza** — diciéndole a iFay qué tan fiable es la respuesta.

**3. Integrar — El conocimiento aprendido se vuelve propio**

La información adquirida de fuentes de conocimiento externo no es solo "usar y descartar". El conocimiento importante se integra en el Montón de datos personales, convirtiéndose en parte de la propia memoria de iFay.

**¿Qué pasa si una fuente de conocimiento no está disponible?**

La red podría desconectarse, o una fuente de conocimiento podría estar fuera de línea. En ese caso, el módulo de Conocimiento externo **recurre al conocimiento en caché del Montón de datos personales**. Mientras tanto, iFay notifica a la Capa de Cognición que "actualmente usa conocimiento en caché, que puede no ser el más reciente."

## Historias de escenarios

### Escenario 1: Ayudarte a entender un informe de chequeo médico

Recibes tu informe anual de chequeo médico, lleno de indicadores incomprensibles: triglicéridos 2,8 mmol/L, colesterol LDL 3,9 mmol/L, ácido úrico 480 μmol/L…

Le dices a iFay: "Ayúdame a revisar este informe de chequeo — ¿hay algo que deba preocuparme?"

iFay se pone a trabajar:
1. Primero recupera tus datos de chequeo de los últimos tres años del Montón de datos personales (su propia memoria)
2. Luego consulta una **base de conocimiento médico** externa (la biblioteca): ¿cuál es el rango normal para cada indicador? ¿Qué significa excederlo?
3. Después de un análisis integral, te dice:

"Tus triglicéridos están elevados (lo normal debería ser inferior a 1,7, el tuyo es 2,8), y tu colesterol LDL también está alto (lo normal debería ser inferior a 3,4, el tuyo es 3,9). Ambos indicadores han subido comparados con el año pasado. Combinado con tus registros de comidas de los últimos tres meses (datos del Montón de datos personales), tu frecuencia de pedidos de comida a domicilio ha aumentado notablemente, con preferencia por alimentos altos en aceite y sal."

"Sugiero que prestes atención a tu salud de lípidos en sangre y consideres ajustar tu dieta. ¿Quieres que reserve una cita con cardiología?"

### Escenario 2: Ayudarte a redactar cláusulas de contrato

Eres dueño de una pequeña empresa que necesita firmar un contrato de adquisición con un proveedor. No estás muy familiarizado con el derecho contractual, pero no quieres pagar un abogado cada vez.

Le dices a iFay: "Ayúdame a redactar una cláusula de incumplimiento para un contrato de adquisición — si el proveedor retrasa la entrega más de 15 días, tenemos derecho a rescindir el contrato."

iFay se pone a trabajar:
1. Consulta una **base de conocimiento legal** externa: disposiciones legales y formulaciones comunes para cláusulas de incumplimiento en contratos de adquisición
2. Referencia plantillas de contratos que has firmado previamente del Montón de datos personales (su propia memoria)
3. Sintetiza un borrador de cláusula de incumplimiento incluyendo terminología legal y disposiciones protectoras

Al mismo tiempo, iFay te recuerda: "Este es un borrador generado a partir de la base de conocimiento legal. Recomiendo que un abogado profesional lo revise antes de la firma formal."

## Para desarrolladores

El Conocimiento externo pertenece a la **Fase 3 (iFay como interfaz al mundo virtual)** como módulo central.

- **ID de requisito**: Requisito 12 (Integración de Conocimiento externo)
- **Especificación de interfaz**: Interfaz `ExternalKnowledge` con tres métodos centrales: `query()` (consultar conocimiento externo), `registerSource()` (registrar fuente de conocimiento) y `fallbackToCache()` (recurrir a caché)
- **Tipos de fuentes de conocimiento**: `knowledge_base`, `llm` (Modelo de Lenguaje Grande), `expert_system`, `search_engine`
- **Protocolo asociado**: SSP (Protocolo de Compartición de Habilidades) para integración estandarizada de fuentes de conocimiento externo
- **Módulos asociados**: Montón de datos personales (`PersonalDataHeap`) integra conocimiento externo, Habilidades registradas (`RegisteredSkillManager`) gestiona el registro de fuentes de conocimiento, Habilidades internas (`InternalSkill`) verifica conflictos de conocimiento
- **Estrategia de respaldo**: Cuando las fuentes de conocimiento externo no están disponibles, recurre automáticamente al conocimiento en caché del Montón de datos personales y notifica a la Capa de Cognición
- **Pruebas de conformidad**: iFACTS L1 valida capacidades de consulta de conocimiento y respaldo a caché, L2 valida la interfaz de integración de conocimiento con el Montón de datos personales, L3 valida la cadena completa "consulta de conocimiento → integración → caché → respaldo"


---

## 11.3 Conciencia alineada

## Definición en una línea

La Conciencia alineada es la **comprensión completa de ti** por parte de iFay — si el Modelo Ego es la "personalidad" de iFay, la Conciencia alineada es la cognición profunda de iFay sobre ti como persona — tus valores, preferencias, hábitos y límites. Es la línea base para todo el comportamiento de iFay.

## Por qué es necesario

Imagina que tienes un asistente que ha estado contigo durante diez años. La razón por la que este asistente funciona tan bien no es por habilidades técnicas superiores, sino porque **te conoce tan bien**:

- Sabe que no te gustan las reuniones antes de las 10 AM
- Sabe que eres alérgico a los cacahuetes y los evita automáticamente al pedir comida
- Sabe que prefieres decisiones basadas en datos, así que los informes siempre incluyen gráficos
- Sabe que actualmente estás a dieta, así que no recomendará proactivamente postres

La Conciencia alineada es la versión de iFay de esta "comprensión completa" de ti. Mantiene un **perfil integral** sobre ti — no simples etiquetas ("hombre, 30, programador"), sino una comprensión multidimensional, continuamente actualizada y profundamente arraigada.

## Cómo funciona

El perfil del Human Prime mantenido por la Conciencia alineada contiene múltiples dimensiones: **orientación de valores, preferencias de interés, patrones de hábitos, límites cognitivos, límites de habilidades, límites de permisos y estilo de trabajo**.

Este perfil se establece y actualiza a través de **tres métodos**:

**1. Minería de datos — Entenderte a partir de tus datos**

La Conciencia alineada mina patrones de comportamiento del Montón de datos personales. Por ejemplo:
- Analizando tus pedidos de comida del último año, descubriendo que no has pedido platos de carne en los últimos tres meses → infiriendo que podrías haberte vuelto vegetariano
- Analizando tus datos de calendario, descubriendo que nunca programas reuniones de trabajo los fines de semana → infiriendo que valoras el equilibrio trabajo-vida

Este método es **pasivo y continuo** — iFay no necesita preguntarte; gradualmente te entiende observando tus datos.

**2. Ajuste en tiempo real — Leerte a partir de tus reacciones**

El módulo de Autoconciencia observa tus reacciones en tiempo real y pasa las observaciones a la Conciencia alineada. Por ejemplo:
- iFay recomendó una canción y la saltaste inmediatamente → la Conciencia alineada actualiza: no te gusta este estilo de música
- iFay escribió un correo por ti y revisaste mucho la redacción → la Conciencia alineada actualiza: tu estilo de correo es más formal de lo que iFay esperaba

Este método es **activo e inmediato** — iFay aprende de cada una de tus reacciones.

**3. Definición manual — Le dices a iFay directamente**

Algunas preferencias y límites puedes decírselos a iFay directamente:
- "No quiero que programes ninguna reunión antes de las 10 AM"
- "Soy alérgico a los cacahuetes — tenlo en cuenta al pedir comida para mí"
- "Usa tono formal para correos de trabajo, casual está bien para mensajes personales"

Los tres métodos se complementan: la minería de datos proporciona tendencias a largo plazo, el ajuste en tiempo real captura cambios inmediatos y la definición manual establece límites explícitos.

## Historias de escenarios

### Escenario 1: Descubrir que te has vuelto vegetariano a partir de datos de pedidos de comida

Durante los últimos tres meses, la función de minería de datos de la Conciencia alineada de iFay ha analizado tus registros de pedidos de comida en el Montón de datos personales:

- Hace tres meses: 70% de tus pedidos incluían platos de carne
- Hace dos meses: el ratio de platos de carne bajó al 30%, con opciones vegetarianas apareciendo frecuentemente
- El último mes: no has pedido ningún plato de carne, y has seguido a varios bloggers vegetarianos en redes sociales

La Conciencia alineada sintetiza estos datos y actualiza tu perfil: **la preferencia dietética ha cambiado de omnívoro a vegetariano**.

Esta actualización afecta inmediatamente el comportamiento de iFay:
- Cuando dices "pídeme comida a domicilio", iFay recomienda solo restaurantes vegetarianos
- Cuando iFay planifica un viaje para ti, marca específicamente restaurantes amigables con vegetarianos cerca del destino

Nunca le dijiste explícitamente a iFay "soy vegetariano ahora", pero iFay descubrió este cambio a través de la minería de datos por sí solo y ajustó automáticamente todos los comportamientos relacionados.

### Escenario 2: Le dices directamente a iFay una regla

Una mañana, te despierta una reunión a las 8 AM. Algo molesto, le dices a iFay: "De ahora en adelante, no programes ninguna reunión para mí antes de las 10 AM."

iFay responde inmediatamente: "Entendido. Todas las reuniones se programarán después de las 10 AM de ahora en adelante."

Esta es una **definición manual**. La Conciencia alineada actualiza inmediatamente tu perfil, añadiendo esta restricción a la dimensión de "patrones de hábitos".

El impacto de esta actualización es inmediato:
- Cuando alguien intenta reservarte para una reunión a las 9 AM mañana a través de iFay, iFay responde: "XX no está disponible antes de las 10 AM. ¿Funcionaría después de las 10?"
- Cuando el Comportamiento autónomo de iFay quiere recordarte una tarea de trabajo a las 8 AM, verifica la Conciencia alineada, encuentra la regla "sin molestias antes de las 10" y pospone el recordatorio a las 10 AM

## Para desarrolladores

La Conciencia alineada pertenece a la **Fase 4 (iFay + coFay Personificación completa)** como módulo central.

- **ID de requisito**: Requisito 16 (Conciencia alineada)
- **Especificación de interfaz**: Interfaz `AlignedConsciousness` con cuatro métodos centrales: `getProfile()` (obtener perfil del Human Prime), `mineFromDataHeap()` (actualización por minería de datos), `adjustFromAwareness()` (ajuste en tiempo real desde Autoconciencia) y `manualUpdate()` (definición manual del Human Prime)
- **Dimensiones del perfil del Human Prime**: Orientación de valores (`values`), preferencias (`preferences`), hábitos (`habits`), límites cognitivos (`cognitiveBoundaries`), límites de habilidades (`skillBoundaries`), límites de permisos (`permissionBoundaries`), estilo de trabajo (`workingStyle`)
- **Tres métodos de actualización**: Minería del Montón de datos personales (pasivo, continuo), ajuste en tiempo real vía Autoconciencia (activo, inmediato), definición manual del Human Prime (explícito, inmediato)
- **Módulos asociados**: Montón de datos personales (`PersonalDataHeap`) proporciona fuente de datos, Autoconciencia (`SelfAwareness`) proporciona retroalimentación en tiempo real, Modelo Ego (`EgoModel`) y Habilidades internas (`InternalSkill`) consumen datos del perfil
- **Relación con Perfil iFay**: El perfil del Human Prime (`HostProfile`) es un subconjunto y fuente de entrada del Perfil iFay
- **Pruebas de conformidad**: iFACTS L1 valida los tres métodos de actualización de perfil, L2 valida las interfaces de entrega de perfil con Modelo Ego y Habilidades internas, L4 valida el impacto real de las actualizaciones de perfil en las restricciones conductuales
