# Mantenimiento Hospitalario — Plan de Pruebas

![Tipo de ejecución](https://img.shields.io/badge/Ejecución-Manual-lightgrey)
![Módulos](https://img.shields.io/badge/Módulos-Usuarios%20%7C%20Perfiles%20%7C%20Intervenciones-blue)
![Enfoque](https://img.shields.io/badge/Enfoque-Funcional%20%2B%20Validaciones-success)

Selección curada de los casos de prueba más representativos del ciclo de pruebas, pensada para mostrar cobertura, criterio de diseño de casos (valores límite, roles, formatos) y manejo de reglas de negocio, no solo validaciones básicas de campos.

---

## Índice

* [Módulo Usuario](#módulo-usuario)

  * [Registro de Usuario](#registro-de-usuario)
  * [Listado y Filtros](#listado-y-filtros)
  * [Modificación](#modificación)
  * [Baja y Reactivación](#baja-y-reactivación)
  * [Login](#login)
* [Módulo Perfiles](#módulo-perfiles)
* [Módulo Intervenciones](#módulo-intervenciones)
* [Técnicas de diseño de pruebas aplicadas](#técnicas-de-diseño-de-pruebas-aplicadas)

---

## Módulo Usuario

### Registro de Usuario

#### `CP-001` — Registro exitoso de usuario

**Prioridad:** Alta

Caso base: completa todos los campos con datos válidos (nombre, apellido, cédula con formato uruguayo, teléfono, usuario en formato `nombre.apellido`, email, contraseña segura, tipo de usuario).

**Resultado esperado:** El usuario se registra con éxito y queda **pendiente de revisión**.

---

#### `CP-019` vs `CP-020` — Formato de cédula uruguaya

**Prioridad:** Alta

Par de casos complementarios (positivo/negativo) que validan el formato específico de cédula uruguaya (`1.111.111-1`). El caso inválido verifica que el sistema indique el formato correcto esperado.

---

#### `CP-021` a `CP-024` — Validación exhaustiva de "Nombre de Usuario"

**Prioridad:** Alta

Serie de 4 casos que cubren distintas variantes inválidas del campo `nombre.apellido`:

* Con espacio (`nombre apellido`)
* Con signo distinto al punto (`nombre_apellido`)
* Con números (`nombre02`)
* Con mayúsculas (`Nombre.Apellido`)

Buen ejemplo de **partición de equivalencia** aplicada a un único campo con formato estricto.

---

#### `CP-013` / `CP-014` / `CP-015` — Nombre: número, carácter especial y alfabético

**Prioridad:** Alta

Trío clásico de **valores límite/frontera**: mismo campo probado con dato inválido numérico, inválido especial y válido, patrón que se repite consistentemente en todo el módulo (aplicado también a Apellido).

---

#### `CP-026` — Registro con email ya existente

**Prioridad:** Alta

Valida la regla de unicidad de email contra la base de datos, no solo el formato.

---

#### `CP-030` a `CP-034` — Reglas de contraseña

**Prioridad:** Alta

Cobertura completa de la política de contraseñas (mínimo 8 caracteres, debe incluir letras y números): menor a 8, sin letras, sin números, igual a 8 (**caso límite exacto**) y mayor a 8.

---

### Listado y Filtros

#### `CP-038` — Restricción de acceso al listado por rol

**Prioridad:** Alta

Verifica que **solo** Administrador o Auxiliar Administrativo puedan ver el listado de usuarios; cualquier otro perfil queda bloqueado.

---

#### `CP-056` a `CP-059` — Filtrado por cada tipo de usuario

**Prioridad:** Alta

Casos que recorren los distintos roles del dominio hospitalario: Auxiliar Administrativo, Ingeniero Biomédico, Tecnólogo y Técnico, asegurando que el filtro combinatorio funcione para cada uno.

---

#### `CP-063` — Filtrar por nombre inexistente

**Prioridad:** Alta

Caso de **dato no encontrado**: valida que el listado quede vacío y se notifique correctamente, en vez de fallar silenciosamente.

---

### Modificación

#### `CP-074` / `CP-075` — Un Administrador no puede modificar Contraseña ni Nombre de Usuario

**Prioridad:** Alta

Regla de negocio interesante: aunque el actor tiene privilegios administrativos, ciertos campos sensibles (contraseña, username) quedan **fuera de su alcance** incluso al editar a otros usuarios, estableciendo una separación entre "gestión de usuarios" y "credenciales propias".

---

#### `CP-071` a `CP-073` — Matriz de transición de estados

**Prioridad:** Alta

Tres casos que cubren las transiciones válidas del ciclo de vida del usuario:

`Sin validar → Activo` · `Sin validar → Eliminado` · `Activo → Eliminado`

Buen ejemplo de **pruebas de transición de estados**, una técnica más avanzada que la simple validación de campos.

---

#### `CP-070` — Formulario de modificación reutiliza el de registro

**Prioridad:** Alta

Caso de diseño de UI/UX: valida que el formulario de edición sea coherente con el de alta (mismos campos), agregando únicamente el campo "Estado", como control de consistencia entre pantallas.

---

### Baja y Reactivación

#### `CP-087` — Un usuario "Eliminado" no puede iniciar sesión

**Prioridad:** Alta

Conecta el módulo de bajas con el de autenticación: verifica el efecto de la baja lógica sobre el login.

---

#### `CP-088` / `CP-089` — Reactivación de usuario por Admin y Auxiliar

**Prioridad:** Alta

Confirma que la baja es **lógica y reversible**, no un borrado físico, y que ambos roles administrativos pueden ejecutar la reactivación.

---

### Login

#### `CP-142` / `CP-143` — Login bloqueado por estado del usuario

**Prioridad:** Alta

Dos casos que aseguran que el login rechace específicamente a usuarios en estado `Eliminado` y `Sin validar`, cada uno con su propio mensaje, en lugar de utilizar un mensaje genérico de "credenciales incorrectas".

---

## Módulo Perfiles

#### `CP-176` — Registro de perfil por Administrador

**Prioridad:** Alta

---

#### `CP-188` — No se permite un perfil con nombre duplicado

**Prioridad:** Alta

---

#### `CP-208` — Reactivar un perfil dado de baja

**Prioridad:** Alta

Verifica el mismo patrón de baja lógica/reactivación que en el módulo Usuario, mostrando **consistencia de diseño** entre módulos del sistema.

---

#### `CP-202` — Cancelar una modificación de perfil

**Prioridad:** Alta

Valida que al cancelar en el diálogo de confirmación, **ningún cambio se persiste**, evitando ediciones accidentales.

---

## Módulo Intervenciones

#### `CP-144` a `CP-148` — Registro de intervención por cada rol técnico

**Prioridad:** Alta

Serie de 5 casos que confirman que **todos los roles operativos** del hospital (Administrador, Auxiliar Administrativo, Ingeniero Biomédico, Tecnólogo y Técnico) pueden registrar una intervención sobre equipamiento, a diferencia de otros módulos donde el acceso está restringido solo a perfiles administrativos.

Campos cubiertos: fecha/hora, tipo de intervención (**Prevención / Falla / Resolución**), motivo, identificación del equipamiento y observaciones (opcional).

---

#### `CP-150` a `CP-153` — Validación de campos obligatorios de intervención

**Prioridad:** Alta

Casos que descomponen la validación general en un caso por campo obligatorio, permitiendo aislar exactamente qué mensaje de error corresponde a cada uno.

---

## Técnicas de diseño de pruebas aplicadas

| Técnica                                | Ejemplos en este plan                                                            |
| -------------------------------------- | -------------------------------------------------------------------------------- |
| **Partición de equivalencia**          | Validación de formato de `Nombre de Usuario` (espacio, signo, número, mayúscula) |
| **Valores límite**                     | Contraseña de exactamente 8 caracteres (`CP-034`)                                |
| **Pruebas de transición de estados**   | Ciclo `Sin validar → Activo → Eliminado` de Usuarios y Perfiles                  |
| **Pruebas basadas en roles (RBAC)**    | Acceso a listados y modificación restringido por perfil                          |
| **Casos positivo/negativo pareados**   | Cédula válida vs. inválida, email con/sin `@` y `.com`                           |
| **Pruebas de regresión de UI**         | Formulario de modificación vs. formulario de registro                            |
| **Manejo de confirmación/cancelación** | Diálogos de confirmación en alta, baja y modificación                            |

---
