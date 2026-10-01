# 📋 Backlog inicial

Este documento es la **fuente** del backlog. Cada historia se convierte en un *issue* de GitHub dentro del Project.
Formato de historia: *Como [usuario], quiero [acción] para [beneficio]*, con criterios de aceptación (CA).

**Tallas:** XS (menos de 1 h) · S (2–3 h) · M (medio día) · L (1–2 días) · XL (hay que dividirla)
**Prioridad:** P0 (MVP) · P1 (justo después del MVP) · P2 (más adelante)

---

## Sprint 0 · Descubrimiento

Los *spikes* son tareas de investigación con un tiempo máximo fijado. Su resultado es un documento, no código.

| ID | Spike | Entregable | Talla |
|---|---|---|---|
| S0-1 | Datos de vivienda joven en España: esfuerzo salarial, emancipación y precios | `docs/research/vivienda.md` con fuentes | M |
| S0-2 | Tipología de estafas de alquiler (Policía, INCIBE, OCU) | `docs/research/estafas.md` con las señales de alerta | M |
| S0-3 | Mapa de APIs y datos: Idealista API, Catastro, índices de precios del alquiler, INE, ayudas | `docs/research/apis.md` con acceso, límites y licencia | M |
| S0-4 | Proveedor de identidad: Keycloak, Supabase Auth o Spring Authorization Server | ADR-0002 | M |
| S0-5 | Benchmark de competidores (portales, apps de finanzas) | Tabla comparativa | S |
| S0-6 | Personas de usuario y propuesta de valor | `docs/personas.md` | S |
| S0-7 | Definir el MVP y cerrar el alcance | Actualizar este backlog | S |
| S0-8 | Crear el repo, GitHub Projects y las plantillas de issue | Captura del tablero 📸 | S |

---

## Épicas

### EPIC-0 · Plataforma y DevOps · P0
- **US-0.1** Como desarrolladora, quiero un monorepo con backend Spring Boot y app KMP para trabajar en un único sitio.
  - CA: compila en local · `README` con instrucciones de arranque
- **US-0.2** Como desarrolladora, quiero Docker Compose (API, Postgres con pgvector e IdP) para levantar el entorno con un solo comando.
- **US-0.3** Como desarrolladora, quiero un pipeline de CI (build, tests, lint, escaneo de dependencias y de secretos) para no fusionar código roto ni inseguro.
- **US-0.4** Como desarrolladora, quiero un `CLAUDE.md` y skills propias para que el asistente siga mis convenciones.

### EPIC-1 · Cuenta y seguridad · P0
- **US-1.1** Como usuaria, quiero entrar con Google para no tener que crear otra contraseña.
  - CA: flujo OIDC con PKCE en móvil y web · el backend valida los JWT como *resource server*
- **US-1.2** Como usuaria, quiero borrar mi cuenta y todos mis datos (derecho al olvido del RGPD).
- **US-1.3** Como desarrolladora, quiero un modelo de amenazas STRIDE del sistema para priorizar los controles.
- **US-1.4** Como sistema, quiero *rate limiting* y cabeceras de seguridad para mitigar abusos.

### EPIC-2 · Mi dinero · P0
- **US-2.1** Como usuaria, quiero registrar mis ingresos netos mensuales para calcular qué alquiler me puedo permitir.
- **US-2.2** Como usuaria, quiero registrar gastos fijos por categoría para ver cuánto me queda libre.
- **US-2.3** Como usuaria, quiero ver el **% de esfuerzo** de un alquiler respecto a mi sueldo, con un semáforo, para decidir con datos.
  - CA: verde por debajo del 30 % · ámbar entre el 30 % y el 40 % · rojo por encima del 40 % (umbrales configurables)
- **US-2.4** Como usuaria, quiero un objetivo de ahorro (fianza, mudanza, muebles) con su progreso.

### EPIC-3 · Detector de estafas · P0
- **US-3.1** Como usuaria, quiero pegar el texto de un anuncio y recibir una puntuación de riesgo con los motivos.
  - CA: respuesta JSON validada contra un esquema · motivos explicados · nunca se presenta como un veredicto absoluto
- **US-3.2** Como sistema, quiero reglas deterministas (precio anómalo, pago por adelantado, contacto solo por WhatsApp) que complementen a la IA.
- **US-3.3** Como desarrolladora, quiero proteger el prompt frente a inyecciones dentro del anuncio (OWASP LLM01).
- **US-3.4** Como desarrolladora, quiero un conjunto de anuncios de prueba (reales y fraudulentos) para medir precisión y *recall*.

### EPIC-4 · Revisor de contratos · P1
- **US-4.1** Como usuaria, quiero subir el PDF del contrato y ver las cláusulas dudosas, con la referencia al artículo de la LAU.
- **US-4.2** Como sistema, quiero indexar la LAU en pgvector (RAG) para fundamentar las respuestas.
- **US-4.3** Como usuaria, quiero que el contrato no se guarde salvo que yo lo pida (privacidad).

### EPIC-5 · Explicador de nómina · P1
- **US-5.1** Como usuaria, quiero subir mi nómina y que me explique cada concepto.
- **US-5.2** Como sistema, quiero anonimizar datos personales (DNI, número de Seguridad Social, IBAN) antes de enviarlos al modelo.

### EPIC-6 · Ayudas · P2
- **US-6.1** Como usuaria, quiero saber a qué ayudas al alquiler podría optar según mi edad, ingresos y comunidad autónoma.

---

## 🎯 MVP (propuesta, se confirma en S0-7)
EPIC-0 + EPIC-1 + EPIC-2 + EPIC-3: **dinero y detector de estafas, con autenticación seria**.
