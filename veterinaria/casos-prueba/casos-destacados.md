# Veterinaria — Casos de Prueba Destacados

Este documento reúne una selección de los casos de prueba más representativos del proyecto **Veterinaria**.

La selección está orientada a mostrar las capacidades de diseño y ejecución de pruebas de QA, priorizando escenarios que demuestran:

- Validación de datos de entrada.
- Validación de campos obligatorios.
- Reglas de negocio.
- Validación de relaciones entre entidades.
- Manejo de datos inválidos.
- Flujos funcionales críticos.
- Casos negativos y escenarios de borde.

La suite original contempla pruebas para los módulos **Cliente, Mascota, Veterinario y Consulta**.

---

## Casos seleccionados

| ID | Caso de prueba | Módulo | Tipo de validación |
|---|---|---|---|
| **NRo-32** | Ingresar una Cédula no válida | Cliente | Validación de formato |
| **NRo-57** | Dar de alta un cliente con campos vacíos | Cliente | Campos obligatorios |
| **NRo-34** | Ingresar un Nro. de patente no válido | Mascota | Validación de formato |
| **NRo-36** | Ingresar una edad no válida | Mascota | Regla de negocio |
| **NRo-37** | Verificar que el ComboBox Cliente muestre los clientes correspondientes | Mascota | Integridad / relación entre entidades |
| **NRo-45** | Ingresar un código de veterinario inválido | Veterinario | Validación de formato |
| **NRo-49** | Registrar una consulta con un número de patente inexistente | Consulta | Integridad / validación de existencia |
| **NRo-50** | Ingresar una fecha de ingreso posterior a la fecha actual | Consulta | Regla de negocio temporal |

---

## Módulo Cliente

### NRo-32 — Cédula no válida

**Objetivo:** verificar que el sistema rechace una Cédula ingresada con un formato no válido.

**Qué demuestra:**

- Validación de datos críticos.
- Diseño de escenarios negativos.
- Control de entradas inválidas.

### NRo-57 — Campos vacíos

**Objetivo:** verificar que el sistema no permita dar de alta un cliente cuando existen campos obligatorios sin completar.

**Qué demuestra:**

- Validación de obligatoriedad.
- Manejo de datos incompletos.
- Prevención de registros inválidos.

---

## Módulo Mascota

### NRo-34 — Nro. de patente no válido

**Objetivo:** comprobar que el sistema valide correctamente el formato del número de patente.

**Qué demuestra:**

- Validación de formato.
- Pruebas negativas.
- Control de datos de identificación de la mascota.

### NRo-36 — Edad no válida

**Objetivo:** verificar el comportamiento del sistema ante el ingreso de una edad no válida.

**Qué demuestra:**

- Aplicación de reglas de negocio.
- Validación de límites o valores permitidos.
- Diseño de casos de borde.

### NRo-37 — Clientes correspondientes

**Objetivo:** comprobar que el ComboBox de Cliente muestre los clientes correspondientes al registrar una mascota.

**Qué demuestra:**

- Validación de relaciones entre entidades.
- Integridad de los datos.
- Verificación de información dependiente.

---

## Módulo Veterinario

### NRo-45 — Código de veterinario inválido

**Objetivo:** verificar que el sistema rechace valores inválidos en el campo Código del registro de veterinario.

**Qué demuestra:**

- Validación de formato específico.
- Pruebas de entradas inválidas.
- Verificación de reglas asociadas a campos estructurados.

---

## Módulo Consulta

### NRo-49 — Patente inexistente

**Objetivo:** verificar que no sea posible registrar una consulta utilizando un número de patente inexistente.

**Qué demuestra:**

- Validación de existencia de datos.
- Integridad referencial a nivel funcional.
- Validación de relaciones entre módulos.
- Prevención de registros inconsistentes.

### NRo-50 — Fecha posterior a la actual

**Objetivo:** comprobar que el sistema impida registrar una consulta con una fecha de ingreso posterior a la fecha actual.

**Qué demuestra:**

- Validación de reglas de negocio.
- Manejo de fechas.
- Pruebas de límites y escenarios inválidos.
- Validación temporal.

---

## ¿Por qué estos casos?

La selección busca evitar que los casos destacados sean únicamente pruebas del flujo feliz (*happy path*).

Los casos seleccionados representan diferentes dimensiones de testing:

| Dimensión | Casos |
|---|---|
| Datos inválidos | NRo-32, NRo-34, NRo-45 |
| Campos obligatorios | NRo-57 |
| Reglas de negocio | NRo-36, NRo-50 |
| Relaciones entre entidades | NRo-37, NRo-49 |
| Escenarios negativos | NRo-32, NRo-34, NRo-36, NRo-45, NRo-49, NRo-50 |

Esto permite mostrar una perspectiva de QA enfocada no solamente en comprobar que una funcionalidad funciona, sino también en verificar **cómo responde el sistema frente a entradas incorrectas, datos incompletos y condiciones que deberían impedir una operación**.

---

## Cobertura representada

Los casos seleccionados cubren los cuatro módulos principales del proyecto:

- **Cliente**
- **Mascota**
- **Veterinario**
- **Consulta**

En conjunto, funcionan como una muestra representativa de la estrategia de pruebas aplicada al sistema.

> **Nota:** estos casos son una selección de la suite completa de pruebas del proyecto Veterinaria. La suite completa contiene escenarios adicionales de alta, cancelación, listados, filtros, mensajes y validaciones específicas.
