# ASUR WEB — Casos de Prueba Destacados

Este documento presenta una selección de los casos de prueba más representativos del sistema ASUR, destacando escenarios funcionales, validaciones de reglas de negocio, restricciones, integridad de datos y casos de borde.

El objetivo es mostrar, de forma resumida, el trabajo realizado, incluyendo validaciones positivas y negativas sobre los principales módulos de la aplicación.

---

## Casos de prueba destacados

## 1. Gestión de Usuarios

### CP1 — Registro de usuario con datos válidos

**ID:** PFTDZGR06-55
**Prioridad:** Alta
**Tipo:** Positivo

**Objetivo:** Verificar el registro exitoso de un usuario No Socio utilizando información válida.

| Paso | Acción                                  | Resultado esperado                            |
| ---- | --------------------------------------- | --------------------------------------------- |
| 1    | Seleccionar "Registro de nuevo usuario" | El formulario se muestra correctamente        |
| 2    | Completar los campos con datos válidos  | Los datos son aceptados                       |
| 3    | Confirmar el registro                   | El sistema procesa correctamente la operación |
| 4    | Verificar el resultado                  | El usuario queda registrado                   |

---

### CP2 — Registro con email duplicado

**ID:** PFTDZGR06-3
**Prioridad:** Media
**Tipo:** Negativo

**Objetivo:** Verificar que el sistema impida registrar un usuario utilizando un email existente.

**Precondición:**

* Debe existir un usuario registrado con el email utilizado en la prueba.

| Paso | Acción                                   | Resultado esperado                                  |
| ---- | ---------------------------------------- | --------------------------------------------------- |
| 1    | Acceder al formulario de registro        | Formulario visible                                  |
| 2    | Ingresar un email ya registrado          | El dato es ingresado                                |
| 3    | Completar los demás campos correctamente | El formulario queda válido                          |
| 4    | Confirmar el registro                    | El sistema rechaza la operación por email duplicado |

---

### CP3 — Validación de contraseña

**ID:** PFTDZGR06-140, 141, 142
**Prioridad:** Alta
**Tipo:** Validación de negocio

**Objetivo:** Verificar el cumplimiento de las reglas de complejidad de contraseña.

| Escenario             | Entrada    | Resultado |
| --------------------- | ---------- | --------- |
| Solo caracteres       | `holahola` | Rechazado |
| Solo números          | `12345678` | Rechazado |
| Menos de 8 caracteres | `hola123`  | Rechazado |
| Alfanumérico válido   | `hola1234` | Aceptado  |

**Regla de negocio:** La contraseña debe contener caracteres y números y tener una longitud mínima de 8 caracteres.

---

### CP4 — Filtrado de usuarios por múltiples criterios

**ID:** PFTDZGR06-29, 69, 70, 71, 72
**Prioridad:** Alta
**Tipo:** Funcional

**Objetivo:** Verificar el correcto funcionamiento de los filtros disponibles en el listado de usuarios.

**Criterios validados:**

* Estado: Activo / Inactivo
* Nombre
* Apellido
* Documento
* Tipo de usuario: Socio / No Socio / Administrador

**Resultado esperado:** El listado muestra únicamente los registros que cumplen con los criterios seleccionados.

---

### CP5 — Modificación de usuario y protección de campos

**ID:** PFTDZGR06-75, 76, 77, 78
**Prioridad:** Alta
**Tipo:** Seguridad

**Objetivo:** Verificar que determinados datos del usuario permanezcan protegidos durante la modificación.

**Campos no modificables:**

* Número de documento
* Tipo de documento
* Email
* Contraseña

**Campos modificables:**

* Nombre
* Apellido
* Fecha de nacimiento
* Teléfono
* Domicilio
* Tipo de usuario

**Resultado esperado:** El sistema permite modificar únicamente los campos autorizados.

---

## 2. Gestión de Actividades

### CP6 — Registro de actividad con validaciones de negocio

**ID:** PFTDZGR06-227
**Prioridad:** Media
**Tipo:** Flujo de negocio

**Objetivo:** Verificar el registro de una actividad considerando las reglas de negocio asociadas.

**Campos y reglas validadas:**

* Nombre de actividad: requerido
* Descripción: requerida
* Tipo de actividad: selección obligatoria
* Fecha: futura y requerida
* Lugar/Espacio: sujeto a disponibilidad
* Duración: requerida
* Requiere inscripción: Sí / No
* Fecha de apertura de inscripción: anterior a la actividad
* Costo: valor positivo
* Forma de pago: requerida

