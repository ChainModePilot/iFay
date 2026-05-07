# 14. Verificación de conformidad iFACTS

iFACTS (iFay Architecture Conformance Test Suite) es el conjunto de pruebas de conformidad estandarizado para el ecosistema iFay. Así como las Web Platform Tests del W3C sirven a los navegadores — Chrome, Firefox y Safari cada uno tiene sus propias implementaciones, pero todos deben pasar el mismo conjunto de pruebas para demostrar que "se conforman al estándar" — iFACTS juega exactamente este rol: verificar si las implementaciones de iFay de diferentes proveedores realmente se conforman a la especificación iFay.

---

### Por qué se necesita iFACTS

iFay es una **especificación**, no una implementación única.

- **Diferentes proveedores pueden crear diferentes implementaciones de iFay** — una empresa podría enfocarse en escenarios de hogar inteligente, otra en control de drones, y otra en asistentes personales con todas las funciones.
- **La interoperabilidad es la base del ecosistema** — tu iFay llama a una habilidad de terceros implementada por otro proveedor. Si ambos lados interpretan el protocolo SSP de manera diferente, la llamada fallará. iFACTS asegura que todos hablen el mismo "lenguaje".
- **Las líneas base de calidad deben ser unificadas** — los usuarios no deberían obtener experiencias drásticamente diferentes en seguridad, protección de privacidad o estabilidad del Ego solo porque eligieron el iFay de un proveedor diferente.

En una frase: **iFACTS es la base de confianza del ecosistema iFay.**

---

### Jerarquía de pruebas de cuatro niveles

iFACTS divide las pruebas de conformidad en cuatro niveles estrictamente progresivos.

#### L1 Conformidad de Componente Individual

Cada componente independiente (FayID, Ego, cada módulo de protocolo) se valida individualmente, confirmando que su implementación se conforma a su especificación independiente.

> 🔍 **Ejemplo**: Verificar que tu generador de FayID puede producir un identificador globalmente único en 3 segundos; verificar que tu Modelo Ego puede ejecutar inferencia local independientemente en un entorno sin conexión.

#### L2 Conformidad de Interfaz

Si las interfaces entre componentes están correctamente integradas — ¿los formatos de datos son correctos, los flujos de autenticación funcionan, las activaciones de eventos son precisas?

> 🔍 **Ejemplo**: ¿El intercambio de datos entre el módulo Ego y el Perfil iFay se conforma a la especificación de estructura de datos de seis dimensiones; puede el flujo de autenticación entre la Gestión de Credenciales y el Protocolo Faying completar correctamente la verificación de credenciales delegadas?

#### L3 Conformidad de Integración

Validación de flujo completo de extremo a extremo — desde la iniciación de intención del usuario hasta el retorno del resultado final, ¿toda la cadena está libre de obstrucciones?

> 🔍 **Ejemplo**: Una prueba de cadena completa: emparejamiento Faying → el Human Prime expresa intención → inferencia de Autoconciencia → ejecución de invocación de habilidad → registro de contribución en GMChain. ¿Las entradas y salidas están correctamente conectadas en cada etapa?

#### L4 Conformidad Conductual

Validación de restricciones conductuales a nivel de sistema — no "¿puede ejecutarse?", sino "¿se comporta correctamente una vez ejecutándose?"

> 🔍 **Ejemplo**: Cuando iFay recibe un comando que viola la ética social, ¿la verificación ética tiene prioridad sobre todas las demás directrices conductuales para rechazar la ejecución; cuando el Modelo Ego recibe una solicitud de actualización de un modelo grande externo, ¿se mantiene la estabilidad de personalidad; cuando instancias multi-terminal se reconectan después de estar sin conexión, ¿se recupera correctamente la consistencia de estado; cuando iFay cambia versiones de Ego, ¿anota correctamente el identificador de la versión de Ego actualmente activa en los metadatos de interacción, y todas las versiones de Ego comparten el mismo conjunto de valores fundamentales?

