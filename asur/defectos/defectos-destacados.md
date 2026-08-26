# Defectos Destacados

Selección de defectos relevantes identificados durante las pruebas de ASUR y registrados mediante **MantisBT**.

Los defectos fueron analizados considerando prioridad, gravedad, reproducibilidad, módulo afectado, estado y resolución. Se seleccionan aquellos que mejor representan problemas de **reglas de negocio, validaciones, seguridad y funcionalidades críticas**.

## Resumen

Durante las ejecuciones se registraron **22 defectos**.

| Métrica | Resultado |
|---|---:|
| Defectos registrados | 22 |
| Cerrados y corregidos | 21 |
| Abiertos / asignados | 1 |
| Gravedad mayor | 17 |
| Gravedad bloqueo | 4 |
| Gravedad menor | 2 |

## Defectos destacados

### 1. Registro de perfil con datos inválidos

**ID:** 0042693 · **API** · **Prioridad:** Alta · **Gravedad:** Mayor · **Estado:** Cerrado

El sistema permitía registrar un perfil utilizando datos que no cumplían las validaciones esperadas.

**Impacto:** podía generar información incorrecta y afectar la integridad de los datos.

**Resultado:** defecto corregido y verificado mediante una nueva ejecución.

---

### 2. Registro de reservas no disponible

**ID:** 0042666 · **API** · **Prioridad:** Urgente · **Gravedad:** Mayor · **Estado:** Cerrado

No era posible registrar nuevas reservas en el módulo de espacios.

**Impacto:** impedía completar una funcionalidad principal del sistema.

**Resultado:** defecto corregido y flujo de reserva verificado nuevamente.

---

### 3. Bloqueo en validación de solapamiento de reservas

**ID:** 0042667 · **API** · **Prioridad:** Urgente · **Gravedad:** Bloqueo · **Estado:** Cerrado

Se producía un bloqueo al validar el solapamiento de nuevas reservas.

**Impacto:** impedía validar correctamente una regla de negocio crítica relacionada con la disponibilidad de espacios.

**Resultado:** defecto corregido y flujo afectado probado nuevamente.

---

### 4. Inscripciones a actividades canceladas

**ID:** 0042660 · **API** · **Prioridad:** Urgente · **Gravedad:** Mayor · **Estado:** Cerrado

El sistema permitía inscribirse en actividades que ya se encontraban canceladas.

**Impacto:** permitía ejecutar una operación que debía estar restringida según el estado de la actividad.

**Resultado:** regla de negocio corregida y verificada mediante pruebas de regresión.

---

### 5. Vulnerabilidad en el inicio de sesión

**ID:** 0042653 · **API** · **Prioridad:** Alta · **Gravedad:** Mayor · **Estado:** Cerrado

El sistema no bloqueaba al usuario después de cinco intentos de inicio de sesión incorrectos.

**Impacto:** aumentaba la exposición ante posibles intentos de fuerza bruta.

**Resultado:** comportamiento corregido y validado mediante nuevas pruebas.

---

### 6. Filtro de estado incorrecto en listado de perfiles

**ID:** 0043292 · **Web** · **Prioridad:** Normal · **Gravedad:** Mayor · **Estado:** Cerrado

El filtro por estado del listado de perfiles no aplicaba correctamente el criterio seleccionado.

**Impacto:** la información mostrada podía no corresponder con el filtro solicitado.

**Resultado:** defecto corregido y comportamiento verificado.

---

## Cobertura de los defectos destacados

Los defectos seleccionados representan diferentes áreas de testing:

| Área | Ejemplo |
|---|---|
| Validaciones | Datos inválidos |
| Reglas de negocio | Solapamiento e inscripciones |
| Seguridad | Bloqueo de inicio de sesión |
| Funcionalidad crítica | Registro de reservas |
| API REST | Validaciones y reglas de negocio |
| Aplicación Web | Filtros y comportamiento de interfaz |

## Gestión y seguimiento

El flujo utilizado para los defectos fue:

**Detección → Registro → Asignación → Corrección → Verificación → Cierre**

Los registros completos se encuentran disponibles en el archivo CSV exportado desde MantisBT.

**[Ver registro completo de defectos](./bug-mantis.csv)**