**Resultado esperado:** La actividad se registra únicamente cuando todos los datos cumplen las reglas establecidas.

---

### CP7 — Validación de fechas y disponibilidad

**ID:** PFTDZGR06-235, 237
**Prioridad:** Alta
**Tipo:** Validación de lógica

| Escenario          | Entrada                        | Resultado esperado                    |
| ------------------ | ------------------------------ | ------------------------------------- |
| Fecha anterior     | 28/10/2020                     | Rechazado: la fecha debe ser futura   |
| Fecha vacía        | Vacío                          | Rechazado: campo requerido            |
| Lugar ocupado      | Mismo horario                  | El espacio no aparece como disponible |
| Apertura posterior | Fecha posterior a la actividad | Rechazado                             |

---

### CP8 — Disponibilidad de espacios ante conflictos horarios

**ID:** PFTDZGR06-237
**Prioridad:** Alta
**Tipo:** Regla de negocio

**Escenario:**

* Actividad A: 15/09/2026, 10:00–12:00, Salón A.
* Actividad B: 15/09/2026, 11:00–13:00.

**Resultado esperado:**

* Salón A no debe aparecer entre los espacios disponibles.
* Solo deben mostrarse espacios libres para la fecha y horario seleccionados.

---

### CP9 — Baja de actividad con restricciones

**ID:** PFTDZGR06-464
**Prioridad:** Alta
**Tipo:** Regla de negocio

**Condiciones validadas:**

* La actividad se encuentra activa.
* La inscripción no se encuentra abierta.
* La actividad aún no comenzó.

**Escenarios bloqueados:**

| Condición             | Resultado esperado                       |
| --------------------- | ---------------------------------------- |
| Inscripción abierta   | Operación rechazada                      |
| Actividad en progreso | Operación bloqueada                      |
| Actividad finalizada  | Operación permitida según regla definida |

---

### CP10 — Inscripción a actividad

**ID:** PFTDZGR06-468, 469
**Prioridad:** Alta
**Tipo:** Flujo de usuario

**Validaciones:**

* Período de inscripción abierto.
* Usuario no inscripto previamente.
* Capacidad disponible.
* Usuario activo.

**Resultado esperado:** Se registra correctamente la inscripción y se muestra la confirmación correspondiente.

---

## 3. Gestión de Espacios y Reservas

### CP11 — Registro de espacio con validaciones

**ID:** PFTDZGR06-479
**Prioridad:** Alta
**Tipo:** Maestro de datos

| Campo             | Validación                   |
| ----------------- | ---------------------------- |
| Nombre            | Obligatorio                  |
| Capacidad máxima  | Número positivo              |
| Precio Socio      | Número positivo              |
| Precio No Socio   | Número positivo              |
| Fecha de vigencia | Formato válido y obligatoria |
| Observaciones     | Opcional                     |

**Validaciones especiales:**

* La capacidad no admite valores negativos ni texto.
* Los precios deben ser valores numéricos positivos.
* La fecha debe cumplir el formato establecido.

---

### CP12 — Reserva de espacio y cálculo de vencimiento de seña

**ID:** PFTDZGR06-500
**Prioridad:** Alta
**Tipo:** Lógica de negocio

**Regla:** La fecha de vencimiento de la seña se calcula cinco días hábiles antes de la actividad.

**Ejemplo:**

* Fecha de actividad: 28/10/2026.
* Fecha de vencimiento: cinco días hábiles antes, según calendario laboral aplicado por el sistema.

**Resultado esperado:** El sistema calcula correctamente la fecha límite de pago.

---

### CP13 — Tarifa diferenciada según tipo de usuario

**ID:** PFTDZGR06-501, 502
**Prioridad:** Alta
**Tipo:** Regla de negocio

| Tipo de usuario | Tarifa          |
| --------------- | --------------- |
| Socio           | Tarifa reducida |
| No Socio        | Tarifa general  |

**Resultado esperado:** El sistema muestra y aplica la tarifa correspondiente al tipo de usuario autenticado.

---

### CP14 — Cancelación de reserva y liberación del espacio

**ID:** PFTDZGR06-507
**Prioridad:** Alta
**Tipo:** Integridad de datos

**Flujo:**

1. Crear una reserva para un espacio determinado.
2. Cancelar la reserva.
3. Consultar nuevamente la disponibilidad.
4. Verificar el estado del espacio.

**Resultado esperado:** El espacio queda nuevamente disponible para la fecha y horario correspondientes.

---

### CP15 — Cancelación automática por falta de pago

**ID:** PFTDZGR06-504
**Prioridad:** Alta
**Tipo:** Proceso automático

