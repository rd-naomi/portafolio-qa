# Defectos Destacados

Selección de defectos relevantes identificados durante las ejecuciones de prueba del sistema de gestión de equipamiento clínico-hospitalario.

Los defectos fueron registrados y gestionados durante las pruebas, considerando prioridad, gravedad, reproducibilidad, módulo afectado, estado y resolución.

La selección busca mostrar diferentes tipos de problemas detectados, especialmente aquellos relacionados con **permisos de usuario, autenticación, reglas de negocio, validaciones de datos y funcionalidades críticas**.

## Resumen

Durante las ejecuciones se registraron **73 defectos**.

| Métrica               | Resultado |
| --------------------- | --------: |
| Defectos registrados  |        73 |
| Cerrados / corregidos |        45 |
| Abiertos / pendientes |        28 |
| Gravedad mayor        |         7 |
| Gravedad bloqueo      |         3 |
| Gravedad menor        |        35 |
| Gravedad ajuste       |        27 |

> Los estados se consideran según el campo **Estado** del registro de defectos.

## Defectos destacados

### 1. Permisos de usuario no implementados en el registro de ubicaciones

**ID:** 0036288 · **Prioridad:** Alta · **Gravedad:** Bloqueo · **Estado:** Resuelta

**Descripción:**
En el módulo de Ubicación, el registro de una nueva ubicación no implementaba el control de permisos correspondiente para los usuarios.

**Impacto:**
Permitía acceder a una funcionalidad sin aplicar correctamente las restricciones definidas para los distintos perfiles de usuario. Se trata de un defecto relevante por su impacto en la **seguridad y control de acceso** de la aplicación.

**Resultado:**
Defecto registrado como resuelto durante las pruebas.

---

### 2. Usuarios eliminados podían ingresar al aplicativo

**ID:** 0036613 · **Prioridad:** Normal · **Gravedad:** Mayor · **Estado:** Nueva

**Descripción:**
Se identificó que un usuario dado de baja podía continuar ingresando al sistema, ya que no se controlaba correctamente el estado del usuario durante el inicio de sesión.

**Impacto:**
Compromete el control de acceso al sistema y puede permitir que usuarios que ya no deberían tener acceso continúen utilizando la aplicación.

**Resultado:**
Defecto registrado y pendiente de corrección.

---

### 3. Permisos de usuario no implementados en el registro de intervenciones

**ID:** 0036140 · **Prioridad:** Alta · **Gravedad:** Bloqueo · **Estado:** Resuelta

**Descripción:**
En el módulo de Intervención, la funcionalidad de registro no aplicaba los permisos de usuario correspondientes.

**Impacto:**
Los controles de acceso definidos para la operación no se estaban aplicando correctamente, afectando una funcionalidad relacionada con la gestión del equipamiento clínico.

**Resultado:**
Defecto registrado como resuelto durante las pruebas.

---

### 4. Permite registrar equipos con número de serie duplicado

**ID:** 0036048 · **Prioridad:** Normal · **Gravedad:** Ajuste · **Estado:** Nueva

**Descripción:**
El sistema permitía registrar un nuevo equipo utilizando un número de serie que ya pertenecía a otro equipo registrado.

**Impacto:**
Puede generar registros duplicados y afectar la **trazabilidad e identificación única del equipamiento**, dificultando posteriormente su gestión y seguimiento.

**Resultado:**
Defecto registrado y pendiente de corrección.

---

### 5. Permite registrar intervenciones con campos obligatorios vacíos

**ID:** 0036592 · **Prioridad:** Normal · **Gravedad:** Menor · **Estado:** Resuelta

**Descripción:**
Durante el registro de una intervención, el sistema permitía completar la operación dejando campos definidos como obligatorios sin información.

**Impacto:**
Puede generar registros incompletos y afectar la calidad e integridad de la información almacenada.

**Resultado:**
Defecto registrado como resuelto durante las pruebas.

---

## Tipos de problemas detectados

Los defectos registrados abarcaron diferentes áreas de calidad, entre ellas:

* Control de permisos y acceso de usuarios.
* Autenticación y gestión del estado de usuarios.
* Validaciones de datos.
* Reglas de negocio.
* Gestión de equipamiento.
* Gestión de ubicaciones y movimientos.
* Gestión de perfiles.
* Gestión de intervenciones.
* Generación y exportación de reportes.
* Mensajes y notificaciones al usuario.
* Filtros y listados.

## Gestión de defectos

El flujo utilizado fue:

**Detección → Registro → Asignación → Corrección → Verificación → Cierre**

Los defectos fueron registrados considerando su **prioridad, gravedad y reproducibilidad**, permitiendo identificar aquellos problemas con mayor impacto sobre la funcionalidad y calidad del sistema.

**[Ver registro completo de defectos](./bugs-mantis.csv)**
