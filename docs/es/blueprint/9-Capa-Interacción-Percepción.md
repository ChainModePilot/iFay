# 9. Capa de Interacción — Percepción

El subsistema de Percepción de la Capa de Interacción son los "sentidos" de iFay — permite a iFay ver la pantalla, percibir el entorno y leer tus intenciones.


---

## 9.2 Sensor

## Definición en una línea

El Sensor es el **sistema nervioso** de iFay — permite a iFay percibir todos los cambios en el entorno circundante, desde temperatura y ubicación hasta ritmo cardíaco y luz, igual que las terminaciones nerviosas distribuidas por todo tu cuerpo.

## Por qué es necesario

Si el Rastreador en primera persona son los ojos y oídos de iFay, entonces el Sensor es toda la **red neuronal** de iFay.

Piensa en tu cuerpo: no solo percibes el mundo a través de ojos y oídos. Tu piel siente temperatura y tacto, tu oído interno siente equilibrio y aceleración, tu cuerpo te dice cuándo tienes hambre, estás cansado o tienes frío. Estas sensaciones no vienen de los ojos u oídos — vienen del sistema nervioso distribuido por todo tu cuerpo.

Ahora piensa en tu teléfono y smartwatch: el GPS sabe dónde estás, el acelerómetro sabe si estás caminando o corriendo, el sensor de luz sabe si estás en interiores o exteriores, el sensor de ritmo cardíaco sabe qué tan rápido late tu corazón. Todos estos son "sensores" — las terminaciones nerviosas del dispositivo.

El módulo Sensor de iFay **unifica el acceso** a todos estos sensores a través de dispositivos, dando a iFay un sistema nervioso completo. Y este sistema nervioso es continuamente expandible — cualquier nuevo tipo de sensor que surja en el futuro puede integrarse.

## Su posición en la arquitectura

```
Arquitectura de cuatro capas de iFay
├── Capa Social
├── Capa de Interacción          ← El Sensor está aquí
│   ├── Percepción (Sentido)
│   │   ├── Rastreador en primera persona   ← Mira hacia afuera, ve la pantalla
│   │   ├── 👉 Sensor                       ← Percibe el entorno (temperatura, ubicación, movimiento…)
│   │   └── Autoconciencia                  ← Mira hacia adentro, te lee
│   └── Acción
│       ├── Operación simulada
│       ├── Invocación de habilidades
│       └── Comportamiento autónomo
├── Capa de Cognición
│   ├── Pensamiento
│   │   ├── Montón de datos personales    ← Los datos del Sensor se almacenan aquí
│   │   └── ...
│   └── Habilidades
│       ├── Hub de controladores          ← Las interfaces de hardware del Sensor son gestionadas por él
│       └── ...
└── Capa Ego
```

El Sensor se encuentra en el **subsistema de Percepción de la Capa de Interacción**, junto con el Rastreador en primera persona y la Autoconciencia. Pero el Sensor tiene una característica especial: solo maneja el **ajuste de sensibilidad** (decidir cuándo recopilar más datos y cuándo recopilar menos), mientras que las conexiones reales de hardware y el almacenamiento de datos son manejados por el **Hub de controladores** y el **Montón de datos personales** de la Capa de Cognición respectivamente.

## Cómo funciona

El flujo de trabajo del Sensor se puede resumir en tres palabras clave: **Puente, Regular, Extender**.

**1. Puente — Conectar sensores de dispositivos**

Tu teléfono tiene GPS, giroscopio, acelerómetro, sensor de luz, barómetro… Tu smartwatch tiene sensor de ritmo cardíaco, sensor de oxígeno en sangre, sensor de temperatura de piel… Tu hogar inteligente tiene sensores de temperatura, humedad, puertas/ventanas…

El módulo Sensor actúa como un "traductor", traduciendo uniformemente datos de todos estos diferentes dispositivos y tipos de sensores a un formato que iFay puede entender. Usa **CAP (Protocolo de Autoridad de Control)** y **DTP (Protocolo de Túnel de Datos)** para lograr este puente.

**2. Regular — Sensibilidad dinámica**

