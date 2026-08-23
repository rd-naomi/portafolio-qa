# ASUR API — Casos de Prueba Destacados

Este documento presenta una selección de los casos de prueba más representativos del plan de pruebas de la API del Sistema ASUR.

El objetivo es mostrar, de forma resumida, el trabajo realizado en **Quality Assurance y API Testing**, destacando escenarios relacionados con autenticación, autorización, validaciones, integridad de datos, reglas de negocio, manejo de errores y restricciones de seguridad.

---

## Casos de prueba destacados

## 1. Autenticación y Seguridad

### CP1 — Inicio de sesión exitoso

**ID:** CP266
**Prioridad:** Alta
**Tipo:** Positivo

**Endpoint:** `POST /api/auth/login`

**Objetivo:** Verificar que un usuario activo pueda autenticarse utilizando credenciales válidas.

**Resultado esperado:**

* Código HTTP: `200 OK`
* Generación de token JWT válido.
* Acceso autorizado a los recursos correspondientes.

---

### CP2 — Inicio de sesión con credenciales inválidas

**ID:** CP267
**Prioridad:** Alta
**Tipo:** Negativo

**Endpoint:** `POST /api/auth/login`

**Objetivo:** Validar el comportamiento de la API ante credenciales incorrectas.

**Resultado esperado:**

* Código HTTP: `400 Bad Request`
* No se genera token.
* El usuario no obtiene acceso a los recursos protegidos.

---

### CP3 — Login de usuario inactivo

**ID:** CP268
**Prioridad:** Alta
**Tipo:** Seguridad

**Endpoint:** `POST /api/auth/login`

**Objetivo:** Verificar que un usuario con estado `INACTIVO` no pueda autenticarse.

**Resultado esperado:**

* Código HTTP: `401 Unauthorized`
* No se genera token válido.

---

### CP4 — Protección ante múltiples intentos fallidos

**ID:** CP271
**Prioridad:** Alta
**Tipo:** Seguridad

**Endpoint:** `POST /api/auth/login`

**Escenario:** Realizar múltiples intentos consecutivos de autenticación utilizando credenciales incorrectas.

**Resultado esperado:**

* Los intentos son rechazados.
* El sistema bloquea temporalmente el acceso.
* El bloqueo tiene una duración de 15 minutos según la regla configurada.

---

## 2. Validaciones e Integridad de Datos

### CP5 — Registro de usuario con datos inválidos

**ID:** CP219
**Prioridad:** Alta
**Tipo:** Negativo

**Endpoint:** `POST /api/usuarios`

**Objetivo:** Verificar que la API rechace información que incumpla las reglas de validación.

**Resultado esperado:**

* Código HTTP: `400 Bad Request`
* Se informa el campo o los campos inválidos.
* El usuario no es creado.

---

### CP6 — Registro con campos obligatorios faltantes

**ID:** CP220
**Prioridad:** Alta
**Tipo:** Validación

**Endpoint:** `POST /api/usuarios`

**Escenario:** Enviar uno o más campos obligatorios vacíos o con valor `null`.

**Resultado esperado:**

* Código HTTP: `400 Bad Request`
* Se informa la validación correspondiente.
* No se modifica la base de datos.

---

### CP7 — Registro de usuario duplicado

**ID:** CP221
**Prioridad:** Alta
**Tipo:** Integridad de datos

**Endpoint:** `POST /api/usuarios`

**Escenario:** Intentar registrar un usuario utilizando información que debe ser única y que ya pertenece a otro registro.

**Datos considerados:**

* Documento.
* Email.
* Teléfono.

**Resultado esperado:**

* Código HTTP: `409 Conflict`
* No se crea un registro duplicado.

---

### CP8 — Modificación con datos duplicados

**ID:** CP257
**Prioridad:** Alta
**Tipo:** Integridad de datos

**Endpoint:** `PUT /api/usuarios/{id}`

**Objetivo:** Verificar que una modificación no permita utilizar información única perteneciente a otro usuario.