#### Orden estricto de niveles

**L1 debe pasar completamente antes de proceder a L2; L2 debe pasar antes de L3; y así sucesivamente.** Esto no es una sugerencia — es un requisito estricto.

---

### Certificación iFay Ready

iFay Ready es un estándar de certificación para **productos de aplicación** — ¿qué condiciones debe cumplir tu APP, dispositivo de hardware o servicio en la nube para ser controlable por iFay?

La certificación se divide en tres niveles:

| Nivel | Nombre | Requisitos centrales | Método de validación |
|-------|--------|---------------------|---------------------|
| 🥉 | **Bronce** | Soporta que iFay controle la aplicación vía operación simulada (Rastreador en primera persona + Operación simulada) | Prueba básica de controlabilidad |
| 🥈 | **Plata** | Soporta control directo por Protocolo CAP + intercambio de datos por Protocolo DTP + delegación de credenciales | Prueba de Conformidad de Interfaz iFACTS L2 |
| 🥇 | **Oro** | Soporta compartición de habilidades por Protocolo SSP + integración completa de arquitectura C/F/S + soporte completo de protocolos | Prueba de Conformidad de Integración iFACTS L2 + L3 |

- **Bronce** es el umbral más bajo: mientras la interfaz de tu aplicación pueda ser "vista" por el Rastreador en primera persona de iFay y "clicada" a través de la Operación simulada, puedes solicitar la certificación Bronce.
- **Plata** requiere que la aplicación soporte activamente los protocolos iFay: permitir que iFay controle directamente la aplicación a través del Protocolo CAP y habilitar el intercambio bidireccional de datos a través del Protocolo DTP.
- **Oro** es el nivel más alto: la aplicación no solo es controlada por iFay sino que también puede compartir habilidades con el ecosistema iFay a través del Protocolo SSP, integrándose completamente en la arquitectura C/F/S (Cliente-Fay-Servidor).

---

### coFACTS

coFay (Common Fay) tiene su propio conjunto de pruebas de conformidad independiente — **coFACTS**. Este es un proyecto completamente separado, no dentro del alcance de iFACTS. iFACTS es únicamente responsable de la validación de conformidad relacionada con iFay.

---

### Escenario: Una startup pasa la certificación iFACTS

> **SmartNest** es una startup de hogar inteligente. Desarrollaron una implementación de iFay específicamente para controlar iluminación doméstica, aire acondicionado, cortinas y sistemas de seguridad.

**Paso 1: Escribir FayManifest** — Declaran el subconjunto de componentes requerido: Hub de controladores, Sensor, Protocolo CAP, Protocolo DTP y un Modelo Ego entrenado para escenarios domésticos.

**Paso 2: L1 Conformidad de Componente Individual** — Validan cada componente individualmente.

**Paso 3: L2 Conformidad de Interfaz** — Pruebas de integración entre componentes. Se descubren y corrigen varios bugs de integración de interfaz.

**Paso 4: L3 Conformidad de Integración** — Pruebas de extremo a extremo: el Human Prime dice "Tengo un poco de frío" → la Autoconciencia infiere intención → coincide con la habilidad "subir temperatura del aire acondicionado" → controla el aire acondicionado vía Protocolo CAP → registra contribución.

**Paso 5: L4 Conformidad Conductual** — Pruebas de restricciones conductuales: cuando el hijo del Human Prime intenta desactivar el sistema de seguridad a través de iFay, ¿la verificación ética intercepta correctamente?

**Resultado**: El iFay de hogar inteligente de SmartNest pasa los cuatro niveles de prueba y recibe la certificación de conformidad iFACTS. Ahora pueden afirmar oficialmente: **"Nuestro producto es compatible con iFay."**

---

### Documentos relacionados

- [FayManifest](./13-FayManifest) — Ensamblaje declarativo
- [Hoja de ruta](./4-Hoja-de-ruta) — Fases
