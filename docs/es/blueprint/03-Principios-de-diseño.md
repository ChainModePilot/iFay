<img width="100%" alt="iFay Title Banner" src="./illustration/ifay-title-banner.png"/>

# 3. Principios de diseño

iFay (Individual Fay) es un avatar digital de IA profundamente vinculado a una persona natural. No es una herramienta, sino una extensión de tu personalidad — fusionando tu carácter, recuerdos, preferencias y capacidades digitales, asumiendo tu trabajo mecánico, repetitivo y peligroso, y amplificando tu valor social. iFay adopta el framework CPE+M (Contexto, Protocolo, Entorno, Mérito), consistiendo en una arquitectura de cuatro capas — Capa Social, Capa de Interacción, Capa de Cognición y Capa Ego — cubriendo cinco fases evolutivas desde la simulación de operaciones humanas hasta la remodelación de la estructura laboral y la distribución de valor.

---

## Principios de diseño

El diseño de iFay sigue cinco principios fundamentales que permean toda la arquitectura e implementación del sistema:

| # | Principio | Resumen en una línea |
|---|-----------|---------------------|
| 1 | **Adopción progresiva amigable con el ecosistema** | Los socios del ecosistema no necesitan implementar un iFay completo para lanzar un producto — un iFay que solo controla drones solo necesita satisfacer el subconjunto requerido de componentes para salir al mercado. |
| 2 | **Ensamblaje mínimo declarativo** | Define los componentes, protocolos y configuraciones requeridos a través de un único archivo de declaración FayManifest, ensamblando iFay como escribir un package.json. |
| 3 | **Composición flexible** | Los componentes están débilmente acoplados y son combinables; implementaciones de diferentes proveedores pueden combinarse libremente siempre que cumplan con los contratos de interfaz. |
| 4 | **Personificado, no instrumentalizado** | iFay no es un Agent — cada iFay tiene una personalidad, memoria y preferencias únicas, una Instanciación (réplica) del Human Prime, capaz de continuar la personalidad del Prime incluso después de su fallecimiento. |
| 5 | **Intuición guiada por escenarios** | Cada módulo funcional puede explicarse con un escenario concreto de la vida, permitiendo a los lectores imaginar intuitivamente la vida con iFay. |

---

## Tabla de contenidos

1. [Definición y concepto](./02-Definición-y-concepto)

    Proporciona la definición y visión estructural de iFay, analiza las diferencias fundamentales entre iFay y el concepto actual de Agent, y los principios detrás de sus características operativas.

---