Tu sistema nervioso tiene una característica inteligente: cuando estás concentrado en el trabajo, apenas sientes el tacto de la silla; pero cuando alguien te toca el hombro, lo sientes inmediatamente. Eso es regulación dinámica de sensibilidad.

El Sensor de iFay funciona de la misma manera. No necesita recopilar datos de todos los sensores a máxima precisión todo el tiempo — eso desperdiciaría demasiados recursos. Por ejemplo:
- Cuando estás trabajando tranquilamente en la oficina, el GPS no necesita actualizar tu posición cada segundo
- Pero cuando estás conduciendo con navegación, el GPS necesita actualizaciones de alta frecuencia
- Cuando estás durmiendo, el sensor de ritmo cardíaco puede reducir su frecuencia de muestreo
- Pero cuando se detecta un ritmo cardíaco anormal, la frecuencia de muestreo aumenta inmediatamente

El módulo Sensor **ajusta automáticamente la sensibilidad de cada sensor** basándose en el escenario y necesidades actuales.

**3. Extender — Los sensores futuros también pueden integrarse**

Los sensores de hoy son GPS y monitores de ritmo cardíaco; los de mañana podrían ser sensores de ondas cerebrales, sensores de calidad del aire o incluso sensores de reconocimiento de emociones. El diseño del módulo Sensor es abierto — cuando aparecen nuevos tipos de sensores, solo necesitas registrar un nuevo controlador a través del Hub de controladores, y el módulo Sensor puede gestionar su sensibilidad mientras el Montón de datos personales almacena sus datos.

## Relaciones con otros módulos

| Módulo relacionado | Relación | Analogía con el cuerpo humano |
|-------------------|----------|-------------------------------|
| **Hub de controladores** | Las interfaces reales de hardware del Sensor son gestionadas por el Hub de controladores | Terminaciones nerviosas → vías de conducción nerviosa |
| **Montón de datos personales** | Los datos recopilados por sensores se almacenan finalmente en el Montón de datos personales | Señales sensoriales → almacenamiento de memoria |
| **Rastreador en primera persona** | Ambos en el subsistema de Percepción, pero roles diferentes: el Rastreador ve la pantalla, el Sensor percibe el entorno físico | Ojos vs. nervios de todo el cuerpo |
| **Autoconciencia** | El Sensor proporciona datos ambientales; la Autoconciencia usa estos datos para inferir el estado del Human Prime | El sistema nervioso proporciona sensaciones → el cerebro interpreta emociones |
| **Protocolos CAP / DTP** | El Sensor implementa el puente de datos basándose en estos dos protocolos | Protocolo de transmisión para señales nerviosas |

## Historias de escenarios

### Escenario 1: Recordatorio inteligente de salud

A las 3 PM, has estado sentado frente a tu computadora durante tres horas. iFay descubre a través de los datos de sensores de tu smartwatch:

- **Acelerómetro**: Casi ningún movimiento significativo en las últimas 3 horas (indicando que has estado sentado todo el tiempo)
- **Sensor de ritmo cardíaco**: El ritmo cardíaco aumentó de 72 bpm normales a 85 bpm (posiblemente malestar leve por estar sentado prolongadamente)
- **Sensor de temperatura de piel**: Temperatura de muñeca ligeramente elevada

El módulo Sensor agrega estos datos y los pasa a la Capa de Cognición de iFay. Después de un análisis integral, iFay te recuerda gentilmente: "Has estado sentado 3 horas y tu ritmo cardíaco está un poco alto. ¿Qué tal si te levantas y estiras? El tiempo que me toma prepararte una taza de té es justo suficiente para una caminata rápida."

En este proceso, el módulo Sensor no "entendió" qué significaban los datos — solo los recopiló y transmitió fielmente. La comprensión y el juicio son trabajo de la Capa de Cognición. Pero sin los datos brutos proporcionados por el Sensor, la Capa de Cognición no tendría nada con qué trabajar.

### Escenario 2: Vuelo autónomo de dron

iFay está desplegado en un dron para una misión de fotografía aérea. El dron tiene múltiples sensores:

