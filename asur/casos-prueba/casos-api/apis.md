# ASUR API — Casos de Prueba Destacados

Este documento presenta una selección de los casos de prueba más representativos del plan de pruebas de la API del Sistema ASUR.

El objetivo de esta selección es mostrar, de forma resumida, el trabajo realizado en **Quality Assurance y API Testing**, destacando escenarios que requieren validación de reglas de negocio, autenticación, autorización, manejo de errores, integridad de datos y restricciones de seguridad.

## Casos de prueba destacados

### 1. Autenticación y seguridad

#### CP266 — Inicio de sesión exitoso

**Endpoint:** `POST /api/auth/login`

Valida que un usuario activo pueda autenticarse utilizando credenciales válidas.

**Resultado esperado:** `200 OK` y generación de un token JWT válido.

---

#### CP267 — Login con credenciales inválidas

Valida el comportamiento del sistema frente a credenciales incorrectas.

**Resultado esperado:** `400 Bad Request`, sin generación de token.

---

#### CP268 — Login de usuario inactivo

Valida que un usuario cuyo estado es `INACTIVO` no pueda autenticarse.

**Resultado esperado:** `401 Unauthorized`.

---

#### CP271 — Múltiples intentos fallidos / fuerza bruta

Se realizan múltiples intentos consecutivos de autenticación utilizando credenciales incorrectas.

**Resultado esperado:** el sistema rechaza los intentos y bloquea temporalmente el acceso durante 15 minutos.

---

### 2. Validaciones e integridad de datos

#### CP219 — Registro de usuario con datos inválidos

**Endpoint:** `POST /api/usuarios`

Se envían datos que incumplen las reglas de validación del sistema.

**Resultado esperado:** `400 Bad Request`, con información sobre los campos inválidos y sin creación del usuario.

---

#### CP220 — Registro con campos obligatorios faltantes

Se prueba el comportamiento de la API cuando uno o más campos obligatorios se encuentran vacíos o son `null`.

**Resultado esperado:** `400 Bad Request`, sin modificación de la base de datos.

---

#### CP221 — Registro de usuario duplicado

Valida que no puedan registrarse usuarios utilizando información única que ya existe, como documento, email o teléfono.

**Resultado esperado:** `409 Conflict`.

---

#### CP257 — Modificación con datos duplicados

**Endpoint:** `PUT /api/usuarios/{id}`

Se intenta modificar un usuario utilizando información que ya pertenece a otro registro.

**Resultado esperado:** `409 Conflict`, sin modificar los datos existentes.

---

### 3. Autorización y control de acceso

#### CP247 — Acceso al listado por usuario no autorizado

Se intenta consultar el listado de usuarios utilizando un usuario con rol Socio o No Socio.

**Resultado esperado:** `403 Forbidden`.

---

#### CP256 — Modificación por usuario no autorizado

**Endpoint:** `PUT /api/usuarios/{id}`

Se intenta modificar información de un usuario utilizando una cuenta que no posee rol Administrador.

**Resultado esperado:** `403 Forbidden`.

---

#### CP272 — Modificación de datos privados

Se valida que incluso un usuario Administrador no pueda modificar determinados datos privados de otro usuario, como su contraseña.

**Resultado esperado:** `403 Forbidden`.

---

### 4. Reglas de negocio

#### CP370 — Solapamiento de actividades

**Endpoint:** `POST /api/actividades`

Se intenta registrar una actividad en un espacio y horario que ya se encuentra ocupado.

**Resultado esperado:** `409 Conflict`.

La nueva actividad no debe ser registrada.

---

#### CP407 — Solapamiento de reservas

**Endpoint:** `POST /api/reservas/confirmar`

Se intenta crear una reserva cuyo horario coincide total o parcialmente con otra reserva o actividad existente.

**Resultado esperado:** `409 Conflict`.

No se crea una nueva reserva.

---

#### CP411 — Cancelación de una reserva ya cancelada

Se intenta cancelar nuevamente una reserva cuyo estado ya es `CANCELADA`.

**Resultado esperado:** `409 Conflict`.

---

### 5. Gestión de permisos

#### CP447 — Vinculación de funcionalidad inactiva

**Endpoint:** `POST /api/permisos/acceso-funcionalidad`

Se intenta asignar a un perfil una funcionalidad cuyo estado es `INACTIVO`.

**Resultado esperado:** `422 Unprocessable Entity`.

---

#### CP451 — Prevención de vínculos duplicados

Se intenta asociar nuevamente funcionalidades que ya se encuentran vinculadas a un perfil.

**Resultado esperado:** `409 Conflict`.

La operación no debe generar relaciones duplicadas ni modificar los datos existentes.

---

### 6. Auditoría

#### CP282 — Acceso a auditoría por usuario no autorizado

**Endpoint:** `GET /api/auditorias/{tipoAuditoria}`

Se intenta consultar información de auditoría utilizando un usuario que no posee permisos administrativos.

**Resultado esperado:** `403 Forbidden`.

---

#### CP280 — Consulta de auditoría con filtros inválidos

Se utilizan filtros incorrectos, como fechas con formato inválido o usuarios inexistentes.

**Resultado esperado:** `400 Bad Request`, con información sobre los parámetros inválidos.

---

## Cobertura demostrada

Los casos seleccionados representan diferentes tipos de pruebas:

| Área | Cobertura |
|---|---|
| Autenticación | Login exitoso, credenciales inválidas, usuarios inactivos |
| Seguridad | Múltiples intentos fallidos y bloqueo temporal |
| Validación | Campos inválidos y campos obligatorios |
| Integridad de datos | Duplicados en registros y modificaciones |
| Autorización | Restricciones por rol |
| Privacidad | Restricciones sobre datos sensibles |
| Reglas de negocio | Solapamiento de actividades y reservas |
| Estados | Baja, reactivación y operaciones sobre estados inválidos |
| Permisos | Funcionalidades activas, inactivas y relaciones duplicadas |
| Auditoría | Acceso autorizado, no autorizado y filtros inválidos |
| HTTP | Validación de códigos `200`, `201`, `400`, `401`, `403`, `404`, `409` y `422` |

## Ejecución de APIs

Además del diseño y gestión de los casos de prueba, se realizaron **dos builds para las APIs** como parte del flujo de trabajo del proyecto.

La ejecución de las pruebas de API se documenta por separado:

**[Ver Ejecución de APIs](./ejecucion-pruebas)**

En esa sección se puede consultar el detalle de las ejecuciones realizadas sobre las colecciones de Postman.

## Herramientas y tecnologías

| Componente | Tecnología |
|---|---|
| Backend | Spring Boot |
| API | REST |
| Cliente de pruebas | Postman |
| Gestión de casos | TestLink |
| Autenticación | JWT |
| Tipo de ejecución | Manual |
| Cobertura | Casos positivos, negativos, autorización y reglas de negocio |

## Documentación relacionada

- [Ejecución de APIs](./results_sistema_asur_apis.csv)
- [Plan de pruebas completo](./plan-pruebas-asur.pdf)