**Escenario:** Verificar la cancelación automática de una reserva cuando:

* La fecha límite de pago fue superada.
* No existe un pago registrado.

**Resultado esperado:** El estado de la reserva cambia automáticamente a `CANCELADA`.

---

## 4. Gestión de Perfiles y Funcionalidades

### CP16 — Registro de perfil

**ID:** PFTDZGR06-16
**Prioridad:** Alta
**Tipo:** Maestro de datos

| Campo       | Validación                         |
| ----------- | ---------------------------------- |
| Nombre      | Alfanumérico, máximo 50 caracteres |
| Descripción | Texto, máximo 300 caracteres       |
| Estado      | Activo / Inactivo                  |

**Resultado esperado:** El sistema registra el perfil únicamente cuando los datos cumplen las reglas definidas.

---

### CP17 — Vinculación de funcionalidades a perfiles

**ID:** PFTDZGR06-124, 189
**Prioridad:** Media
**Tipo:** Relación maestro-detalle

**Escenarios validados:**

* Vincular una funcionalidad a un perfil.
* Vincular múltiples funcionalidades.
* Desvincular funcionalidades.
* Consultar las vinculaciones existentes.
* Impedir vinculaciones duplicadas.
* Impedir asociaciones con elementos inactivos.

**Resultado esperado:** Se mantiene la integridad de las relaciones entre perfiles y funcionalidades.

---

## 5. Auditoría y Seguridad

### CP18 — Registro de auditoría

**ID:** PFTDZGR06-222
**Prioridad:** Alta
**Tipo:** Auditoría

**Información validada:**

* Fecha de acción.
* Hora de acción.
* Usuario que ejecutó la operación.
* Terminal/IP cuando corresponde.
* Tipo de operación.
* Entidad afectada.

**Resultado esperado:** Las operaciones relevantes quedan registradas correctamente en la auditoría.

---

### CP19 — Filtrado de registros de auditoría

**ID:** PFTDZGR06-223, 224, 225, 226
**Prioridad:** Alta
**Tipo:** Consulta de datos

**Filtros validados:**

* Usuario.
* Rango de fechas.
* Tipo de operación.
* Combinación de filtros.

**Resultado esperado:** El sistema devuelve únicamente los registros que cumplen los criterios seleccionados.

---

## Cobertura por módulo

| Módulo                     | Casos del plan |
| -------------------------- | -------------- |
| Gestión de Usuarios        | 35             |
| Gestión de Actividades     | 45             |
| Gestión de Espacios        | 20             |
| Gestión de Reservas        | 15             |
| Gestión de Perfiles        | 20             |
| Gestión de Funcionalidades | 15             |
| Auditoría                  | 10             |
| **TOTAL**                  | **195**        |

> Los casos anteriores representan una selección de los casos más relevantes del conjunto completo de 195 casos de prueba.

---

## Tipos de validación aplicados

* Validaciones de campos obligatorios.
* Validaciones de formato.
* Validaciones de longitud.
* Validaciones de rango.
* Validaciones de fechas.
* Validaciones de duplicados.
* Validaciones de reglas de negocio.
* Validaciones de disponibilidad.
* Validaciones de restricciones.
* Validaciones de integridad de datos.
* Validaciones de seguridad y permisos.

---

## Patrones de prueba aplicados

1. **Pruebas positivas y negativas:** comportamiento esperado ante datos válidos e inválidos.
2. **Edge Cases:** validación de límites y condiciones excepcionales.
3. **Flujos completos:** validación de procesos desde el inicio hasta su finalización.
4. **Reglas de negocio:** comprobación de restricciones específicas del sistema.
5. **Integridad referencial:** validación de relaciones entre entidades.
6. **Seguridad:** protección de información y restricciones de acceso.
7. **Validación de estados:** comportamiento según el estado actual de las entidades.

---

## Herramientas y tecnologías

| Componente             | Tecnología                                                  |
| ---------------------- | ----------------------------------------------------------- |
| Aplicación             | Aplicación Web                                              |
| Frontend               | React                                                       |
| Gestión de casos       | TestLink                                                    |
| Gestión de incidencias | Mantis                                                      |
| Ejecución              | Pruebas manuales                                            |
| Tipo de pruebas        | Funcionales, integración, regresión, seguridad y usabilidad |

---

## Documentación relacionada

* [Resultados de ejecución de WEB](./ejecucion-pruebas/results_sistema_asur_web.csv)
* [Plan de pruebas completo](./plan-pruebas-asur.pdf)
* Casos de prueba completos.
* Registro de incidencias.
