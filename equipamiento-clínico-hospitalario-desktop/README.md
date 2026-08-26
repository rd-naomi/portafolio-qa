# Sistema de Gestión de Mantenimiento del Equipamiento Clínico-Hospitalario

Proyecto académico de desarrollo de software y Quality Assurance orientado a la gestión del mantenimiento de equipamiento clínico-hospitalario.

El proyecto abarcó tanto el **desarrollo de la aplicación** como la **planificación, diseño, ejecución y seguimiento de pruebas de software**, permitiendo aplicar un proceso completo de desarrollo y aseguramiento de calidad.

---

## Contexto del proyecto

El sistema fue desarrollado para gestionar información relacionada con equipamiento clínico-hospitalario y su mantenimiento.

La solución permite gestionar diferentes entidades y procesos del sistema, incluyendo:

- Usuarios.
- Perfiles.
- Equipamiento.
- Ubicaciones.
- Intervenciones.
- Tipos de intervención.
- Estados y bajas de registros.
- Búsqueda y filtrado de información.
- Registro de mantenimiento del equipamiento.

El proyecto fue desarrollado en equipo como parte de una instancia académica de desarrollo y testing.

---

## Participación en el proyecto

Mi participación abarcó diferentes etapas del proyecto, incluyendo tanto actividades de desarrollo como de Quality Assurance.

### Desarrollo

- Participación en el desarrollo del sistema.
- Implementación y/o integración de funcionalidades.
- Trabajo colaborativo sobre los diferentes módulos.
- Validación funcional de las funcionalidades desarrolladas.

### Quality Assurance

- Análisis de requisitos y reglas de negocio.
- Diseño de casos de prueba.
- Aplicación de técnicas de caja negra.
- Partición de equivalencia.
- Tablas de decisión.
- Ejecución manual de pruebas.
- Pruebas funcionales.
- Pruebas exploratorias.
- Pruebas de regresión.
- Pruebas de integración.
- Identificación y documentación de defectos.
- Seguimiento de correcciones.
- Verificación de defectos corregidos.
- Gestión de casos mediante TestLink.
- Gestión de defectos mediante MantisBT.
- Elaboración de métricas y resultados de pruebas.
- Elaboración del informe final de pruebas.

---

# Arquitectura y tecnologías

El sistema fue desarrollado utilizando una arquitectura basada en aplicación de escritorio, servidor de aplicaciones y base de datos.

| Componente | Tecnología |
|---|---|
| Aplicación | Java |
| Servidor de aplicaciones | WildFly 28.0.1.Final |
| Base de datos | Oracle |
| Sistema operativo | Windows 10 / Windows 11 |
| Gestión de pruebas | TestLink |
| Gestión de defectos | MantisBT |
| Documentación y análisis | Excel / PDF |

---

# Módulos del sistema

El alcance funcional incluyó los siguientes módulos:

- **Gestión de Usuarios**
- **Gestión de Perfiles**
- **Gestión de Intervenciones**
- **Gestión de Equipos**
- **Gestión de Ubicaciones**
- **Gestión de Tipos de Intervención**

Estos módulos fueron desarrollados y posteriormente incluidos dentro del proceso de pruebas.

---

# Proceso de Quality Assurance

El proceso de pruebas se desarrolló de forma incremental a medida que evolucionaba el sistema.

El flujo general fue:

**Análisis → Diseño → Desarrollo → Ejecución → Registro de defectos → Corrección → Regresión → Integración → Validación**

Las pruebas se organizaron en diferentes ciclos asociados a las versiones del sistema.

---

## Documentación de QA

### Planificación de pruebas

La documentación del proceso de pruebas define el alcance, estrategia, ambiente, datos de prueba, ciclos y herramientas utilizadas.

[📄 Ver documentación del proceso de pruebas](./informe-final-pruebas/)

---

## Diseño de pruebas

Se utilizaron técnicas de diseño de pruebas de caja negra para obtener escenarios representativos y cubrir diferentes condiciones de entrada.

Las principales técnicas utilizadas fueron:

- **Partición de equivalencia**
- **Tabla de decisiones**

La partición de equivalencia permitió identificar clases válidas e inválidas para los diferentes campos del sistema.

Las tablas de decisión permitieron analizar combinaciones de condiciones, especialmente en funcionalidades de búsqueda y filtrado.

