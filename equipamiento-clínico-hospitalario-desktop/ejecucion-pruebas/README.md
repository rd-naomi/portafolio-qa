# Ejecución de Pruebas

Esta carpeta contiene los resultados de las ejecuciones de prueba realizadas
sobre el Sistema de Gestión de Mantenimiento del Equipamiento
Clínico-Hospitalario.

Las pruebas se ejecutaron en diferentes ciclos, permitiendo validar las
funcionalidades implementadas, verificar correcciones y realizar pruebas de
regresión e integración.

## Ciclos de prueba

Se realizaron cuatro ciclos de ejecución:

| Ciclo | Tipo | Objetivo |
|---|---|---|
| **1.0** | Parcial | Validar las funcionalidades disponibles en una primera versión del sistema. |
| **1.1** | Completo | Validar las funcionalidades implementadas y detectar defectos. |
| **2.1** | Regresión | Verificar correcciones y comprobar que los cambios no afectaran funcionalidades existentes. |
| **3.1** | Integración | Validar el comportamiento del sistema luego de la integración de los módulos con la interfaz. |

## Enfoque de ejecución

Durante los ciclos se utilizaron principalmente:

- Pruebas funcionales.
- Pruebas exploratorias.
- Pruebas de caja negra.
- Pruebas de regresión.
- Pruebas de integración.

Las ejecuciones fueron gestionadas mediante **TestLink**, utilizando una Build
para cada ciclo.

El objetivo fue verificar tanto el comportamiento esperado de las
funcionalidades como la corrección de los defectos detectados en ciclos
anteriores.

## Resultados

Los resultados completos de cada ciclo se encuentran en los archivos CSV
correspondientes.

| Ciclo | Resultados |
|---|---|
| **1.0** | [Resultados de ejecución 1.0](./resultados-1.0.csv) |
| **1.1** | [Resultados de ejecución 1.1](./resultados-1.1.csv) |
| **2.1** | [Resultados de ejecución 2.1](./resultados-2.1.csv) |
| **3.1** | [Resultados de ejecución 3.1](./resultados-3.1.csv) |

> Los nombres de los archivos deben coincidir con los archivos reales del
> repositorio.

## Evolución de las pruebas

Los ciclos permitieron seguir la evolución del sistema:

**1.0 → 1.1 → 2.1 → 3.1**

- **1.0:** primera evaluación parcial del sistema.
- **1.1:** ampliación de la cobertura sobre las funcionalidades disponibles.
- **2.1:** verificación de correcciones y pruebas de regresión.
- **3.1:** validación posterior a la integración de los módulos.

De esta forma, las ejecuciones no se limitaron a comprobar funcionalidades
individuales, sino que también permitieron verificar la estabilidad del sistema
a medida que evolucionaba.

## Evidencia

Los archivos CSV contienen el detalle de las ejecuciones realizadas,
incluyendo el resultado obtenido para cada caso de prueba.

Para consultar el análisis global de las pruebas:

📄 [Informe Final de Pruebas](../informe-de-pruebas/informe-final-pruebas.pdf)
