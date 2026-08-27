# Sistema de Gestión Institucional para ASUR

Proyecto académico enfocado en la planificación, diseño, ejecución y análisis de pruebas sobre una plataforma de gestión institucional para la **Asociación de Sordos del Uruguay (ASUR)**.

El trabajo abarcó tanto el **Backend mediante API REST** como la **Aplicación Web**, realizando dos ciclos principales de pruebas correspondientes a las versiones **v1.0 y v2.0**.

---

## Contexto del proyecto

ASUR necesitaba una solución para centralizar y digitalizar procesos que anteriormente se gestionaban de forma manual, como el registro de socios, la organización de actividades y la reserva de espacios.

La plataforma permite gestionar:

* Usuarios, socios y no socios.
* Perfiles y roles de acceso.
* Actividades, inscripciones y cupos.
* Espacios y reservas.
* Reglas de negocio relacionadas con reservas y vencimientos.
* Auditoría de acciones realizadas en el sistema.

El sistema fue desarrollado como proyecto final académico.

---

## Mi rol

Participé de forma integral en las diferentes etapas del proceso de Quality Assurance:

* Análisis de funcionalidades y reglas de negocio.
* Diseño de casos de prueba.
* Aplicación de técnicas de partición de equivalencia y valores límite.
* Ejecución manual de pruebas sobre API REST y aplicación Web.
* Pruebas funcionales, de integración y regresión.
* Validación de reglas de negocio, autorización y seguridad.
* Identificación, documentación y seguimiento de defectos.
* Gestión de casos y trazabilidad mediante TestLink.
* Gestión de defectos mediante MantisBT.
* Análisis y priorización de riesgos.
* Elaboración y análisis de métricas de pruebas.
* Elaboración del informe final de pruebas.

---

## Objetivos

El proceso de pruebas tuvo como principales objetivos:

* Validar el cumplimiento de los requisitos funcionales.
* Verificar el comportamiento de la API REST y la aplicación Web.
* Validar reglas de negocio y permisos según el rol del usuario.
* Detectar y documentar defectos de forma reproducible.
* Verificar las correcciones mediante pruebas de regresión.
* Identificar y priorizar riesgos asociados al producto.
* Medir los resultados de las ejecuciones mediante métricas de calidad.

---

## Stack y ambiente

| Componente             | Tecnología                    |
| ---------------------- | ----------------------------- |
| Backend                | Java + Spring Boot (REST API) |
| Frontend               | React / Next.js               |
| Base de datos          | PostgreSQL                    |
| Contenedores           | Docker                        |
| Cliente de pruebas API | Postman                       |
| Gestión de casos       | TestLink                      |
| Gestión de defectos    | MantisBT                      |
| Ejecución              | Pruebas manuales              |

### Tipos de pruebas

* Pruebas funcionales
* Pruebas de integración
* Pruebas de regresión
* Pruebas de seguridad
* Validación de reglas de negocio
* Pruebas sobre API REST
* Pruebas sobre aplicación Web

---

# Documentación

## Plan de pruebas

Documento que define el enfoque general de testing, alcance, estrategia, métricas, ciclo de vida de las pruebas y defectos, ambientes y criterios de aceptación, rechazo y suspensión.

[📄 Ver Plan de Pruebas](./plan-pruebas/plan-prueba-asur.pdf)

---

## Casos de prueba

Se diseñaron casos para cubrir las principales funcionalidades del sistema, incluyendo autenticación, validaciones, autorización, reglas de negocio, integridad de datos y auditoría.

### Casos destacados

* [🔹 Casos destacados — API](./casos-prueba/casos-api/casos-destacados-apis.md)
* [🔹 Casos destacados — Web](./casos-prueba/casos-web/casos-destacados-web.md)

Además de los casos destacados, se documentaron **388 casos de prueba completos**:

* **193 casos para API REST**
* **195 casos para aplicación Web**

La documentación completa se encuentra disponible en el PDF correspondiente.

[📄 Ver casos de prueba completos de APIs](./casos-prueba/casos-api/casos-prueba-apis.pdf)
[📄 Ver casos de prueba completos de WEB](./casos-prueba/casos-web/casos-prueba-web.pdf)

---

## Diseño de pruebas

Se aplicaron técnicas de diseño de casos de prueba para identificar escenarios representativos y validar diferentes condiciones de entrada.

