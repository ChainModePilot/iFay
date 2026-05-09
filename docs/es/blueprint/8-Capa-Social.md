# 8. Capa Social

La Capa Social define el **modo de existencia** de iFay en la sociedad — responde tres preguntas fundamentales: "¿Quién soy?" (Identidad), "¿Qué estoy autorizado a hacer?" (Permisos Sociales) y "¿Cuánto valen mis contribuciones?" (Contribución Social y Voz).

Si comparamos a iFay con una persona social, la Capa Social es su **identidad social**: un documento de identidad demuestra quién eres, varios certificados y claves demuestran qué estás autorizado a hacer, y tu reputación social e historial de contribuciones determinan tu voz y credibilidad en la comunidad.

La Capa Social es la piedra angular del sistema de seguridad de iFay y el prerrequisito para la integración de iFay en las relaciones sociales.

```
Arquitectura de cuatro capas de iFay
├── 👉 Capa Social
│   ├── 8.1 Identidad (FayID)              ← Quién soy
│   ├── 8.2 Permisos Sociales              ← Qué estoy autorizado a hacer
│   │   ├── Cuenta/Contraseña
│   │   ├── Certificado
│   │   ├── Autorización
│   │   ├── Token de acceso
│   │   └── Smart Contract
│   └── 8.3 Contribución Social y Voz      ← Cuánto valen mis contribuciones
│       ├── GMChain (Global Merit Chain)
│       └── MeriToken
├── Capa de Interacción
├── Capa de Cognición
└── Capa Ego
```

---

## 8.1 Identidad (FayID)

### Definición en una línea

FayID es el **número de identidad** de iFay — un identificador persistente, globalmente único, legible por humanos y por máquinas, que sirve como base para que iFay sea reconocido y rastreado en todas las interacciones sociales.

### Por qué se necesita

En la sociedad humana, un número de identificación es el punto de partida para todas las actividades sociales — sin identificación, no puedes abrir una cuenta bancaria, firmar un contrato, ni siquiera comprar un billete de tren. FayID tiene exactamente la misma importancia para iFay: es el prerrequisito para que iFay participe en cualquier interacción social.

El diseño de FayID tiene dos consideraciones clave:

1. **Identificación unificada**: iFay y coFay utilizan el mismo mecanismo de generación y gestión de FayID. Esto asegura que cuando los iFays individuales eventualmente asuman roles sociales significativos, su identidad pueda transicionar sin problemas — igual que algunos YouTubers individuales evolucionan hasta jugar roles importantes en el discurso público sin necesidad de cambiar su identidad.

