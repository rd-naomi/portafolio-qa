# Ejecuciones de Pruebas

Este directorio contiene la evidencia de las ejecuciones de pruebas realizadas sobre el sistema, incluyendo pruebas manuales de **APIs** y pruebas funcionales sobre la **aplicación web**.

Las ejecuciones se organizaron en dos ciclos principales, correspondientes a las versiones **v1** y **v2**, permitiendo comparar los resultados y verificar la corrección de los defectos encontrados durante el primer ciclo.

## Alcance

Se realizaron pruebas sobre:

- **APIs:** pruebas manuales utilizando Postman.
- **Aplicación Web:** pruebas funcionales y de regresión.
- **Gestión de casos:** TestLink.
- **Gestión y seguimiento de defectos:** Mantis.
- **Consolidación de métricas:** Excel.

Los casos contemplaron escenarios positivos y negativos, incluyendo validaciones de datos, campos obligatorios, permisos, autenticación, registros duplicados y reglas de negocio.

---

## Resumen de ejecuciones

| Métrica | APIs | Web | Total |
|---|---:|---:|---:|
| Casos de prueba | 193 | 195 | 388 |
| Casos ejecutados v1 | 190 | 195 | 385 |
| Pasados v1 | 175 | 192 | 367 |
| Fallados v1 | 15 | 3 | 18 |
| Bloqueados v1 | 3 | 0 | 3 |
| Casos ejecutados v2 | 193 | 195 | 388 |
| Pasados v2 | 192 | 195 | 387 |
| Fallados v2 | 1 | 0 | 1 |
| Bloqueados v2 | 0 | 0 | 0 |

---

## Ciclo v1

Durante el primer ciclo se realizaron las ejecuciones iniciales sobre las APIs y la aplicación web.

### APIs

Se ejecutaron 190 de los 193 casos disponibles:

- **175** casos pasados.
- **15** casos fallados.
- **3** casos bloqueados.

### Web

Se ejecutaron los 195 casos:

- **192** casos pasados.
- **3** casos fallados.
- **0** casos bloqueados.

### Resultado v1

| Métrica | Resultado |
|---|---:|
| Casos planificados | 388 |
| Casos ejecutados | 385 |
| Pass | 367 |
| Fail | 18 |
| Bloqueados | 3 |
| Tasa de ejecución | 99,23% |
| Tasa de éxito | 95,32% |

El resultado se encuentra dentro del criterio **Aceptable** definido para el proyecto, considerando como aceptable una tasa de casos pasados igual o superior al 95%.

---

## Ciclo v2

Luego de los ajustes realizados sobre el sistema, se ejecutó un segundo ciclo para verificar las correcciones y realizar pruebas de regresión.

### APIs

Se ejecutaron nuevamente los 193 casos:

- **192** casos pasados.
- **1** caso fallado.
- **0** casos bloqueados.

### Web

Se ejecutaron los 195 casos:

- **195** casos pasados.
- **0** casos fallados.
- **0** casos bloqueados.

### Resultado v2

| Métrica | Resultado |
|---|---:|
| Casos ejecutados | 388 |
| Pass | 387 |
| Fail | 1 |
| Bloqueados | 0 |
| Tasa de ejecución | 100% |
| Tasa de éxito | 99,74% |

El resultado supera el umbral establecido de **95% de casos pasados** y se aproxima al objetivo definido para un release candidate.

---

## Comparación entre ciclos

| Métrica | v1 | v2 | Evolución |
|---|---:|---:|---:|
| Casos ejecutados | 385 | 388 | +3 |
| Pass | 367 | 387 | +20 |
| Fail | 18 | 1 | -17 |
| Bloqueados | 3 | 0 | -3 |
| Tasa de éxito | 95,32% | 99,74% | +4,42 pp |

La comparación muestra una mejora significativa entre ambos ciclos. Los casos fallados disminuyeron de **18 a 1**, mientras que los casos bloqueados pasaron de **3 a 0**.

---

## Métricas de calidad

Las métricas definidas durante el proyecto permitieron evaluar objetivamente la calidad del sistema y el avance de las pruebas.

### Cobertura de requisitos

**Fórmula:**

`(Requisitos con casos de prueba / Total de requisitos) × 100`

**Objetivo:** ≥ 98% por sprint.

Esta métrica permite verificar que las funcionalidades requeridas tengan casos de prueba asociados.

### Ejecución y aprobación de casos

Se realizó seguimiento de:

- Casos diseñados.
- Casos ejecutados.
- Casos aprobados.
- Eficiencia de ejecución.

**Eficiencia:**

`(Casos aprobados / Casos ejecutados) × 100`

**Objetivos:**

- Casos diseñados: 100% de cobertura de los requisitos del sprint.
- Casos ejecutados: ≥ 95% de los casos planificados.
- Casos aprobados: ≥ 90% de los casos ejecutados.
- Eficiencia: ≥ 85%.

### Cumplimiento de casos de prueba

**Fórmula:**

`(Casos de prueba pasados / Total de casos ejecutados) × 100`

**Objetivos:**

- ≥ 95% por sprint.
- 100% para release candidate.

### Defectos

Se realizó seguimiento de los defectos encontrados por release y su severidad.

**Objetivos:**

- Menos de 10 defectos críticos/altos por release.
- Densidad menor a 0,5 defectos por caso de uso.

### Tiempo de resolución

Se definieron objetivos según la severidad del defecto:

| Severidad | Objetivo de resolución |
|---|---:|
| Crítico | < 24 h |
| Alto | < 48 h |
| Medio | < 5 días |

---

## Criterios de aceptación

Para interpretar los resultados de las ejecuciones se utilizaron los siguientes umbrales:

| Resultado | Criterio |
|---|---:|
| Aceptable | ≥ 95% de casos pasados |
| Riesgo | 85% – 94% de casos pasados |
| Crítico | < 85% de casos pasados |

Los resultados obtenidos en ambos ciclos se encontraron dentro del rango **Aceptable**, con una mejora significativa en el segundo ciclo.

---

## Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| **Postman** | Ejecución y validación manual de APIs |
| **TestLink** | Gestión de casos de prueba y seguimiento de ejecuciones |
| **Mantis** | Registro, seguimiento y gestión de defectos |
| **Excel** | Consolidación y análisis de métricas |

---

## Conclusiones

Las ejecuciones permitieron validar el comportamiento del sistema mediante pruebas manuales sobre APIs y aplicación web, utilizando una estrategia de seguimiento basada en casos de prueba, defectos y métricas de calidad.

La comparación entre **v1 y v2** evidencia una mejora significativa de la estabilidad del sistema:

- Los casos fallados disminuyeron de **18 a 1**.
- Los casos bloqueados disminuyeron de **3 a 0**.
- La tasa de éxito aumentó de **95,32% a 99,74%**.
- Las pruebas web alcanzaron un **100% de casos pasados en v2**.
- Las APIs alcanzaron un **99,48% de casos pasados en v2**.

Esto permitió utilizar el segundo ciclo como una instancia de verificación de las correcciones y de regresión sobre las funcionalidades previamente probadas.

## Evidencias

- [Ejecuciones de APIs](./ejecucion-apis.md)
- [Ejecuciones Web](./ejecucion-web.md)