2. [Escenarios de aplicación iFay](./05-Escenarios-de-aplicación-iFay)

    El proceso completo de usar iFay desde cero: cómo inyectar tu personalidad, añadir habilidades a iFay, interactuar con iFay, cómo iFay socializa, y una vista panorámica de la seguridad y el ecosistema industrial.

    - [Inyectar rasgos del Prime en iFay](./05-Escenarios-de-aplicación-iFay#inyectar-rasgos-del-prime-en-ifay)
    - [Complementar iFay con capacidades externas](./05-Escenarios-de-aplicación-iFay#complementar-ifay-con-capacidades-externas)
    - [Métodos de interacción humano-iFay](./05-Escenarios-de-aplicación-iFay#métodos-de-interacción-humano-ifay)
        - [Cómo activar iFay](./05-Escenarios-de-aplicación-iFay#cómo-activar-ifay)
        - [Conciencia autónoma de iFay](./05-Escenarios-de-aplicación-iFay#conciencia-autónoma-de-ifay)
        - [Cómo apagar iFay](./05-Escenarios-de-aplicación-iFay#cómo-apagar-ifay)
    - [Funciones sociales de iFay](./05-Escenarios-de-aplicación-iFay#funciones-sociales-de-ifay)
    - [Seguridad](./05-Escenarios-de-aplicación-iFay#seguridad)
    - [Modelando el ecosistema de la industria IA](./05-Escenarios-de-aplicación-iFay#modelando-el-ecosistema-de-la-industria-ia)

---

3. [iFay es réplica de la personalidad humana](./06-iFay-es-réplica-de-la-personalidad-humana)

    iFay está vinculado a una persona natural específica, por lo que los rasgos del Human Prime necesitan ser inyectados en iFay desde tres dimensiones: la personalidad da forma al Modelo Ego, los datos pueblan el Montón de datos personales y los permisos establecen la delegación de credenciales.

    - [Personalidad del Prime](./06-iFay-es-réplica-de-la-personalidad-humana#personalidad-del-prime)
    - [Datos del Prime](./06-iFay-es-réplica-de-la-personalidad-humana#datos-del-prime)
    - [Permisos del Prime](./06-iFay-es-réplica-de-la-personalidad-humana#permisos-del-prime)

---

4. [Perfil iFay](./07-Perfil-iFay)

    El Perfil iFay es la "tarjeta de identidad" completa de iFay — una tabla de atributos de seis dimensiones semánticamente interpretable usada para que humanos identifiquen a iFay, sistemas identifiquen a iFay y Fays se identifiquen entre sí.

    - [Identidad iFay](./07-Perfil-iFay#identidad-ifay)
    - [Modelo Ego](./07-Perfil-iFay#modelo-ego)
    - [Faying Thinking](./07-Perfil-iFay#faying-thinking)
        1. [Contenido](./07-Perfil-iFay#contenido)
        2. [Datos](./07-Perfil-iFay#datos)
        3. [Base de conocimiento](./07-Perfil-iFay#base-de-conocimiento)
        4. [Info Feed](./07-Perfil-iFay#info-feed)
    - [Faying Skills](./07-Perfil-iFay#faying-skills)
        1. [API](./07-Perfil-iFay#api)
        2. [Workflow](./07-Perfil-iFay#workflow)
        3. [Bot](./07-Perfil-iFay#bot)
        4. [Agent](./07-Perfil-iFay#agent)
        5. [APP](./07-Perfil-iFay#app)
        6. [Microservicio](./07-Perfil-iFay#microservicio)
    - [Faying Hardware](./07-Perfil-iFay#faying-hardware)
        1. [Dispositivo](./07-Perfil-iFay#dispositivo)
        2. [Almacenamiento](./07-Perfil-iFay#almacenamiento)
        3. [Computación](./07-Perfil-iFay#computación)
    - [Faying Permissions](./07-Perfil-iFay#faying-permissions)
        1. [SSO](./07-Perfil-iFay#sso)
        2. [OAuth](./07-Perfil-iFay#oauth)
        3. [Fingerprint](./07-Perfil-iFay#fingerprint)

---

5. [Ensamblaje declarativo FayManifest](./13-FayManifest)

    FayManifest es el "package.json" de iFay — los desarrolladores solo necesitan listar los componentes, protocolos, modos de control y configuraciones de controladores requeridos en un único archivo de declaración JSON, y el entorno de ejecución FayGer resuelve automáticamente las dependencias y ensambla la instancia de iFay. Puedes construir un iFay dedicado desde cero en un fin de semana.

---

6. [Verificación de conformidad iFACTS](./14-iFACTS)

    iFACTS (iFay Architecture Conformance Test Suite) es un conjunto de pruebas de conformidad estandarizado que cubre puntos clave de la especificación incluyendo interacciones de protocolo, interfaces de módulos y comportamientos de seguridad. Las implementaciones de los proveedores deben pasar las pruebas iFACTS para afirmar "iFay Ready", con pruebas divididas en cuatro niveles: L1 Conformidad de Componente Individual, L2 Conformidad de Interfaz, L3 Conformidad de Integración, L4 Conformidad Conductual.

---

7. [Tutela y continuidad de personalidad](./15-Tutela-y-continuidad-de-personalidad)

    iFay es el recipiente digital de la personalidad. Cuando el Human Prime ya no puede gestionar iFay, un Tutor puede asumir los derechos de gestión mediante frases mnemónicas o autenticación de identidad preespecificada; después del fallecimiento del Human Prime, iFay puede continuar existiendo como una identidad independiente en un sandbox del Cementerio digital — la personalidad perdura.

---

8. Casos de estudio

    Proporcionaremos una serie de casos de estudio que demuestran cómo se crea iFay y cómo los sistemas se conectan con iFay.
