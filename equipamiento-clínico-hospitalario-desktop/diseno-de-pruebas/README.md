# Técnicas de Diseño de Casos de Prueba

Artefactos utilizados para el diseño de casos de prueba del sistema de gestión de equipamiento clínico-hospitalario.

Se aplicaron técnicas de **caja negra** para identificar escenarios representativos a partir de reglas de validación, criterios de búsqueda y combinaciones de condiciones.

### Técnicas utilizadas

- **Partición de Equivalencia**
- **Tabla de Decisiones**

---

## Partición de Equivalencia

Se identificaron clases de equivalencia **válidas e inválidas** para seleccionar datos representativos y evitar pruebas redundantes.

Se consideraron principalmente:

- Longitudes y formatos.
- Rangos numéricos y de fechas.
- Valores permitidos y no permitidos.
- Campos obligatorios y opcionales.
- Valores vacíos o inválidos.

### Aplicación por módulo

| Módulo | Principales entradas analizadas |
|---|---|
| **Usuario** | Nombre, apellido, cédula, teléfono, email, contraseña, tipo y estado |
| **Perfil** | Nombre y estado |
| **Intervenciones** | Fecha/hora, tipo, motivo, equipamiento, observaciones y filtros |
| **Equipo** | Nombre, tipo, marca, modelo, número de serie, garantía, proveedor, fechas y ubicación |
| **Ubicaciones** | Institución, sector, nombre, número, piso, cama y fechas |
| **Tipo de Intervención** | Tipo y estado |

---

## Tabla de Decisiones

Se utilizaron tablas de decisión para analizar funcionalidades cuyo resultado depende de **una o varias condiciones combinadas**, principalmente en búsquedas y filtros.

Se contemplaron escenarios como:

- Sin filtros.
- Un único criterio.
- Combinación de filtros.
- Filtros por estado, fecha o tipo.
- Combinaciones incompatibles.
- Sin resultados.
- Un resultado.
- Múltiples resultados.

### Módulos analizados

- **Ubicaciones**
- **Equipo**
- **Usuario**
- **Tipo de Intervención**
- **Perfil**
- **Intervenciones**

Cada tabla relaciona las **condiciones de entrada** con las **acciones esperadas**, permitiendo identificar escenarios positivos y negativos.

---

## Resultado

La combinación de ambas técnicas permitió cubrir dos dimensiones del comportamiento del sistema:

**Partición de Equivalencia**  
→ Validación de diferentes clases de datos de entrada.

**Tabla de Decisiones**  
→ Validación de combinaciones de condiciones y criterios.

Los escenarios identificados mediante estas técnicas fueron utilizados como base para la elaboración de los casos de prueba y su posterior ejecución.

## Evidencia

- [📄 Partición de Equivalencia](./tecnicas-diseño-casos-prueba.pdf)
- [📄 Tabla de Decisiones](./tabla-de-decisiones.pdf)
