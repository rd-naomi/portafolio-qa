# Sistema ASUR — Proyecto de QA / Testing

Plan y ejecución de pruebas para la plataforma de gestión institucional de la Asociación de Sordos del Uruguay (ASUR), desarrollada como proyecto final académico (PFT-DZ-GRUPO06-2025).

El sistema gestiona usuarios (socios, no socios y administradores), perfiles y funcionalidades, actividades, espacios y reservas, y auditoría de acciones. Este repositorio documenta el trabajo de **Quality Assurance** realizado sobre el Backend (API REST) y la Aplicación Web, en dos ciclos de ejecución (v1.0 y v2.0).

## Stack y ambiente

| Componente | Tecnología |
|---|---|
| Backend | Java + Spring Boot (REST API) |
| Frontend | React / Next.js |
| Base de datos | PostgreSQL (Docker) |
| Cliente de pruebas API | Postman |
| Gestión de casos | TestLink |
| Gestión de defectos | MantisBT |
| Ejecución | Pruebas manuales |
| Tipo de pruebas | Funcionales, integración, regresión, seguridad, reglas de negocio |

## Contenido de este proyecto

### Plan de pruebas
Enfoque general, alcance, métricas definidas (cobertura, eficiencia, densidad de defectos), ciclo de vida de pruebas y de defectos, ambientes, criterios de aceptación/rechazo/suspensión.
 [`plan-pruebas-asur.pdf`](./plan-pruebas-asur.pdf)

### Casos de prueba destacados
Selección representativa de casos por módulo (autenticación, validaciones, autorización, reglas de negocio, integridad de datos, auditoría), con objetivo, endpoint/escenario y resultado esperado.
- [Casos destacados — API](./asur-api-casos-destacados.md)
- [Casos destacados — Web](./asur-web-casos-destacados.md)

> Además de los casos destacados, se diseñaron y documentaron **todos los casos de prueba como evidencia completa** (193 API + 195 Web).

### Particiones de equivalencia y valores límite
Diseño de casos basado en clases válidas/inválidas y condiciones de borde para los campos críticos del sistema (fechas, contraseñas, capacidades, precios, etc.).
[`particiones-equivalencia-valores-limite.pdf`](./particiones-equivalencia-valores-limite.pdf)

### Registro de bugs
Defectos detectados durante la ejecución, con trazabilidad entre MantisBT y TestLink (caso de prueba ↔ ID de bug ↔ módulo ↔ estado).
[`registro-bugs.md`](./registro-bugs.md)

### Ejecución de pruebas
Resultados detallados por caso, ciclo (v1/v2), fecha, tester y duración.
- [Resultados de ejecución — API](./ejecucion-pruebas/results_sistema_asur_apis.csv)
- [Resultados de ejecución — Web](./ejecucion-pruebas/results_sistema_asur_web.csv)

### Matriz de riesgos
Riesgos identificados (técnicos, de personas, de proyecto, de producto, organizacionales), probabilidad, impacto, exposición, estrategia de mitigación/contingencia y resultado final.
[`matriz-de-riesgos.csv`](./matriz-de-riesgos.csv)

### Informe final de pruebas
Resumen ejecutivo con métricas de cobertura, eficiencia de ejecución (90,7% API v1 / 98,5% Web v1 / 99% API v2 / 100% Web v2), defectos por release y conclusiones sobre la calidad del producto.
[`informe-final-pruebas.pdf`](./informe-final-pruebas.pdf)

## Resumen de resultados

| Ciclo | Casos ejecutados | % Aprobados | Defectos | Bloqueados |
|---|---|---|---|---|
| API v1.0 | 193 | 90,7% | 15 | 3 |
| Web v1.0 | 195 | 98,5% | 3 | 0 |
| API v2.0 | 193 | 99% | 1 | 0 |
| Web v2.0 | 195 | 100% | 0 | 0 |

## Mi rol

Participé de forma integral en todas las etapas del proceso de QA: diseño de casos de prueba (incluyendo particiones de equivalencia y valores límite), ejecución manual sobre API y Web, gestión y trazabilidad de defectos en Mantis/TestLink, análisis de riesgos y elaboración de las métricas e informe final.

---
📁 Ver también: [Repositorio del proyecto (código fuente)](#)
