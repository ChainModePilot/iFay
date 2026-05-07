# 2. Directrices SEP

## Qué es un SEP

Un SEP (Specification Enhancement Proposal) es el proceso formal de propuesta para cambios en la especificación iFay. Cualquier modificación sustancial de la especificación iFay — ya sea agregar un nuevo módulo, modificar el comportamiento de un protocolo o ajustar el modelo de datos de iFay Profile — debe pasar por el proceso SEP.

## Por qué se necesitan los SEPs

iFay es un ecosistema de estándares abiertos con implementaciones de múltiples proveedores, y cada cambio en la especificación puede afectar potencialmente a todos los implementadores. El proceso SEP garantiza que la evolución de la especificación sea ordenada, transparente y rastreable, dando a todas las partes interesadas la oportunidad de participar en la discusión y revisión.

## Ciclo de vida del SEP

Un SEP pasa por las siguientes etapas desde la propuesta hasta la implementación final:

### 1. Draft (Borrador)

El proponente crea un Issue de SEP en GitHub utilizando la plantilla estándar, describiendo la motivación, la solución propuesta y el impacto. Un SEP en la etapa de Draft puede estar incompleto, pero debe contener suficiente información para que la comunidad comprenda la intención de la propuesta.

### 2. Discussion (Discusión)

El SEP entra en un período de discusión pública que dura al menos **14 días**. Durante este período:

- Los miembros de la comunidad y los grupos de trabajo relevantes discuten la propuesta
- El proponente revisa y perfecciona la propuesta basándose en los comentarios recibidos
- Los mantenedores de los subproyectos relacionados evalúan el impacto de la propuesta en sus respectivos dominios

### 3. Review (Revisión)

Después de que finaliza el período de discusión, los Core Maintainers realizan una revisión formal del SEP. Durante la revisión, se puede solicitar al proponente que realice revisiones o adiciones adicionales, como:

- Agregar un análisis de compatibilidad con versiones anteriores
- Completar una evaluación del impacto en las pruebas de iFACTS
- Proporcionar un análisis comparativo de enfoques alternativos

### 4. Accepted / Rejected (Aceptado / Rechazado)

Los Core Maintainers deciden el resultado final del SEP mediante votación:

- **Accepted (Aceptado)**: El SEP es aprobado y pasa a la etapa de implementación
- **Rejected (Rechazado)**: El SEP es rechazado, con las razones documentadas. El proponente puede revisar y volver a enviar basándose en los comentarios recibidos

### 5. Implemented (Implementado)

Un SEP aceptado entra en la etapa de implementación. El trabajo de implementación puede ser realizado por el proponente u otros colaboradores. Durante la implementación:

- Se deben actualizar los documentos de especificación relacionados
- Se debe implementar el código de referencia (si corresponde)
- Se deben escribir o actualizar los casos de prueba de iFACTS

### 6. Final

Después de que la implementación se completa y pasa la revisión, el SEP entra en su estado final. En este punto:

- Los documentos de especificación han sido actualizados
- El conjunto de pruebas de iFACTS ha sido actualizado en consecuencia
- La documentación y guías relacionadas han sido actualizadas

## Plantilla de SEP

Al enviar un SEP, incluya lo siguiente:

- **Título**: Una descripción concisa de la propuesta
- **Motivación**: ¿Por qué se necesita este cambio? ¿Qué problema resuelve?
- **Diseño detallado**: Detalles técnicos y plan de implementación de la propuesta
- **Compatibilidad con versiones anteriores**: Análisis del impacto en las especificaciones e implementaciones existentes
- **Impacto en iFACTS**: Qué pruebas de conformidad necesitan ser agregadas o modificadas
- **Alternativas**: Otros enfoques considerados y sus ventajas y desventajas comparativas

## Quién puede enviar un SEP

Cualquier persona puede enviar un SEP. Ya sea que usted sea Core Maintainer, mantenedor, colaborador o usuario del ecosistema iFay, si considera que la especificación necesita mejoras, le invitamos a enviar una propuesta.

## Notas especiales

Los SEPs que involucran cambios de protocolo requieren atención especial: dado que cada protocolo de iFay (Faying, Telepathy, ICP, CAP, DTP, SSP) corresponde a un subproyecto independiente, los mantenedores de los protocolos relevantes deben participar en la revisión. Por ejemplo, un SEP que modifica el comportamiento del Control Authority Protocol (CAP) requiere que los mantenedores del grupo de trabajo WG-Protocols evalúen su impacto en módulos relacionados como el Device Driver Hub y el entorno de ejecución FayGer.