- **GPS**: Proporciona información de posición y altitud
- **IMU (Unidad de Medición Inercial)**: Proporciona aceleración y velocidad angular para control de actitud
- **Cámara**: Proporciona información visual (manejada por el Rastreador en primera persona)
- **Ultrasónico/LiDAR**: Proporciona información de distancia a obstáculos
- **Barómetro**: Proporciona datos precisos de altitud
- **Sensor de velocidad del viento**: Proporciona información de fuerza del viento actual

El módulo Sensor unifica todos estos flujos de datos. Durante el vuelo estable, la sensibilidad del IMU puede reducirse apropiadamente; pero cuando se detectan cambios repentinos en la velocidad del viento, el módulo Sensor aumenta inmediatamente la sensibilidad del IMU y el barómetro, permitiendo a iFay controlar más precisamente la actitud del dron y evitar la pérdida de control.

## Para desarrolladores

El módulo Sensor pertenece a la **Fase 2 (Toma de control directo del cliente)** como módulo central, dependiendo de los protocolos CAP y DTP.

- **ID de requisito**: Requisito 7 (Módulo Sensor)
- **Especificación de interfaz**: Interfaz `SensorModule` con cuatro métodos centrales: `registerSource()`, `adjustSensitivity()`, `getDataStream()` y `getActiveStatus()`
- **Protocolos relacionados**: CAP (Protocolo de Autoridad de Control) para tomar el control del hardware de sensores; DTP (Protocolo de Túnel de Datos) para transmisión bidireccional de datos
- **Módulos relacionados**: Hub de controladores (`DeviceDriverHub`) gestiona las interfaces reales de hardware; Montón de datos personales (`PersonalDataHeap`) almacena datos de sensores
- **Pruebas de conformidad**: iFACTS L1 verifica la capacidad de ajuste de sensibilidad; L2 verifica la integración de interfaz con Hub de controladores y Montón de datos personales
- **Puntos de diseño**: El módulo Sensor sirve solo como regulador de sensibilidad, no gestiona directamente interfaces de hardware; soporta ajuste dinámico de sensibilidad; nuevos tipos de sensores se integran a través del Hub de controladores


---

## 9.3 Autoconciencia

## Definición en una línea

La Autoconciencia es la **inteligencia emocional** de iFay — no mira la pantalla ni percibe el entorno. En cambio, **mira hacia adentro, hacia ti**, infiriendo tus sentimientos e intenciones a través de tus reacciones, como un viejo amigo que es excelente leyendo a las personas.

## Por qué es necesario

El subsistema de Percepción de iFay tiene tres módulos, cada uno mirando en una dirección diferente:
- **Rastreador en primera persona** mira hacia afuera — ve lo que hay en la pantalla
- **Sensor** percibe el entorno — siente temperatura, ubicación, movimiento
- **Autoconciencia** mira hacia adentro — te observa **a ti**

¿Por qué mirar hacia adentro?

Imagina dos tipos de asistentes. El primero hace lo que le dices, como una máquina expendedora — presionas un botón, dispensa una bebida. El segundo nota que hoy estás hablando más rápido de lo usual, tu ceño está ligeramente fruncido y solo comiste la mitad del almuerzo, así que proactivamente pospone tu reunión de la tarde media hora, te sirve una taza de agua caliente y pone tu música ligera favorita.

El primero es iFay sin Autoconciencia — un robot que sigue comandos.
El segundo es iFay con Autoconciencia — un compañero que **te entiende**.

La Autoconciencia eleva a iFay de "tú dices, yo hago" a "tú no dices, yo igual entiendo." Observa tus micro-expresiones, cambios en tus hábitos de operación y fluctuaciones emocionales, luego infiere lo que podrías necesitar — incluso antes de que tú mismo te des cuenta.

Esa es la diferencia entre una máquina expendedora y un amigo considerado.

## Su posición en la arquitectura

```
Arquitectura de cuatro capas de iFay
├── Capa Social
├── Capa de Interacción          ← La Autoconciencia está aquí
│   ├── Percepción (Sentido)
│   │   ├── Rastreador en primera persona   ← Mira hacia afuera, ve la pantalla
│   │   ├── Sensor                          ← Percibe el entorno
│   │   └── 👉 Autoconciencia              ← Mira hacia adentro, te lee
│   └── Acción
│       ├── Operación simulada
│       ├── Invocación de habilidades
│       └── Comportamiento autónomo  ← Las inferencias de Autoconciencia activan el comportamiento autónomo
├── Capa de Cognición
│   └── Pensamiento
│       └── Conciencia alineada ← La Autoconciencia ajusta la Conciencia alineada en tiempo real
└── Capa Ego
```

