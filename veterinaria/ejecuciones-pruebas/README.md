# Ejecución de Pruebas

Esta carpeta contiene los resultados de las ejecuciones de prueba realizadas
sobre el **Sistema de Gestión de Veterinaria**.

Las pruebas fueron gestionadas mediante **TestLink** y permitieron validar las
funcionalidades principales del sistema, identificar defectos, verificar
correcciones y realizar una segunda ejecución de regresión.

## Ciclos de prueba

Se realizaron dos ciclos principales de ejecución:

| Ciclo   | Tipo      | Objetivo                                                                                                                                       |
| ------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **1** | Inicial   | Validar las funcionalidades principales del sistema, detectar defectos y comprobar el comportamiento frente a los requerimientos establecidos. |
| **2** | Regresión | Reejecutar los casos del primer ciclo, verificar correcciones y ampliar la cobertura mediante nuevos casos de prueba.                          |

## Alcance de las pruebas

Las ejecuciones abarcaron los principales módulos del Sistema de Gestión de
Veterinaria:

* **Módulo Cliente**

  * Alta de clientes.
  * Cancelación del alta.
  * Validación de datos.
  * Campos obligatorios.
  * Mensajes y textos de la interfaz.

* **Módulo Mascota**

  * Alta de mascotas.
  * Cancelación del alta.
  * Validación de número de patente, nombre y edad.
  * Selección de cliente y tipo de mascota.
  * Listado y búsqueda de mascotas.
  * Mensajes y textos de la interfaz.

* **Módulo Veterinario**

  * Alta de veterinarios.
  * Cancelación del alta.
  * Validación de código, nombre y cédula.
  * Selección de especialidad.
  * Mensajes y textos de la interfaz.

* **Módulo Consulta**

  * Registro de consultas.
  * Cancelación del registro.
  * Validación del número de patente y fecha.
  * Listado y filtrado de consultas.
  * Mensajes y textos de la interfaz.

## Enfoque de ejecución

Durante las ejecuciones se utilizaron principalmente:

* Pruebas funcionales.
* Pruebas exploratorias.
* Pruebas de caja negra.
* Pruebas de regresión.
* Pruebas de validación de datos.
* Pruebas de interfaz y mensajes.

Los casos de prueba fueron gestionados y ejecutados mediante **TestLink**,
registrando el resultado obtenido para cada caso.

Los defectos identificados durante las ejecuciones fueron documentados y
gestionados mediante **Mantis**.

## Criterios de evaluación

Un caso de prueba se consideró **fallido** cuando el resultado obtenido no
coincidía con el resultado esperado definido para el caso, incluso cuando la
funcionalidad principal pudiera ejecutarse correctamente.

Por ejemplo, si el sistema rechazaba correctamente un dato inválido pero
mostraba un mensaje incorrecto o insuficiente para informar al usuario, el
caso se consideraba fallido.

También se consideró fallido un caso compuesto por varios pasos cuando uno o
más de sus pasos no cumplían con el comportamiento esperado.

Los casos que no pudieron ejecutarse debido a problemas que impedían acceder
a la funcionalidad correspondiente fueron considerados **bloqueados**.

## Resultados

Los resultados completos de cada ciclo se encuentran en los archivos CSV
correspondientes.

| Ciclo   | Resultados                                          |
| ------- | --------------------------------------------------- |
| **1.0** | [Resultados de ejecución 1.0](./resultados-v1.csv) |
| **1.1** | [Resultados de ejecución 1.1](./resultados-v2.csv) |

## Ciclo 1

Durante el primer ciclo se realizaron pruebas iniciales sobre las
funcionalidades disponibles del sistema.

Se ejecutaron **31 casos de prueba**, distribuidos entre los módulos de
Cliente, Mascota, Veterinario y Consulta.

Los resultados permitieron identificar:

* Casos ejecutados correctamente.
* Casos con resultados diferentes a los esperados.
* Defectos funcionales.
* Problemas relacionados con mensajes y validaciones.
* Casos bloqueados por problemas que impedían continuar la ejecución.

Entre los principales problemas identificados se encontraron validaciones
incorrectas, mensajes de error poco específicos, problemas en la cancelación
de operaciones y dificultades para acceder a determinadas funcionalidades.

Los casos bloqueados fueron documentados para permitir su posterior análisis
y resolución.

## Ciclo 2

El segundo ciclo tuvo como objetivo verificar la evolución del sistema y
comprobar el comportamiento de las funcionalidades luego de los cambios
realizados.

Se reejecutaron los casos del ciclo anterior como parte de las pruebas de
**regresión** y se incorporaron nuevos casos para ampliar la cobertura.

Durante este ciclo se observaron mejoras en algunas funcionalidades, mientras
que determinados defectos continuaron presentes.

Entre los problemas detectados se encontraron:

* Validaciones que permitían ingresar datos inválidos.
* Mensajes de error que no coincidían con el problema real.
* Mensajes de interfaz con errores lingüísticos.
* Comportamientos incorrectos durante la cancelación de registros.
* Diferencias entre el resultado funcional y el mensaje mostrado al usuario.
* Problemas en el registro de veterinarios con datos inválidos.

Los resultados de este ciclo permitieron comparar el comportamiento del
sistema respecto de la primera ejecución y evaluar la efectividad de las
correcciones realizadas.

## Evolución de las pruebas

La evolución de las ejecuciones puede representarse de la siguiente manera:

**1 → 2**

* **1:** ejecución inicial, identificación de defectos y casos bloqueados.
* **2:** regresión de los casos existentes, verificación de cambios y
  ampliación de la cobertura.

La comparación entre ambos ciclos permitió determinar qué funcionalidades
mejoraron, cuáles mantuvieron sus defectos y qué nuevos problemas fueron
detectados durante la regresión.

## Herramientas utilizadas

### TestLink

Utilizado para:

* Gestión de casos de prueba.
* Organización de suites.
* Creación de Builds.
* Ejecución de casos.
* Registro de resultados.
* Seguimiento de las ejecuciones.

### Mantis

Utilizado para:

* Registro de defectos.
* Documentación de incidencias.
* Seguimiento de los problemas encontrados durante las pruebas.

## Evidencia

Los archivos CSV contienen el detalle de las ejecuciones realizadas,
incluyendo:

* Suite de pruebas.
* Caso de prueba.
* Prioridad.
* Build evaluada.
* Fecha de ejecución.
* Resultado.
* Observaciones.
* Duración de la ejecución.

Para consultar el análisis completo de las pruebas:

📄 [Informe Final de Pruebas](../informe-de-pruebas/informe-final-pruebas.pdf)