**Resultado esperado:**

* Código HTTP: `409 Conflict`
* Los datos existentes permanecen sin modificaciones.

---

## 3. Autorización y Control de Acceso

### CP9 — Acceso a listado por usuario no autorizado

**ID:** CP247
**Prioridad:** Alta
**Tipo:** Autorización

**Endpoint:** Consulta del listado de usuarios.

**Escenario:** Intentar acceder al listado utilizando una cuenta con rol Socio o No Socio.

**Resultado esperado:**

* Código HTTP: `403 Forbidden`
* El recurso no es accesible.

---

### CP10 — Modificación por usuario sin permisos

**ID:** CP256
**Prioridad:** Alta
**Tipo:** Autorización

**Endpoint:** `PUT /api/usuarios/{id}`

**Escenario:** Intentar modificar información utilizando una cuenta que no posee rol Administrador.

**Resultado esperado:**

* Código HTTP: `403 Forbidden`
* No se modifica el registro.

---

### CP11 — Modificación de datos privados

**ID:** CP272
**Prioridad:** Alta
**Tipo:** Seguridad

**Objetivo:** Verificar la protección de información privada de otros usuarios.

**Escenario:** Un usuario Administrador intenta modificar datos privados de otro usuario, como su contraseña.

**Resultado esperado:**

* Código HTTP: `403 Forbidden`
* La información protegida no es modificada.

---

## 4. Reglas de Negocio

### CP12 — Solapamiento de actividades

**ID:** CP370
**Prioridad:** Alta
**Tipo:** Regla de negocio

**Endpoint:** `POST /api/actividades`

**Escenario:** Intentar registrar una actividad en un espacio y horario que ya se encuentra ocupado.

**Resultado esperado:**

* Código HTTP: `409 Conflict`
* La actividad no es registrada.
* El espacio continúa reservado para la actividad existente.

---

### CP13 — Solapamiento de reservas

**ID:** CP407
**Prioridad:** Alta
**Tipo:** Regla de negocio

**Endpoint:** `POST /api/reservas/confirmar`

**Escenario:** Crear una reserva cuyo horario coincide total o parcialmente con una reserva o actividad existente.

**Resultado esperado:**

* Código HTTP: `409 Conflict`
* La nueva reserva no es creada.
* No se genera una superposición de horarios.

---

### CP14 — Cancelación de una reserva ya cancelada

**ID:** CP411
**Prioridad:** Alta
**Tipo:** Validación de estado

**Escenario:** Intentar cancelar nuevamente una reserva cuyo estado ya es `CANCELADA`.

**Resultado esperado:**

* Código HTTP: `409 Conflict`
* El estado permanece sin cambios.

---

## 5. Gestión de Permisos

### CP15 — Vinculación de funcionalidad inactiva

**ID:** CP447
**Prioridad:** Alta
**Tipo:** Regla de negocio

**Endpoint:** `POST /api/permisos/acceso-funcionalidad`

**Escenario:** Intentar asignar a un perfil una funcionalidad cuyo estado es `INACTIVO`.

**Resultado esperado:**

* Código HTTP: `422 Unprocessable Entity`
* La funcionalidad no es vinculada al perfil.

---

### CP16 — Prevención de vínculos duplicados

**ID:** CP451
**Prioridad:** Alta
**Tipo:** Integridad de datos

**Escenario:** Intentar asociar nuevamente una funcionalidad que ya se encuentra vinculada a un perfil.

**Resultado esperado:**

* Código HTTP: `409 Conflict`
* No se crea una relación duplicada.
* Las relaciones existentes permanecen sin modificaciones.

---

## 6. Auditoría

### CP17 — Acceso a auditoría por usuario no autorizado

**ID:** CP282
**Prioridad:** Alta
**Tipo:** Seguridad

**Endpoint:** `GET /api/auditorias/{tipoAuditoria}`