La Autoconciencia se encuentra en el **subsistema de Percepción de la Capa de Interacción**, el más "introvertido" de los tres módulos de percepción. No le importa qué se muestra en pantalla (ese es el trabajo del Rastreador en primera persona), ni cuál es la temperatura ambiente (ese es el trabajo del Sensor). Solo le importa una cosa: **¿Cómo estás ahora mismo? ¿Qué quieres?**

Lo que hace especial a la Autoconciencia es que su salida fluye en dos direcciones simultáneamente:
1. **Hacia abajo** al módulo de **Comportamiento autónomo** — activando las acciones proactivas de iFay
2. **Hacia adentro** al módulo de **Conciencia alineada** — actualizando la comprensión de iFay sobre ti en tiempo real

## Cómo funciona

La Autoconciencia funciona como un viejo amigo que te conoce desde hace años leyéndote:

**1. Observando tus reacciones**

La Autoconciencia monitorea continuamente varias señales durante tus interacciones con iFay:
- Cambios en tu velocidad de operación (repentinamente más rápido podría significar urgencia, más lento podría significar vacilación)
- Tu comportamiento de navegación (detenerte en un pasaje podría significar interés, desplazarte rápidamente podría significar desinterés)
- Tus expresiones y tono (si el dispositivo tiene cámara y micrófono)
- Tus patrones de aceptación o rechazo de las sugerencias de iFay
- Si tus hábitos diarios muestran anomalías

**2. Infiriendo tu intención**

Basándose en las señales observadas, la Autoconciencia infiere tu estado actual y posibles intenciones. Esto no son simples reglas "si A entonces B", sino inferencia inteligente combinando múltiples señales.

Por ejemplo: estás leyendo un artículo sobre aprendizaje automático, la velocidad de desplazamiento se reduce notablemente en cierta sección, y te desplazas hacia atrás dos veces — la Autoconciencia infiere que estás particularmente interesado en este párrafo y podrías querer profundizar más.

**3. Pasando resultados de inferencia**

Cuando la Autoconciencia infiere una nueva intención, hace dos cosas:

- **Le dice al módulo de Comportamiento autónomo**: "El Human Prime podría estar interesado en este tema — ¿deberíamos buscar proactivamente materiales relacionados?" El módulo de Comportamiento autónomo podría entonces buscar automáticamente artículos relacionados.
- **Le dice al módulo de Conciencia alineada**: "El Human Prime muestra interés en el campo del aprendizaje automático — actualizar el perfil del Human Prime." El módulo de Conciencia alineada entonces añade "interesado en aprendizaje automático" a tu perfil personal, haciendo que el comportamiento futuro de iFay esté más alineado contigo.

**4. Ajuste en tiempo real**

La Autoconciencia no es un juicio único — se ejecuta continuamente. Constantemente revisa sus inferencias basándose en tus últimas reacciones. Si infiere incorrectamente (ej., rechazas una sugerencia que proporcionó basándose en una inferencia), aprende y se ajusta.

## Relaciones con otros módulos

| Módulo relacionado | Relación | Analogía con el cuerpo humano |
|-------------------|----------|-------------------------------|
| **Comportamiento autónomo** | Las inferencias de Autoconciencia activan acciones proactivas | IE → cuidado proactivo ("Te ves cansado, déjame…") |
| **Conciencia alineada** | La Autoconciencia ajusta el perfil del Human Prime en la Conciencia alineada en tiempo real | La comprensión de ti se profundiza con el tiempo juntos |
| **Capa de Cognición** | Los resultados de inferencia se pasan a la Capa de Cognición para comprensión y toma de decisiones más profundas | Intuición → pensamiento racional |
| **Rastreador en primera persona** | El Rastreador mira hacia afuera, la Autoconciencia mira hacia adentro — complementarios | Los ojos ven el mundo vs. el corazón lee a las personas |
| **Sensor** | Los datos ambientales del Sensor pueden asistir las inferencias de Autoconciencia | Las sensaciones corporales asisten el juicio emocional (ej., ritmo cardíaco acelerado → posiblemente nervioso) |

