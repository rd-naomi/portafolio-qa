# Diseño de Pruebas

Aplicación de técnicas de diseño de casos de prueba para validar **reglas de negocio, datos de entrada y restricciones funcionales** del sistema ASUR.

Las técnicas utilizadas fueron:

* **Partición de equivalencia**
* **Análisis de valores límite**

El diseño se enfocó especialmente en campos con restricciones de formato, longitud, rangos, valores permitidos y reglas de negocio.

---

## Técnicas aplicadas

### Partición de equivalencia

Se identificaron clases de datos **válidos e inválidos** para reducir casos redundantes y mantener una cobertura representativa.

Algunos ejemplos aplicados al sistema:

| Campo             | Clases / escenarios considerados          |
| ----------------- | ----------------------------------------- |
| Nombre / Apellido | Longitud válida e inválida                |
| Email             | Formato válido, inválido y duplicado      |
| Contraseña        | Longitud y requisitos de complejidad      |
| Teléfono          | Longitud y formato                        |
| Estado            | Valores permitidos y no permitidos        |
| Tipo de pago      | Valores definidos por la regla de negocio |

### Análisis de valores límite

Se evaluaron valores ubicados en los límites de las restricciones definidas por el sistema.

Ejemplos:

| Campo             | Límites evaluados                                 |
| ----------------- | ------------------------------------------------- |
| Nombre / Apellido | Mínimo, máximo y valores fuera de rango           |
| Contraseña        | Mínimo permitido y valores inferiores             |
| Teléfono          | Mínimo, máximo y valores fuera de rango           |
| Capacidad         | 0, mínimo permitido y valores negativos           |
| Precios           | 0, máximo permitido y valores excedidos           |
| Fechas            | Límites relacionados con edad y fechas permitidas |

---

## Aplicación por módulo

### Usuarios

Se analizaron principalmente:

* Datos personales.
* Email y unicidad.
* Contraseña y complejidad.
* Teléfono.
* Fecha de nacimiento.
* Cédula.
* Estados y tipos de documento.

### Tipo de Actividad

Se evaluaron:

* Longitud de nombre y descripción.
* Campos obligatorios y opcionales.
* Estados permitidos.

### Actividad

Se analizaron:

* Nombre y descripción.
* Fecha y hora.
* Duración.
* Costo.
* Tipo de pago.
* Estado.

### Espacio

Se evaluaron:

* Nombre.
* Capacidad.
* Precio para socios y no socios.
* Estado.

---

## Áreas priorizadas

Se dio mayor atención a los campos con mayor cantidad de restricciones o impacto potencial sobre el funcionamiento del sistema.

| Campo               | Prioridad | Motivo                              |
| ------------------- | --------- | ----------------------------------- |
| Contraseña          | 🔴 Alta   | Reglas de complejidad y seguridad   |
| Email               | 🔴 Alta   | Formato y unicidad                  |
| Teléfono            | 🟡 Media  | Restricciones de longitud y formato |
| Fecha de nacimiento | 🟡 Media  | Validaciones de fecha y edad        |
| Precios             | 🟡 Media  | Rangos y precisión decimal          |
| Capacidad           | 🟡 Media  | Restricción de valor mínimo         |

---

## Evidencia

La documentación completa contiene el análisis de las reglas, particiones identificadas y valores límite considerados para los diferentes campos del sistema.

**Documento completo:**
[📄 Particiones de Equivalencia](./particiones-equivalencia.pdf)
[📄 Valores Limite](./valores-limite.png)