[📄 Ver diseño de pruebas](./diseno-de-pruebas/README.md)

---

## Casos de prueba

Los casos de prueba fueron diseñados a partir de las funcionalidades del sistema y de las técnicas de diseño aplicadas.

Se contemplaron escenarios:

- Positivos.
- Negativos.
- Datos inválidos.
- Campos obligatorios.
- Límites y rangos.
- Reglas de negocio.
- Búsquedas y filtros.
- Integración entre módulos.
- Regresión de funcionalidades corregidas.

[📄 Ver casos de prueba](./casos-de-prueba/casos-prueba-destacados.md)

---

## Ejecución de pruebas

Las ejecuciones se realizaron sobre diferentes versiones del sistema, permitiendo evaluar su evolución durante el desarrollo.

Se realizaron los siguientes ciclos:

| Versión | Tipo de ejecución | Objetivo |
|---|---|---|
| **1.0** | Parcial | Validar las funcionalidades disponibles inicialmente |
| **1.1** | Completa | Validar la evolución y correcciones realizadas |
| **2.1** | Regresión | Verificar correcciones y detectar regresiones |
| **3.1** | Integración | Validar el sistema luego de la integración de módulos |

Los resultados de cada ejecución fueron registrados y analizados para identificar casos aprobados, fallidos y bloqueados.

[📄 Ver resultados de las ejecuciones](./ejecucion-pruebas/README.md)

---

## Gestión de defectos

Los defectos detectados durante las ejecuciones fueron registrados y gestionados mediante **MantisBT**.

Para cada incidencia se mantuvo información relacionada con:

- Identificador.
- Prioridad.
- Gravedad.
- Reproducibilidad.
- Módulo afectado.
- Estado.
- Resolución.
- Versión en la que fue corregido.

El seguimiento permitió mantener la trazabilidad desde la detección hasta la verificación de la corrección.

**Flujo utilizado:**

**Detección → Registro → Asignación → Corrección → Verificación → Cierre**

[📄 Ver defectos destacados](./defectos/defectos-destacados.md)

---

# Ambiente de pruebas

Las pruebas fueron realizadas en un ambiente configurado específicamente para la validación del sistema.

### Infraestructura

- Windows 10 / Windows 11.
- Oracle Database.
- WildFly 28.0.1.Final.

### Datos de prueba

Se utilizaron datos preparados mediante scripts para generar escenarios realistas y permitir la validación de dependencias entre módulos.

También se contemplaron:

- Datos válidos e inválidos.
- Valores límite.
- Campos obligatorios.
- Registros relacionados.
- Escenarios negativos.

---

# Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| **TestLink** | Gestión y ejecución de casos de prueba |
| **MantisBT** | Registro y seguimiento de defectos |
| **Excel** | Matrices, resultados y análisis |
| **Oracle** | Persistencia de datos |
| **WildFly** | Servidor de aplicaciones |

---

# Informe final

El proceso completo quedó documentado en un informe final que reúne:

- Alcance.
- Ciclos de prueba.
- Ambiente.
- Datos de prueba.
- Herramientas.
- Resultados.
- Conclusiones.

[📄 Ver informe final de pruebas](./informe-de-pruebas/informe-final-pruebas.pdf)

---

# Resultado del proyecto

El proyecto permitió recorrer un proceso completo de desarrollo y aseguramiento de calidad, desde la construcción de las funcionalidades hasta su validación mediante diferentes ciclos de pruebas.

La combinación de **desarrollo + QA** permitió detectar problemas funcionales, validar reglas de negocio, comprobar correcciones y realizar pruebas de regresión e integración a medida que evolucionaba el sistema.

---

# Repositorios del proyecto

* [💻 Repositorio proyecto](https://github.com/rd-naomi/)

---

## Resumen

**Tipo de proyecto:** Desarrollo de software + Quality Assurance  
**Aplicación:** Sistema de gestión de mantenimiento de equipamiento clínico-hospitalario  
**Testing:** Manual  
**Gestión de casos:** TestLink  
**Gestión de defectos:** MantisBT  
**Técnicas:** Partición de equivalencia y tablas de decisión  
**Ciclos:** 1.0 · 1.1 · 2.1 · 3.1