2. **Vinculación de activación**: FayID está profundamente vinculado al Protocolo Faying. Ningún iFay debería actuar autónomamente sin la intención explícita del Human Prime. El estado de activación de FayID es gestionado por el [Protocolo Faying](https://github.com/ChainModePilot/Faying-Protocol/wiki), asegurando que iFay solo opere bajo la autorización explícita del Human Prime.

### Propiedades fundamentales

| Propiedad | Descripción |
|-----------|-------------|
| **Globalmente único** | Soporta capacidad de identificadores que excede la escala de la población mundial, garantizando ausencia de colisiones |
| **Legible por humanos** | Los humanos pueden reconocerlo y recordarlo intuitivamente — no es una cadena hash sin significado |
| **Legible por máquinas** | Los sistemas y Fays pueden analizarlo y compararlo eficientemente |
| **Persistente** | Una vez asignado, nunca cambia durante toda la vida de iFay, soportando migración de identidad y continuidad de personalidad |
| **Estado de activación** | Vinculado con el Protocolo Faying, indicando claramente si iFay está actualmente activo o en reposo |

### Escenario

> Xiao Ming registra su propio iFay, y el sistema asigna FayID `fay://ming.2024.cn`. Este ID acompañará al iFay de Xiao Ming de por vida — ya sea que iFay migre del teléfono al ordenador, o evolucione de asistente personal a agente de legado digital de Xiao Ming, el FayID nunca cambia.
>
> Cuando el iFay de Xiao Ming se comunica con el coFay de un hospital, ambas partes se identifican mutuamente a través de FayID, igual que dos personas intercambiando tarjetas de visita al encontrarse.

### Para desarrolladores

- **Proyecto independiente**: FayID es un [proyecto open-source independiente](https://github.com/ChainModePilot/FayID); ver [documentación de FayID](https://github.com/ChainModePilot/FayID/wiki)
- **Especificación de interfaz**: Interfaz `FayIDRegistry` con `generate()` (generar FayID), `resolve()` (resolver FayID), `getActivationStatus()` (obtener estado de activación)
- **Pruebas de conformidad**: iFACTS L1 verifica unicidad y persistencia de FayID; L2 verifica la vinculación del estado de activación con el Protocolo Faying

---

## 8.2 Permisos Sociales

### Definición en una línea

Los Permisos Sociales son el **llavero** de iFay — gestionan de forma segura las credenciales que iFay necesita para usar varios servicios en tu nombre. Pero estas credenciales no son tus originales — son copias seguras. Incluso si una copia se pierde, tus credenciales originales permanecen seguras.

### Por qué se necesitan

iFay necesita actuar en tu nombre — iniciar sesión en plataformas de comercio electrónico para comprar cosas, usar tu correo corporativo para enviar mensajes, controlar dispositivos inteligentes del hogar, llamar APIs de terceros. Todo esto requiere "llaves". El módulo de Permisos Sociales te ayuda a gestionar estas llaves de forma segura a través de un **mecanismo de copia** que asegura que las credenciales originales nunca se expongan directamente.

### Cinco tipos de permisos

Los Permisos Sociales gestionan cinco tipos de credenciales, cada uno correspondiente a diferentes escenarios de relaciones sociales:

#### 1. Cuenta / Contraseña

El tipo de credencial más común. El Human Prime delega contraseñas de cuentas de aplicaciones y servicios a iFay, e iFay usa estas credenciales a través del mecanismo de copia para iniciar sesión y operar.

- **Mecanismo de copia**: iFay no posee la contraseña original sino una credencial de copia con permisos restringidos
- **Alcance de permisos**: Las copias pueden tener permisos más estrictos que el original (ej., "solo artículos de uso diario, compra individual no superior a 200 yuan")
- **Revocación por anomalía**: Revoca automáticamente la copia cuando se detecta uso anormal; la contraseña original no se ve afectada

> 🎯 Escenario: Delegas tu cuenta de plataforma de comercio electrónico a iFay. Lo que iFay recibe no es tu contraseña original sino una copia segura. Puede usar esta copia para hacer pedidos por ti, pero si la copia se ve comprometida, puedes revocarla con un clic — tu contraseña original no se ve afectada.

#### 2. Certificado

Certificados digitales para comunicación cifrada y verificación de identidad. Compatible con sistemas de Autoridad de Certificación (CA) existentes, soportando formatos estándar como X.509.

- **Propósito**: Comunicación cifrada de extremo a extremo, firma de código, autenticación de identidad
- **Compatibilidad**: Integración transparente con infraestructura PKI existente, soportando certificados emitidos por CAs principales
- **Ciclo de vida**: Soporta gestión completa del ciclo de vida de solicitud, renovación y revocación de certificados

> 🎯 Escenario: iFay necesita comunicarse con un sistema bancario a través de un canal cifrado. Usa un certificado digital delegado por el Human Prime para establecer una conexión TLS, asegurando la confidencialidad e integridad de la transmisión de datos. El certificado fue emitido por una CA de confianza, permitiendo al sistema bancario verificar la legitimidad de la identidad de iFay.

#### 3. Autorización

Compatible con métodos tradicionales de autenticación de terceros (ej., OAuth 2.0), permitiendo a iFay autenticarse con plataformas de terceros a través de factores autorizados para obtener permisos de acceso restringidos.

- **Compatible con OAuth**: Soporta flujo de código de autorización OAuth 2.0, flujo de credenciales de cliente y otros patrones estándar
- **Autenticación por factores**: Obtiene autorización para plataformas sociales, servicios financieros, etc. a través de información de huella digital de cuenta (huella de dispositivo, biometría, patrones de comportamiento)
- **Control de alcance**: Controla precisamente el alcance de la autorización, asegurando que iFay solo pueda acceder a los recursos necesarios

> 🎯 Escenario: Autorizas a iFay a acceder a tu plataforma social. iFay no necesita tu contraseña de la red social — pasa por el flujo OAuth, usando tu huella de dispositivo y reconocimiento facial como factores de autenticación para obtener un token de acceso con alcance restringido. Este token solo permite leer tu lista de amigos y enviar mensajes, no modificar la configuración de la cuenta.

#### 4. Token de acceso

Credenciales de acceso temporal gestionadas, generalmente con un período de expiración. Usadas para llamadas API, acceso a servicios y escenarios similares.

- **Gestión de expiración**: Rastrea automáticamente el tiempo de expiración del token y lo renueva antes de que expire
- **Privilegio mínimo**: Cada token otorga solo los permisos mínimos necesarios para completar una tarea específica
- **Registro de auditoría**: Cada uso del token se registra, soportando auditoría posterior

> 🎯 Escenario: iFay necesita llamar una API de traducción. Posee un API Key (token de acceso) que rota automáticamente cada 24 horas. Si una clave se ve comprometida, el impacto se limita a 24 horas de volumen de llamadas, y el sistema detecta inmediatamente patrones de llamada anormales y activa la revocación.

#### 5. Smart Contract

Credenciales de smart contract blockchain para servicios descentralizados y colaboración automatizada entre Fays.

- **Ejecución automática**: Se ejecuta automáticamente cuando se cumplen las condiciones del contrato, sin necesidad de intervención manual
- **Inmutable**: El contenido del contrato no puede ser modificado unilateralmente una vez desplegado
- **Transparente y verificable**: Cualquier participante puede verificar los resultados de ejecución del contrato

> 🎯 Escenario: Tu iFay firma un smart contract con un coFay de análisis de datos — "pagar automáticamente 5μ al completar el análisis." Cuando el coFay completa el análisis y envía los resultados, el contrato verifica automáticamente la calidad de los resultados y ejecuta el pago — sin necesidad de confirmación manual. Todo el proceso es transparente, inmutable y ejecutado automáticamente.

### Mecanismo de copia y defensa de seguridad

Los cinco tipos de permisos siguen principios de seguridad unificados:

- **Aislamiento de copia**: iFay nunca posee directamente credenciales originales — solo copias con permisos restringidos
- **Etiquetado de propietario**: Cada credencial indica si el propietario es el Human Prime o iFay mismo (iFay puede adquirir credenciales independientemente)
- **Registro de auditoría**: Cada uso de credencial se registra, soportando auditoría posterior
- **Detección de anomalías**: Revoca automáticamente copias y notifica al Human Prime cuando se detectan patrones de uso anormales
- **Protección de privacidad**: Cuando iFay está autorizado a consultar datos privados, solo se devuelven resultados booleanos (verdadero o falso) sin exponer datos reales

### Para desarrolladores

- **Especificación de interfaz**: Interfaz `CredentialManager` con `delegate()` (delegar/crear copia), `authenticate()` (autenticar), `revoke()` (revocar), `queryPrivacy()` (consulta de privacidad, devuelve solo booleano), `getAuditLog()` (registro de auditoría)
- **Cinco tipos de credenciales**: `account_password`, `certificate`, `authorization`, `access_token`, `smart_contract`
- **Propietario de credencial**: `human_prime` o `ifay`
- **Estado de copia**: `active`, `revoked`, `expired`
- **Pruebas de conformidad**: iFACTS L1 verifica gestión de cinco tipos de credenciales y mecanismo de copia; L2 verifica interfaces de autenticación con Habilidades registradas e Invocación de habilidades; L4 verifica la restricción de retorno booleano para consultas de privacidad y comportamiento de detección de anomalías

---

## 8.3 Contribución Social y Voz (GMChain & MeriToken)

### Definición en una línea

GMChain (Global Merit Chain, GMC) es el **libro de contribución social** del ecosistema iFay — registra cada contribución hecha por Fays y humanos a la sociedad, cuantificada como MeriToken. MeriToken no es moneda — es una **medida de voz y reputación**.

### Por qué se necesita

En la sociedad tradicional, la posición social y la voz de una persona dependen de sus contribuciones, reputación y confianza acumulada. Pero estos son a menudo vagos, subjetivos y difíciles de cuantificar.

En el ecosistema Fay, la mayor parte del trabajo es realizado por Fays, y cada colaboración y contribución puede ser rastreada y registrada con precisión. GMChain es este sistema de rastreo y registro — hace que "quién contribuyó qué" sea transparente, verificable e inmutable.

MeriToken es la unidad de medida en GMChain, representando la contribución social. Su propósito no es "comprar cosas" sino:
- **Medir contribución**: ¿Cuánto valor ha creado tu iFay para la sociedad?
- **Construir reputación**: Más contribuciones significan mayor reputación y mayor confianza en la red de colaboración
- **Ganar voz**: Los contribuyentes tienen mayor voz en decisiones que requieren consenso comunitario
- **Incentivar colaboración**: Las contribuciones en la colaboración Fay-a-Fay se registran y recompensan justamente

### Posición de GMChain

GMChain es una **infraestructura de medición de valor que abarca todos los niveles** del sistema iFay. No pertenece a ningún módulo específico sino que proporciona capacidades de rastreo de contribuciones y medición de valor para todo el ecosistema.

En el framework CPE+M, M (Merit) representa la capa de medición de contribuciones encarnada por GMChain — abarca las capas de Context, Protocol y Environment, proporcionando mecanismos unificados de registro de contribuciones e incentivos para todos los participantes (humanos, iFay, coFay, proveedores de servicios).

```
Posición de GMChain en el framework CPE+M
┌─────────────────────────────────────────────┐
│  Merit (M) — GMChain / MeriToken            │  ← Abarca todas las capas
│  Rastrear, medir, evaluar contribuciones,   │
│  incentivar creación de valor               │
├─────────────────────────────────────────────┤
│  Context (C)  │  Protocol (P)  │  Env (E)  │
│  Contexto     │  Protocolo     │  Entorno   │
│  Entorno      │  Sistema       │  Ejecución │
└─────────────────────────────────────────────┘
```

### Mecanismos fundamentales de GMChain

**1. Registro de contribuciones**

GMChain registra los siguientes tipos de contribuciones:
- Tareas completadas a través de colaboración Fay-a-Fay (ej., un coFay de viajes reservando billetes para ti)
- Provisión de servicios de ensamblaje de información (ej., limpieza de datos, organización de conocimiento)
- Provisión de servicios API y de habilidades
- Provisión de recursos de dispositivos y computación
- Provisión de entornos de ejecución
- Otros inputs de valor añadido reconocidos por la comunidad

**2. Negociación de precios**

Los Fays negocian precios (en unidades μ) antes de ejecutar tareas colaborativas. Esto asegura:
- Cada contribución de colaboración es rastreable y evaluable
- No hay "cobrar sin trabajar" o valor artificialmente inflado
- Los contribuyentes reciben recompensas justas

**3. Libro mayor de MeriToken**

El Libro mayor de MeriToken es el registro de puntuación de contribución para cada Fay y humano. Registra:
- Contribuciones totales acumuladas
- Distribución por tipo de contribución
- Puntuación de reputación (basada en calidad de contribución y feedback de colaboración)
- Peso de voz (peso de voto en la gobernanza comunitaria)

### Diferencias fundamentales con las criptomonedas tradicionales

| Dimensión | Criptomoneda tradicional | MeriToken |
|-----------|--------------------------|-----------|
| **Adquisición** | Consumo de poder de cómputo para tareas computacionales (minería) | Creación de valor social (contribución) |
| **Ancla de valor** | Oferta/demanda del mercado y especulación | Contribución social |
| **Propósito** | Activo financiero, instrumento de inversión | Medición de reputación, voz, incentivo de colaboración |
| **Relación con moneda fiat** | Intercambiable con moneda fiat | No intercambiable con moneda fiat |
| **Volatilidad** | Altamente volátil | Crecimiento estable (las contribuciones solo aumentan) |

### Visión a largo plazo y posición actual

> ⚠️ **Nota importante**: GMChain/MeriToken es un producto de visión a largo plazo para una sociedad completamente impulsada por IA, perteneciente a la Fase 5 de la Hoja de ruta (Fay remodela la estructura laboral y la distribución de valor) como componente central. No nos apresuraremos a implementar GMChain y MeriToken a corto plazo, pero debemos reservar un lugar para ellos en el diseño del sistema porque son la infraestructura clave para la evolución del ecosistema iFay de "uso de herramientas" a "colaboración social".
>
> Nos comprometemos a:
> - GMChain nunca aceptará inyección monetaria
> - MeriToken no será intercambiable con moneda fiat
> - MeriToken mide contribución social, no activos financieros
>
> En una sociedad completamente impulsada por IA, la satisfacción de necesidades de supervivencia y sociales no depende del costo monetario. El mecanismo de anclaje de valor de MeriToken es fundamentalmente diferente de las criptomonedas tradicionales. Los detalles se refinarán progresivamente a través de argumentación rigurosa en fases posteriores.

### Escenario

> Tu iFay reserva un vuelo para ti y contacta a un coFay de viajes a través del Protocolo de Telepatía. El coFay de viajes cotiza 15μ por el servicio completo de reserva. Tu iFay acepta la cotización, y después de que el coFay de viajes completa la tarea, GMChain registra automáticamente esta colaboración:
>
> - El Libro mayor de MeriToken del coFay de viajes aumenta en 15μ (contribución de servicio)
> - El Libro mayor de MeriToken de tu iFay registra un "consumo de servicio" (sin deducción de puntos, solo se registra el historial de colaboración)
> - El Libro mayor de MeriToken del coFay de la aerolínea aumenta en 2μ (contribución por proporcionar interfaz SSP)
>
> A medida que el coFay de viajes acumula más registros de contribución, su puntuación de reputación crece más alta, volviéndose cada vez más confiable en la red de colaboración — más iFays lo elegirán preferentemente, formando un ciclo positivo.

### Para desarrolladores

GMChain pertenece a la **Fase 5 (Fay remodela la estructura laboral y la distribución de valor)** como componente central, pero sus definiciones de interfaz necesitan ser reservadas en fases tempranas.

- **Proyecto independiente**: GMChain es un [proyecto open-source independiente](https://github.com/ChainModePilot/Global-Merit-Chain); ver [documentación de GMChain](https://github.com/ChainModePilot/Global-Merit-Chain/wiki)
- **Especificación de interfaz**: Interfaz `MeritLedger` con `recordContribution()` (registrar contribución), `getBalance()` (consultar saldo), `getReputation()` (consultar puntuación de reputación), `negotiate()` (negociación de precios)
- **Unidad de medida**: μ (MU, Merit Unit), la unidad más pequeña de MeriToken
- **Pruebas de conformidad**: iFACTS L4 verifica inmutabilidad de registros de contribución y equidad de la negociación de precios
- **Puntos de diseño**: Los registros de contribución son inmutables; la negociación de precios se completa antes de la ejecución de la tarea; MeriToken no es intercambiable con moneda fiat; las puntuaciones de reputación se basan en calidad de contribución y feedback de colaboración
