# Sistema Veterinario — Plan de Pruebas

![Tipo de ejecución](https://img.shields.io/badge/Ejecución-Manual-lightgrey)
![Módulos](https://img.shields.io/badge/Módulos-Cliente%20%7C%20Mascota%20%7C%20Veterinario%20%7C%20Consulta-blue)
![Enfoque](https://img.shields.io/badge/Enfoque-Funcional%20%2B%20Validaciones-success)
![Casos](https://img.shields.io/badge/Casos%20Totales-71-orange)

Selección curada de casos de prueba representativos que demuestran cobertura integral, diseño de casos avanzado (partición de equivalencia, valores límite, casos pareados), validación de reglas de negocio y gestión de errores en un sistema de gestión veterinaria.

---

## Índice

* [Módulo Cliente](#módulo-cliente)
  * [Registro de Cliente](#registro-de-cliente)
  * [Validación de Cédula](#validación-de-cédula)
  * [Validación de Nombre y Apellido](#validación-de-nombre-y-apellido)
  * [Campos Obligatorios](#campos-obligatorios)
  * [Operaciones](#operaciones)
* [Módulo Mascota](#módulo-mascota)
  * [Registro de Mascota](#registro-de-mascota)
  * [Validación de Patente](#validación-de-patente)
  * [Validación de Campos de Mascota](#validación-de-campos-de-mascota)
  * [Búsqueda y Filtrado](#búsqueda-y-filtrado)
  * [Referencias Cruzadas](#referencias-cruzadas)
* [Módulo Veterinario](#módulo-veterinario)
  * [Registro de Veterinario](#registro-de-veterinario)
  * [Validación de Código](#validación-de-código)
  * [Validación de Especialidad](#validación-de-especialidad)
  * [Campos Obligatorios](#campos-obligatorios-1)
* [Módulo Consulta](#módulo-consulta)
  * [Registro de Consulta](#registro-de-consulta)
  * [Validación de Fecha](#validación-de-fecha)
  * [Referencias de Entidades](#referencias-de-entidades)
  * [Búsqueda de Consultas](#búsqueda-de-consultas)
* [Matriz de Técnicas de Diseño](#matriz-de-técnicas-de-diseño)

---

## Módulo Cliente

### Registro de Cliente

#### `CP-001` — Registro exitoso de cliente

**Prioridad:** Alta

Caso base: el usuario completa todos los campos obligatorios con datos válidos (nombre 3-20 caracteres alfabéticos, apellido 3-21 caracteres alfabéticos, cédula formato `1.111.111-1`).

**Resultado esperado:** Cliente registrado con éxito; datos grabados y confirmados mediante mensaje positivo.

---

#### `CP-002` — Cancelar el registro de un cliente

**Prioridad:** Alta

Verifica que la operación de cancelación sea funcional: el usuario completa el formulario pero presiona "Cancelar" en lugar de "Ingresar".

**Resultado esperado:** Se despliega mensaje de cancelación y **ningún dato se persiste** en la base de datos.

---

### Validación de Cédula

#### `CP-003` (Válida) vs `CP-004` / `CP-005` / `CP-006` (Inválidas) — Formato de cédula uruguaya

**Prioridad:** Alta

Serie de 4 casos complementarios que validan el formato específico de cédula uruguaya (`1.111.111-1`):

* **`CP-003`** — Cédula válida acepta el registro ✅
* **`CP-004`** — Sin puntos: `11111111` → **Rechaza** con mensaje de formato
* **`CP-005`** — Insuficiente: `222` → **Rechaza** con mensaje de formato
* **`CP-006`** — Campo vacío → **Rechaza** con mensaje de formato

Buen ejemplo de **partición de equivalencia** y **casos pareados positivo/negativo**.

---

#### `CP-007` — Cédula con caracteres inválidos

**Prioridad:** Alta

Valor límite: cédula contiene 1 letra y 1 guion bajo (`1_1.234.245_2`). Verifica que el sistema rechace caracteres no numéricos (excepto puntos y guion).

---

### Validación de Nombre y Apellido

#### `CP-008` / `CP-009` / `CP-010` — Nombre: número, carácter especial, válido

**Prioridad:** Alta

Trío clásico de **valores límite**: mismo campo probado con dato inválido numérico, inválido especial, y válido:

* **`CP-008`** — Nombre con 3 números: `123` → **Rechaza** (solo alfabético)
* **`CP-009`** — Nombre con carácter especial: `Juan@` → **Rechaza** (formato incorrecto)
* **`CP-010`** — Nombre alfabético válido → ✅ **Acepta**

---

#### `CP-011` / `CP-012` — Nombre: rango de caracteres

**Prioridad:** Alta

Validación de límites de longitud:

* **`CP-011`** — Nombre <3 caracteres → **Rechaza** con mensaje "3 a 20 caracteres"
* **`CP-012`** — Nombre >20 caracteres → **Rechaza** con mensaje "3 a 20 caracteres"

Buen ejemplo de **valores límite exactos** (min y max).

---

#### `CP-013` / `CP-014` / `CP-015` — Apellido: número, carácter especial, rango

**Prioridad:** Alta

Mismo patrón que Nombre, aplicado al campo Apellido (rango 3-21 caracteres).

---

### Campos Obligatorios

#### `CP-016` a `CP-019` — Validación individual de campos vacíos

**Prioridad:** Alta

Matriz de 4 casos que aisla exactamente qué sucede cuando se deja vacío cada campo requerido:

| Caso | Campo Vacío | Campos Válidos | Resultado |
|------|------------|----------------|-----------|
| `CP-016` | Nombre | Apellido, Cédula | ❌ "Completar todos los campos" |
| `CP-017` | Apellido | Nombre, Cédula | ❌ "Completar todos los campos" |
| `CP-018` | Cédula | Nombre, Apellido | ❌ "Completar todos los campos" |
| `CP-019` | Todos | — | ❌ "Completar todos los campos" |

Permite identificar si la validación falla en un campo específico o en la lógica general.

---

#### `CP-020` — Mensaje de UI: pantalla "Nuevo Cliente"

**Prioridad:** Media

Valida que los nombres de campos, etiquetas y mensajes en la ventana "Nuevo Cliente" estén escritos correctamente (ortografía, consistencia, claridad).

---

### Operaciones

#### `CP-021` — Email duplicado no permitido

**Prioridad:** Alta

Verifica que el sistema valide la **unicidad de email** contra la base de datos, no solo el formato. Caso regla de negocio.

---

---

## Módulo Mascota

### Registro de Mascota

#### `CP-025` — Registro exitoso de mascota

**Prioridad:** Alta

Caso base: usuario completa todos los campos con datos válidos (nro patente `3 números + 1 mayúscula`, nombre 2-15 caracteres, tipo seleccionado de comboBox, edad 1-2 dígitos, cliente seleccionado de comboBox).

**Resultado esperado:** Mascota registrada con éxito; datos grabados confirmados.

---

#### `CP-026` — Cancelar el registro de una mascota

**Prioridad:** Alta

Usuario completa formulario pero presiona "Cancelar".

**Resultado esperado:** Mensaje de cancelación y **ningún dato se persiste**.

---

### Validación de Patente

#### `CP-027` (Válida) vs `CP-028` / `CP-029` / `CP-030` / `CP-031` (Inválidas) — Formato Nro Patente

**Prioridad:** Alta

Serie de casos exhaustivos que validan formato requerido: **3 números + 1 letra MAYÚSCULA** (ej: `234T`):

* **`CP-027`** — Patente válida: `123A` → ✅ **Acepta**
* **`CP-028`** — Exceso de números: `1234A` → **Rechaza** (debe ser 3 números + 1 mayúscula)
* **`CP-029`** — Solo números: `123` → **Rechaza** (debe incluir 1 letra mayúscula)
* **`CP-030`** — Espacios en blanco: `   ` → **Rechaza** (formato requerido)
* **`CP-031`** — Carácter especial: `234-T` → **Rechaza** (formato incorrecto)
* **`CP-032`** — Solo alfabético: `DDDD` → **Rechaza** (debe incluir números)

**Partición de equivalencia** completa para un campo con regla de formato estricta.

---

### Validación de Campos de Mascota

#### `CP-033` / `CP-034` / `CP-035` — Nombre: longitud y caracteres

**Prioridad:** Alta

Validación de rango 2-15 caracteres:

* **`CP-033`** — Nombre >15 caracteres → **Rechaza**
* **`CP-034`** — Nombre <2 caracteres → **Rechaza**
* **`CP-035`** — Nombre con carácter especial: `Toby!` → **Rechaza** (solo alfabético)

---

#### `CP-036` / `CP-037` / `CP-038` / `CP-039` — Edad: validación numérica

**Prioridad:** Alta

Cobertura de formato (máximo 2 dígitos, positivo, solo números):

* **`CP-036`** — Edad >2 dígitos: `123` → **Rechaza**
* **`CP-037`** — Edad negativa: `-5` → **Rechaza**
* **`CP-038`** — Edad con letra: `3j` → **Rechaza** (solo números)
* **`CP-039`** — Edad con especial: `3@` → **Rechaza** (formato incorrecto)

---

#### `CP-040` a `CP-043` — Campos obligatorios de Mascota

**Prioridad:** Alta

Matriz de 4 casos que aísla cada campo requerido dejándolo vacío:

| Caso | Campo Vacío | Resultado |
|------|------------|-----------|
| `CP-040` | Nro Patente | ❌ "Completar todos los campos" |
| `CP-041` | Nombre | ❌ "Completar todos los campos" |
| `CP-042` | Edad | ❌ "Completar todos los campos" |
| `CP-043` | Tipo / Cliente | ❌ "Completar todos los campos" |

---

### Referencias Cruzadas

#### `CP-044` — El comboBox "Cliente" contiene clientes existentes

**Prioridad:** Alta

Verifica que al abrir el formulario de nueva mascota, el comboBox de Cliente sea **poblado dinámicamente** desde la BD. Usuario selecciona cliente existente y la selección se graba.

---

#### `CP-045` — El comboBox "Tipo" contiene tipos de mascotas válidos

**Prioridad:** Alta

Mismo patrón: comboBox "Tipo" muestra el catálogo de tipos de mascota del sistema (Perro, Gato, Ave, etc.) y la selección se persiste.

---

### Búsqueda y Filtrado

#### `CP-046` / `CP-047` / `CP-048` / `CP-049` — Listado de Mascotas con filtros

**Prioridad:** Alta

Casos que validan la funcionalidad de búsqueda/filtrado en el listado:

* **`CP-046`** — Patente existente + Tipo "Todos" → ✅ **Devuelve registros con filtro aplicado**
* **`CP-047`** — Patente existente + Tipo válido (coincidencia) → ✅ **Devuelve registro específico**
* **`CP-048`** — Patente existente + Tipo inexistente (sin coincidencia) → **Grilla vacía** (comportamiento correcto)
* **`CP-049`** — Patente inexistente → **Grilla vacía** + notificación (dato no encontrado)

Casos pareados positivo/negativo que validan lógica de filtrado en lugar de solo alta de registros.

---

#### `CP-050` — Mensaje de UI: pantalla "Listar Mascotas"

**Prioridad:** Media

Verifica ortografía y claridad en nombres de campos, botones y mensajes de la ventana de listado.

---

---

## Módulo Veterinario

### Registro de Veterinario

#### `CP-051` — Registro exitoso de veterinario

**Prioridad:** Alta

Caso base: usuario completa todos los campos obligatorios con datos válidos (código formato `NNLLL`, especialidad seleccionada, nombre hasta 18 caracteres alfabéticos, cédula formato `1.111.111-1`).

**Resultado esperado:** Veterinario registrado con éxito; datos grabados confirmados.

---

#### `CP-052` — Cancelar el registro de un veterinario

**Prioridad:** Alta

Usuario completa formulario pero presiona "Cancelar".

**Resultado esperado:** Mensaje de cancelación y **ningún dato se persiste**.

---

### Validación de Código

#### `CP-053` (Válido) vs `CP-054` / `CP-055` (Inválidos) — Formato de Código Veterinario

**Prioridad:** Alta

Formato requerido: **3 números + 3 letras** (ej: `123ABC`):

* **`CP-053`** — Código válido: `123ABC` → ✅ **Acepta**
* **`CP-054`** — Solo números: `123` → **Rechaza** (debe ser NNLLL)
* **`CP-055`** — Solo letras: `ABCDE` → **Rechaza** (formato incorrecto)

---

### Validación de Especialidad

#### `CP-056` — El comboBox "Especialidad" contiene especialidades válidas

**Prioridad:** Alta

Verifica que el comboBox sea poblado dinámicamente desde catálogo (Cardiólogo, Cirujano, Oftalmólogo, etc.) y la selección se grabe correctamente.

---

#### `CP-057` a `CP-059` — Campos obligatorios de Veterinario

**Prioridad:** Alta

Matriz de 3 casos aislando cada campo requerido dejándolo vacío:

| Caso | Campo Vacío | Resultado |
|------|------------|-----------|
| `CP-057` | Código | ❌ "Completar todos los campos" |
| `CP-058` | Nombre | ❌ "Completar todos los campos" |
| `CP-059` | Cédula | ❌ "Completar todos los campos" |

---

#### `CP-060` — Nombre: rango 3-18 caracteres

**Prioridad:** Alta

Validación de límites de longitud de nombre de veterinario (más restrictivo que cliente).

---

#### `CP-061` — Cédula: formato 1.111.111-1

**Prioridad:** Alta

Valida que la cédula de veterinario respete el mismo formato que cliente (consistencia entre módulos).

---

#### `CP-062` — Código duplicado no permitido

**Prioridad:** Alta

Verifica **unicidad del código de veterinario** contra la BD. Caso de regla de negocio.

---

#### `CP-063` — Mensaje de UI: pantalla "Nuevo Veterinario"

**Prioridad:** Media

Verifica ortografía y claridad en interfaz de registro.

---

---

## Módulo Consulta

### Registro de Consulta

#### `CP-064` — Registro exitoso de consulta

**Prioridad:** Alta

Caso base: usuario ingresa patente válida (existente), selecciona veterinario, ingresa fecha ≤ fecha actual, presiona "Ingresar".

**Resultado esperado:** Consulta registrada con éxito.

---

#### `CP-065` — Cancelar el registro de una consulta

**Prioridad:** Alta

Usuario completa formulario pero presiona "Cancelar".

**Resultado esperado:** Mensaje de cancelación y **ningún dato se persiste**.

---

### Validación de Fecha

#### `CP-066` (Válida) vs `CP-067` (Inválida) — Fecha no mayor a la actual

**Prioridad:** Alta

Casos pareados positivo/negativo que validan **regla de negocio crítica**:

* **`CP-066`** — Fecha = hoy o pasado → ✅ **Acepta**
* **`CP-067`** — Fecha > hoy (fecha futura) → **Rechaza** con mensaje "No es posible registrar consulta con fecha futura"

Buen ejemplo de validación que no es solo formato, sino **lógica de negocio**.

---

### Referencias de Entidades

#### `CP-068` — El veterinario debe existir en el sistema

**Prioridad:** Alta

Verifica que el campo de veterinario valide contra la BD (comboBox selecciona veterinario registrado).

---

#### `CP-069` (Válida) vs `CP-070` (Inválida) — Nro Patente existente

**Prioridad:** Alta

Casos pareados que validan **integridad referencial**:

* **`CP-069`** — Patente existente → ✅ **Permite registrar consulta**
* **`CP-070`** — Patente inexistente → **Rechaza** con mensaje "No es posible registrar; patente no existe"

Regla de negocio: no se puede crear consulta para mascota que no existe.

---

### Búsqueda de Consultas

#### `CP-071` / `CP-072` / `CP-073` — Listado de Consultas con filtro de fecha

**Prioridad:** Alta

Validación de búsqueda por rango temporal:

* **`CP-071`** — Filtrar por fecha válida con datos existentes → ✅ **Muestra registros de esa fecha**
* **`CP-072`** — Filtrar sin ingresar fecha → **Rechaza** con mensaje "Ingrese una fecha para filtrar"
* **`CP-073`** — Filtrar + "Limpiar Filtro" → ✅ **Restaura listado completo**

Casos que validan no solo la funcionalidad, sino el flujo completo de filtrado y limpieza.

---

#### `CP-074` — Mensaje de UI: pantalla "Listar Consulta"

**Prioridad:** Media

Verifica ortografía y claridad en interfaz de listado de consultas.

---

---

## Matriz de Técnicas de Diseño

| Técnica | Ejemplos en este Plan | Casos |
|---------|----------------------|-------|
| **Partición de equivalencia** | Formato de cédula, patente, código veterinario | `CP-004..007`, `CP-028..032`, `CP-053..055` |
| **Valores límite / Rango** | Nombre 3-20, Apellido 3-21, Edad 1-2, Nombre vet 3-18 | `CP-011..012`, `CP-013..015`, `CP-036..039` |
| **Casos pareados positivo/negativo** | Cédula válida vs. inválida, Patente válida vs. inválida, Fecha válida vs. futura | `CP-003 vs 004..007`, `CP-027 vs 028..032`, `CP-066 vs 067` |
| **Validación de campos obligatorios** | Matriz aislada por campo dejado vacío | `CP-016..019`, `CP-040..043`, `CP-057..059` |
| **Integridad referencial (FK)** | Patente debe existir para crear consulta, Cliente debe existir para mascota | `CP-069..070`, `CP-044`, `CP-045` |
| **Restricción de datos únicos** | Email cliente, Código veterinario | `CP-021`, `CP-062` |
| **Validación de UI/UX** | Ortografía, claridad, consistencia de mensajes | `CP-020`, `CP-050`, `CP-063`, `CP-074` |
| **Reglas de negocio** | Fecha consulta ≤ actual, Patente 3 números + 1 mayúscula | `CP-066..067`, `CP-027..032` |
| **Flujos de cancelación** | Cancelar alta de cliente, mascota, veterinario, consulta | `CP-002`, `CP-026`, `CP-052`, `CP-065` |
| **Búsqueda y filtrado** | Listado de mascotas con filtros, consultas por fecha | `CP-046..049`, `CP-071..073` |

---

## Estadísticas de Cobertura

| Métrica | Valor |
|---------|-------|
| **Casos Totales en Plan** | 71 |
| **Casos Destacados (este documento)** | 74 (CP-001 a CP-074) |
| **Módulos Cubiertos** | 4 (Cliente, Mascota, Veterinario, Consulta) |
| **Validaciones Funcionales** | ~35 |
| **Validaciones de Datos** | ~25 |
| **Pruebas de UI/UX** | ~4 |
| **Reglas de Negocio** | ~10 |

---