Entre las técnicas utilizadas se encuentran:

* Partición de equivalencia.
* Análisis de valores límite.

Estas técnicas se aplicaron sobre campos y reglas críticas del sistema, incluyendo fechas, contraseñas, capacidades, precios y otros datos sujetos a restricciones.

[📄 Ver diseño de pruebas](./diseño-pruebas/README.md)

---

## Gestión de defectos

Los defectos encontrados durante las ejecuciones fueron registrados y gestionados mediante **MantisBT**, manteniendo trazabilidad con los casos de prueba registrados en TestLink.

La documentación permite relacionar:

**Caso de prueba → Defecto → Módulo → Estado → Resolución**

[📋 Ver registro de defectos destacados](./defectos/defectos-destacados.md)

[📊 Ver registro completo de defectos](./defectos/bug-mantis.csv)

---

## Ejecución de pruebas

Las pruebas fueron ejecutadas sobre dos versiones principales del sistema:

* **v1.0**
* **v2.0**

Se realizaron ejecuciones independientes para API REST y aplicación Web, registrando resultados por caso de prueba, ciclo, versión, tester y duración.

### Resultados de ejecución

* [📊 Resumen de ejecición](./ejecucion-pruebas/README.md)
* [📊 Resultados — API](./ejecucion-pruebas/results_sistema_asur_apis.csv)
* [📊 Resultados — Web](./ejecucion-pruebas/results_sistema_asur_web.csv)

---

## Gestión de riesgos

Se realizó un análisis de riesgos considerando diferentes categorías asociadas al producto y al proyecto.

La matriz contempla:

* Riesgo.
* Probabilidad.
* Impacto.
* Exposición.
* Estrategia de abordaje.
* Mitigación y contingencia.
* Estado y resultado.

[📊 Ver resumen matriz de riesgos](./gestion-riesgos/resumen-matriz-riesgos.csv)

[📊 Ver matriz de riesgos](./gestion-riesgos/matriz-riesgos-ASUR.csv)

[📄 Ver matriz de riesgos en PDF](./gestion-riesgos/matriz-riesgos-riesgos.pdf)

---

## Informe final de pruebas

El informe final reúne los principales resultados del proceso, incluyendo métricas de ejecución, defectos encontrados por release y conclusiones sobre la calidad del producto.

[📄 Ver informe final de pruebas](./informe-pruebas/informe-final-pruebas-asur.pdf)

---

# Resumen de resultados

| Ciclo    | Casos ejecutados | % Aprobados | Defectos | Bloqueados |
| -------- | ---------------: | ----------: | -------: | ---------: |
| API v1.0 |              193 |       90,7% |       15 |          3 |
| Web v1.0 |              195 |       98,5% |        3 |          0 |
| API v2.0 |              193 |         99% |        1 |          0 |
| Web v2.0 |              195 |        100% |        0 |          0 |

### Evolución entre versiones

La ejecución sobre la versión **v2.0** mostró una reducción significativa de defectos respecto a la primera versión:

* API: **15 defectos → 1 defecto**
* Web: **3 defectos → 0 defectos**

Las ejecuciones de v2.0 incluyeron pruebas de regresión para verificar que las correcciones implementadas no afectaran funcionalidades previamente validadas.

---

# Herramientas utilizadas

| Herramienta          | Uso                                    |
| -------------------- | -------------------------------------- |
| **TestLink**         | Gestión de casos, suites y ejecuciones |
| **MantisBT**         | Registro y seguimiento de defectos     |
| **Postman**          | Pruebas de API REST                    |
| **Excel / CSV**      | Matrices, resultados y métricas        |
| **Docker**           | Ambiente de base de datos              |
| **Pruebas manuales** | Ejecución y validación funcional       |

---

# Repositorios del proyecto

El sistema ASUR fue desarrollado separando sus componentes de Backend y Frontend.

* [💻 Repositorio Backend ASUR](https://github.com/rd-naomi/asur-institutional-management-backend.git)
* [🌐 Repositorio Frontend ASUR](https://github.com/rd-naomi/asur-institutional-management-frontend.git)

---

## Resultado

Este proyecto permitió aplicar un proceso de QA completo sobre una aplicación Web y una API REST, cubriendo desde la planificación y el diseño de pruebas hasta la ejecución, gestión de defectos, análisis de riesgos, regresión y elaboración de métricas e informe final.
