# Documento de Pruebas

## 1. Descripción del Sistema

La plataforma de Gestión de Eventos Universitarios permite:

1. Registro de estudiantes.
2. Validación de código estudiantil.
3. Inscripción a eventos.

## 2. Requerimientos a Evaluar

- **RF-01** Registro de Estudiante (Edad)
- **RF-02** Validación de Código Estudiantil
- **RF-03** Inscripción a Evento

---

## 3. Técnicas de Prueba Aplicadas

### RF-01 – Registro de Estudiante (Edad)

**Técnica:** Análisis de Valor Límite

**Justificación:** Se aplica esta técnica porque el requerimiento define un rango numérico con un mínimo (16) y un máximo (65), lo que permite identificar los valores límite exactos donde el sistema cambia de comportamiento.

| Caso | Edad Ingresada | Resultado Esperado |
|------|----------------|-------------------|
| VL01 | 15 (Justo debajo del mínimo) | Edad inválida |
| VL02 | 16 (Valor mínimo) | Edad aceptada |
| VL03 | 17 (Justo encima del mínimo) | Edad aceptada |
| VL04 | 64 (Justo debajo del máximo) | Edad aceptada |
| VL05 | 65 (Valor máximo) | Edad aceptada |
| VL06 | 66 (Justo encima del máximo) | Edad inválida |

---

### RF-02 – Validación de Código Estudiantil

**Técnica:** Tabla de Decisión

**Justificación:** Se aplica esta técnica porque el requerimiento combina múltiples condiciones simultáneas (longitud, letra inicial y tipo de caracteres), y la tabla de decisión permite evaluar todas las combinaciones posibles de manera sistemática.

Condiciones evaluadas:
- Condición 1: El código debe tener exactamente 8 caracteres.
- Condición 2: Debe comenzar con la letra "E".
- Condición 3: Los 7 caracteres restantes deben ser numéricos.

| Caso | Descripción | Resultado Esperado |
|------|-------------|-------------------|
| TD01 | 8 caracteres, empieza por "E", 7 restantes numéricos | Aprobado |
| TD02 | 8 caracteres, empieza por "E", 7 restantes NO numéricos | No aprobado |
| TD03 | 8 caracteres, empieza por "A", 7 restantes numéricos | No aprobado |
| TD04 | 7 caracteres, empieza por "E", 6 restantes numéricos | No aprobado |
| TD05 | 9 caracteres, empieza por "E", 8 restantes numéricos | No aprobado |
| TD06 | 5 caracteres, empieza por "T", 4 restantes numéricos | No aprobado |

---

### RF-03 – Inscripción a Evento

**Técnica:** Tabla de Decisión

**Justificación:** Se aplica esta técnica porque es la única que permite combinar los diferentes escenarios en los cuales el sistema acepta o rechaza la inscripción al evento, evaluando las tres condiciones de forma conjunta y cubriendo el 100% de las reglas de decisión factibles.

| Está registrado | Cupos disponibles | Está previamente inscrito | Inscripción |
|:--------------:|:-----------------:|:-------------------------:|:-----------:|
| Sí | Sí | No | Aceptada |
| Sí | Sí | Sí | Rechazada |
| Sí | No | No | Rechazada |
| Sí | No | Sí | Rechazada |
| No | Sí | No | Rechazada |
| No | Sí | Sí | Rechazada |
| No | No | No | Rechazada |
| No | No | Sí | Rechazada |

---

## 4. Casos de Prueba Diseñados

### RF-01 – Registro de Estudiante (Edad)

| ID   | Descripción | Precondiciones | Datos de prueba | Pasos | Resultado Esperado | Estado |
|------|-------------|----------------|-----------------|-------|--------------------|--------|
| CP01 | Verificar que el sistema acepte una edad dentro del rango permitido | El usuario debe ingresar su edad | 18 años | 1. Ingresa la edad  2. Completa el registro  3. Envía el registro | El sistema valida la edad y permite completar el registro | Pendiente |
| CP02 | Verificar que el sistema rechace una edad fuera del rango permitido | El usuario debe ingresar su edad | 14 años | 1. Ingresa la edad  2. Completa el registro  3. Envía el registro | El sistema detecta la edad inválida y cancela el registro | Pendiente |

---

### RF-02 – Validación de Código Estudiantil

| ID   | Descripción | Precondiciones | Datos de prueba | Pasos | Resultado Esperado | Estado |
|------|-------------|----------------|-----------------|-------|--------------------|--------|
| CP03 | Verificar que el sistema rechace un código que no comience con "E" | El estudiante debe estar registrado | 8 caracteres, empieza por "A", 7 restantes numéricos (ej: A1234567) | 1. Ingresa el código  2. El sistema verifica los requisitos  3. El sistema emite resultado | El sistema detecta que el código no comienza con "E" y lo rechaza | No válido |
| CP04 | Verificar que el sistema acepte un código que cumple todos los requisitos | El estudiante debe estar registrado | 8 caracteres, empieza por "E", 7 restantes numéricos (ej: E1234567) | 1. Ingresa el código  2. El sistema verifica los requisitos  3. El sistema emite resultado | El sistema valida que tiene 8 caracteres, comienza con "E" y los 7 restantes son numéricos | Válido |

---

### RF-03 – Inscripción a Evento

| ID   | Descripción | Precondiciones | Datos de prueba | Pasos | Resultado Esperado | Estado |
|------|-------------|----------------|-----------------|-------|--------------------|--------|
| CP05 | Verificar que el sistema acepte la inscripción cuando todas las condiciones se cumplen | El estudiante debe estar registrado, el evento debe tener cupos y el estudiante no debe estar inscrito previamente | Registrado: Sí, Cupos: Sí, Inscrito previamente: No | El sistema evalúa las tres condiciones | El sistema acepta la inscripción | Inscrito al evento |
| CP06 | Verificar que el sistema rechace la inscripción cuando alguna condición no se cumple | N/A | Registrado: No, Cupos: No, Inscrito previamente: Sí | El sistema evalúa las tres condiciones | El sistema rechaza la inscripción | No inscrito al evento |

---

## 5. Trazabilidad

| Requerimiento | Técnica Aplicada | Casos Asociados |
|---------------|-----------------|-----------------|
| RF-01 | Análisis de Valor Límite | CP01, CP02 |
| RF-02 | Tabla de Decisión | CP03, CP04 |
| RF-03 | Tabla de Decisión | CP05, CP06 |

---
