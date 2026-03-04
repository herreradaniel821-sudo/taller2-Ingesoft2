# Documento de Pruebas

## 1. Descripción del Sistema

La plataforma permite:

1. Registro de estudiantes.
2. Validación de código estudiantil.
3. Inscripción a eventos.

## 2. Requerimientos a Evaluar

## RF01 Registro de Estudiante (Edad)
El sistema debe permitir el registro de estudiantes cuya edad esté entre 16 y 65 años inclusive.

## 3. Técnicas de Prueba Aplicadas
## RF01 Registro de Estudiante (Edad)
## Análisis de Valor Límite

Identificamos que podemos aplicar la técnica del valor límite, ya que este requerimiento nos da la edad mínima y máxima a evaluar.

| Caso | Edad Ingresada | Resultado esperado |
|------|----------------|-------------------|
| VL01 | 15 (Justo debajo del mínimo) | Edad inválida |
| VL02 | 16 (Valor mínimo) | Edad aceptada |
| VL03 | 17 (Justo encima del mínimo) | Edad aceptada |
| VL04 | 64 (Justo debajo del máximo) | Edad aceptada |
| VL05 | 65 (Valor máximo) | Edad aceptada |
| VL06 | 66 (Justo encima del máximo) | Edad inválida |
2. Validación de código estudiantil.

## 3. Tecnicas de Prueba Aplicadas

Tabla de Desición

Prueba de cobertura: Coincidimos en que esta fue la mejor **técnica** de caja negra debido a que se utilizan diferentes condiciones para validar un resultado. La que mejor se acomoda a esta descripción es la **técnica de tabla de decisión**, debido a que esta nos permite evaluarla en sus diferentes combinaciones posibles.

- Condición 1: El código debe tener 8 caracteres.
- Condición 2: Debe de comenzar con la letra "E".
- Condición 3: Los 7 caracteres restantes deben ser numéricos. 

Combinaciones posibles:

| Caso  | Condiciones Usuario | Resultado Esperado |
|--------------|--------------|--------------|
| TD01       | El código del estudiante contiene 8 caracteres, empieza por "E" y sus 7 valores restantes son numéricos.       | Aprobado      |
| TD02      | El código del estudiante contiene 8 caracteres, empieza por "E" y sus 7 valores restantes NO son numéricos.     | No aprobado  |
| TD03      | El código del estudiante contiene 8 caracteres, empieza por "A" y sus 7 valores restantes son numéricos.     | No aprobado     |
| TD04      | El código del estudiante contiene 7 caracteres, empieza por "E" y sus 6 valores restantes son numéricos.      | No aprobado   |
| TD05      | El código del estudiante contiene 9 caracteres, empieza por "E" y sus 8 valores restantes son numéricos.     | No aprobado|
| TD06      | El código del estudiante contiene 5 caracteres, empieza por "T" y sus 4 valores restantes son numéricos.      | No aprobado      |

## 4. Casos de Prueba Diseñados
## RF01 Registro de Estudiante (Edad)

## Casos de Prueba

| ID   | Descripción                                                             | Precondiciones                     | Datos de prueba | Pasos                                                                 | Resultado esperado                                                        | Estado    |
|------|-------------------------------------------------------------------------|------------------------------------|-----------------|----------------------------------------------------------------------|----------------------------------------------------------------------------|-----------|
| CP01 | Verificar que el sistema acepte una edad que cumpla con los requisitos | El usuario debe ingresar su edad   | 18 años         | 1. Ingresa la edad <br> 2. Completa el registro <br> 3. Envía registro | El sistema valida la edad y permite completar el registro                 | Pendiente |
| CP02 | Verificar que el sistema rechace una edad fuera del rango permitido    | El usuario debe ingresar su edad   | 14 años         | 1. Ingresa la edad <br> 2. Completa el registro <br> 3. Envía registro | El sistema detecta edad inválida y cancela el registro                    | Pendiente |

El uso de la técnica de valor límite fue el más adecuado en este caso, ya que valida una cobertura total de todos los posibles casos de prueba.

| ID  | Descripción | Precondiciones | Datos de prueba | Pasos | Resultado Esperado | Estado |
|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| CP01      | Verificar que el código del estudiante cumpla con los requisitos para poder validarlo para el evento, teniendo en cuenta el numero de caracteres, que empiece por la letra "E" y que sus 7 valores restantes sean numéricos  | El estudiante debe estar registrado | El código del estudiante contiene 8 caracteres, empieza por "A" y sus 7 valores restantes son numéricos. | 1. Ingresa el código del estudiante.  2. Se verifica que el código cumpla con los requisitos. 3. Se permite el registro | El sistema verifica que tiene 8 caracteres, que comience con la letra "E" y que sus 7 caracteres restantes son números. | No válido |
| CP02      | Verificar que el código del estudiante cumpla con los requisitos para poder validarlo para el evento, teniendo en cuenta el numero de caracteres, que empiece por la letra "E" y que sus 7 valores restantes sean numéricos  | El estudiante debe estar registrado | El código del estudiante contiene 8 caracteres, empieza por "E" y sus 7 valores restantes son numéricos. | 1. Ingresa el código del estudiante.  2. Se verifica que el código cumpla con los requisitos. 3. Se permite el registro | El sistema verifica que tiene 8 caracteres, que comience con la letra "E" y que sus 7 caracteres restantes son números. | Válido |


## 5. Trazabilidad

## 6. Gestión de Versiones (GitFlow)

