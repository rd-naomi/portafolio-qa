# Diseño de Pruebas

El **diseño de casos de prueba** está orientado a la validación funcional y de reglas de negocio de una aplicación web.

El objetivo de este conjunto de pruebas es demostrar la aplicación de técnicas de diseño de pruebas para identificar escenarios **válidos, inválidos, límites y casos especiales**, buscando maximizar la cobertura y detectar defectos de forma temprana.

---

## Objetivo

Esta carpeta contiene tecnicas para la creacion de casos de prueba diseñados a partir de las reglas de validación de diferentes módulos de la aplicación.

El enfoque está puesto en:

* Validación de reglas de negocio.
* Identificación de entradas válidas e inválidas.
* Análisis de valores límite.
* Particiones de equivalencia.
* Validación de campos obligatorios y opcionales.
* Validación de formatos y enumeraciones.
* Identificación de escenarios negativos y edge cases.
* Documentación de resultados esperados.

> **Enfoque QA:** no se busca únicamente comprobar que el sistema funciona, sino diseñar pruebas que permitan encontrar dónde puede fallar.

---

## Técnicas de Diseño de Pruebas

### Particiones de Equivalencia

Se agrupan los valores de entrada en clases que deberían producir un comportamiento equivalente.

Esto permite reducir la cantidad de casos necesarios manteniendo una cobertura representativa.

**Ejemplo:**

Para un campo con una longitud permitida de 2 a 50 caracteres:

| Partición | Ejemplo       | Resultado esperado |
| --------- | ------------- | ------------------ |
| Inválida  | 1 carácter    | ❌ Rechazado        |
| Válida    | 2 caracteres  | ✅ Aceptado         |
| Válida    | 25 caracteres | ✅ Aceptado         |
| Válida    | 50 caracteres | ✅ Aceptado         |
| Inválida  | 51 caracteres | ❌ Rechazado        |

### Análisis de Valores Límite

Se prueban los valores ubicados en los extremos de los rangos permitidos y sus valores adyacentes.

Se priorizan especialmente:

* Mínimo - 1
* Mínimo
* Valor representativo
* Máximo
* Máximo + 1

Esta técnica permite detectar errores frecuentes relacionados con restricciones de longitud, rangos numéricos y límites de negocio.

---

# Cobertura por Módulo

## 1. Usuarios

Validación de información personal, datos de contacto y credenciales.

| Campo                   | Regla / rango                 | Escenarios prioritarios                              |
| ----------------------- | ----------------------------- | ---------------------------------------------------- |
| **Nombre**              | 2–50 caracteres               | 1, 2, 50 y 51 caracteres                             |
| **Apellido**            | 2–50 caracteres               | 1, 2, 50 y 51 caracteres                             |
| **Email**               | Formato válido                | Formato inválido, vacío, duplicado                   |
| **Contraseña**          | Mín. 8 caracteres             | 7, 8 y más caracteres; mayúscula, minúscula y número |
| **Teléfono**            | 7–15 caracteres               | 6, 7, 15 y 16 caracteres                             |
| **Fecha de nacimiento** | Fecha válida y edad permitida | Fecha futura y límite de edad                        |
| **Cédula**              | Hasta 9 caracteres            | Longitud máxima y excedida                           |

### Enumeraciones

* `tipoDoc`: CI, DNI, PASAPORTE, OTRO
* `usuEstado`: ACTIVO

---

## 2. Tipo de Actividad

Validación de las categorías utilizadas para configurar actividades.

| Campo           | Regla / rango                  | Escenarios prioritarios            |
| --------------- | ------------------------------ | ---------------------------------- |
| **Nombre**      | Hasta 20 caracteres            | Vacío, máximo y máximo + 1         |
| **Descripción** | Opcional, hasta 100 caracteres | Vacío, máximo y excedido           |
| **Estado**      | ACTIVO / INACTIVO              | Valores permitidos y no permitidos |

---

## 3. Actividad

Validación de la planificación y configuración de actividades.

| Campo            | Regla / rango                               | Escenarios prioritarios           |
| ---------------- | ------------------------------------------- | --------------------------------- |
| **Nombre**       | Hasta 100 caracteres                        | Vacío, máximo y excedido          |
| **Descripción**  | Opcional, hasta 255 caracteres              | Vacío, máximo y excedido          |
| **Fecha**        | Formato YYYY-MM-DD                          | Fecha válida, inválida y futura   |
| **Hora**         | Formato HH:MM                               | Formato válido e inválido         |
| **Duración**     | Entero en minutos                           | Valores válidos, cero y negativos |
| **Costo**        | Entero, opcional                            | Vacío, cero y valores inválidos   |
| **Tipo de pago** | EFECTIVO / TRANSFERENCIA / DÉBITO / CRÉDITO | Valores válidos e inválidos       |
| **Estado**       | ACTIVO / INACTIVO                           | Estados permitidos                |

---

## 4. Espacio

Validación de espacios físicos, capacidad y precios.

| Campo               | Regla / rango                          | Escenarios prioritarios        |
| ------------------- | -------------------------------------- | ------------------------------ |
| **Nombre**          | Hasta 20 caracteres                    | Vacío, máximo y excedido       |
| **Capacidad**       | Entero ≥ 1                             | 0, 1 y valores negativos       |
| **Precio socio**    | Decimal, hasta 8 enteros + 2 decimales | 0, máximo permitido y excedido |
| **Precio no socio** | Decimal, hasta 8 enteros + 2 decimales | 0, máximo permitido y excedido |
| **Estado**          | ACTIVO / INACTIVO                      | Estados permitidos e inválidos |

---

# Áreas de Mayor Riesgo

Se priorizaron los campos que presentan mayor cantidad de reglas de validación o mayor impacto ante datos incorrectos.

| Campo                   | Prioridad | Motivo                                |
| ----------------------- | --------- | ------------------------------------- |
| **Contraseña**          | 🔴 Alta   | Múltiples reglas de complejidad       |
| **Email**               | 🔴 Alta   | Formato y unicidad                    |
| **Teléfono**            | 🟡 Media  | Rango y caracteres permitidos         |
| **Fecha de nacimiento** | 🟡 Media  | Validaciones de fecha y edad          |
| **Precios**             | 🟡 Media  | Precisión decimal y límites numéricos |
| **Capacidad**           | 🟡 Media  | Restricción de valores mínimos        |

---

# Cobertura de Pruebas

Las pruebas contemplan diferentes tipos de escenarios:

| Tipo de validación          | Cobertura |
| --------------------------- | --------- |
| Particiones de equivalencia | ✅         |
| Valores límite              | ✅         |
| Valores válidos             | ✅         |
| Valores inválidos           | ✅         |
| Campos obligatorios         | ✅         |
| Campos opcionales           | ✅         |
| Valores nulos               | ✅         |
| Campos vacíos               | ✅         |
| Enumeraciones               | ✅         |
| Formatos                    | ✅         |
| Casos negativos             | ✅         |
| Edge cases                  | ✅         |

---