## Historias de escenarios

### Escenario 1: Estás leyendo un artículo, iFay busca materiales proactivamente

Una tarde de fin de semana, estás navegando un artículo largo sobre "diseño de edificios sostenibles" en tu tablet. La Autoconciencia nota:

- Te desplazas rápidamente por la primera mitad (no muy interesado)
- Pero en la sección de "tecnología de ahorro energético de casas pasivas", tu velocidad de desplazamiento se reduce notablemente
- Te desplazas hacia atrás una vez para releer un gráfico
- Te detienes en esta sección durante casi dos minutos

La Autoconciencia infiere: estás particularmente interesado en el tema de "tecnología de ahorro energético de casas pasivas."

Pasa esta inferencia al módulo de Comportamiento autónomo. El módulo de Comportamiento autónomo busca proactivamente varios artículos en profundidad y un tutorial de video en YouTube, colocándolos silenciosamente en tu lista de lectura. Cuando terminas el artículo, iFay sugiere gentilmente: "Encontré algunos materiales en profundidad sobre casas pasivas. ¿Quieres echar un vistazo?"

Nunca dijiste "búscame materiales", pero iFay ya los tenía listos.

### Escenario 2: Un asistente considerado durante una videollamada

Estás en una videollamada. La Autoconciencia captura los cambios en tus micro-expresiones faciales a través de la cámara:

- Primeros 20 minutos: expresión relajada, asentimiento ocasional
- Cuando un colega comienza a discutir recortes de presupuesto del proyecto, tu ceño se frunce ligeramente y las comisuras de tu boca bajan un poco
- Tu postura corporal cambia de relajada a inclinada hacia adelante, dedos golpeando inconscientemente el escritorio

La Autoconciencia infiere: estás incómodo con el tema de discusión actual — posiblemente en desacuerdo con la propuesta de recorte de presupuesto, o el tema te está causando estrés.

Pasa esta inferencia al módulo de Comportamiento autónomo. El módulo de Comportamiento autónomo prepara silenciosamente dos cosas:
1. Un informe de análisis de presupuesto del proyecto que creaste previamente (en caso de que necesites datos para contra-argumentar)
2. Un borrador de mensaje de excusa cortés ("Disculpa, tengo una llamada urgente"), en caso de que quieras salir temporalmente

Todo esto se prepara silenciosamente sin molestarte. Solo cuando los necesites, iFay te los presentará.

## Para desarrolladores

El módulo de Autoconciencia pertenece a la **Fase 4 (iFay + coFay Personificación completa)** como módulo central — la clave para que iFay evolucione de "herramienta" a "compañero".

- **ID de requisito**: Requisito 13 (Autoconciencia)
- **Especificación de interfaz**: Interfaz `SelfAwareness` con tres métodos centrales: `inferIntent()` (inferir intención), `monitorHostReaction()` (monitorear reacciones del Human Prime) y `adjustAlignment()` (ajustar Conciencia alineada)
- **Módulos relacionados**: Comportamiento autónomo (`SelfDrivenBehavior`) recibe resultados de inferencia y activa acciones proactivas; Conciencia alineada (`AlignedConsciousness`) recibe resultados de inferencia y actualiza el perfil del Human Prime
- **Protocolos relacionados**: Sin dependencia directa de protocolo, pero puede aprovechar el módulo Sensor (vía CAP/DTP) para datos auxiliares (ej., ritmo cardíaco, expresiones faciales)
- **Pruebas de conformidad**: iFACTS L1 verifica la capacidad de inferencia de intención; L2 verifica interfaces con Comportamiento autónomo y Conciencia alineada; L4 verifica precisión de inferencia y protección de privacidad
- **Puntos de diseño**: Los resultados de inferencia deben pasarse tanto al módulo de Comportamiento autónomo como a la Capa de Cognición simultáneamente; soporta ajuste de Conciencia alineada en tiempo real; debe aprender y corregir de la retroalimentación del Human Prime cuando las inferencias son incorrectas