**Escenario:** Intentar consultar información de auditoría utilizando un usuario sin permisos administrativos.

**Resultado esperado:**

* Código HTTP: `403 Forbidden`
* La información de auditoría no es expuesta.

---

### CP18 — Consulta de auditoría con filtros inválidos

**ID:** CP280
**Prioridad:** Media
**Tipo:** Validación

**Endpoint:** `GET /api/auditorias/{tipoAuditoria}`

**Escenario:** Realizar consultas utilizando parámetros inválidos, por ejemplo:

* Fechas con formato incorrecto.
* Usuarios inexistentes.
* Parámetros con valores no permitidos.

**Resultado esperado:**

* Código HTTP: `400 Bad Request`
* Se informa el parámetro inválido.
* No se procesa una consulta incorrecta.

---

## Cobertura

Los casos seleccionados representan diferentes áreas y tipos de pruebas realizadas sobre la API:

| Área                | Cobertura                                                  |
| ------------------- | ---------------------------------------------------------- |
| Autenticación       | Login exitoso, credenciales inválidas y usuarios inactivos |
| Seguridad           | Bloqueo ante múltiples intentos fallidos                   |
| Validación          | Datos inválidos y campos obligatorios                      |
| Integridad de datos | Registros y modificaciones duplicadas                      |
| Autorización        | Restricciones según rol                                    |
| Privacidad          | Protección de datos sensibles                              |
| Reglas de negocio   | Solapamiento de actividades y reservas                     |
| Estados             | Operaciones sobre estados inválidos                        |
| Permisos            | Funcionalidades activas, inactivas y relaciones duplicadas |
| Auditoría           | Acceso autorizado, no autorizado y filtros inválidos       |
| HTTP                | Validación de respuestas y códigos de error                |

---

## Tipos de validación aplicados

* Validación de campos obligatorios.
* Validación de formatos.
* Validación de datos inválidos.
* Validación de duplicados.
* Validación de estados.
* Validación de reglas de negocio.
* Validación de autorización.
* Validación de autenticación.
* Validación de integridad de datos.
* Validación de manejo de errores HTTP.
* Validación de restricciones de seguridad.

---

## Patrones de prueba aplicados

1. **Pruebas positivas y negativas:** validación de respuestas ante solicitudes válidas e inválidas.
2. **Boundary / Edge Cases:** escenarios de límite y condiciones excepcionales.
3. **Reglas de negocio:** validación de restricciones propias del dominio.
4. **Autenticación:** validación de acceso mediante credenciales y JWT.
5. **Autorización:** validación de permisos según rol.
6. **Integridad de datos:** prevención de duplicados y relaciones inválidas.
7. **Manejo de errores:** validación de códigos HTTP y respuestas ante solicitudes incorrectas.
8. **Validación de estados:** comportamiento ante operaciones no permitidas según el estado de la entidad.

---

## Ejecución de APIs

Además del diseño y gestión de los casos de prueba, se realizaron **dos ejecuciones sobre las APIs** correspondientes a diferentes builds del sistema.

Los resultados detallados de las ejecuciones se documentan por separado.

**[Ver resultados de ejecución de APIs](./ejecucion-pruebas/results_sistema_asur_apis.csv)**

---

## Herramientas y tecnologías

| Componente         | Tecnología                                              |
| ------------------ | ------------------------------------------------------- |
| Backend            | Spring Boot                                             |
| Arquitectura       | REST API                                                |
| Cliente de pruebas | Postman                                                 |
| Gestión de casos   | TestLink                                                |
| Autenticación      | JWT                                                     |
| Ejecución          | Pruebas manuales                                        |
| Tipo de pruebas    | Funcionales, integración, seguridad y reglas de negocio |

---

## Documentación relacionada

* [Resultados de ejecución de APIs](./ejecucion-pruebas/results_sistema_asur_apis.csv)
* [Plan de pruebas completo](./plan-pruebas-asur.pdf)
* Casos de prueba completos.
* Registro de incidencias.
