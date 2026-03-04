# Documento de Pruebas

## 1. Descripcion del Sistema

La plataforma permite:

1. Registro de estudiantes.
2. Validación de código estudiantil.
3. Inscripción a eventos.

## 2. Requerimientos a Evaluar

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

| ID  | Descripción | Precondiciones | Datos de prueba | Pasos | Resultado Esperado | Estado |
|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| CP01      | Verificar que el código del estudiante cumpla con los requisitos para poder validarlo para el evento, teniendo en cuenta el numero de caracteres, que empiece por la letra "E" y que sus 7 valores restantes sean numéricos  | El estudiante debe estar registrado | El código del estudiante contiene 8 caracteres, empieza por "A" y sus 7 valores restantes son numéricos. | 1. Ingresa el código del estudiante.  2. Se verifica que el código cumpla con los requisitos. 3. Se permite el registro | El sistema verifica que tiene 8 caracteres, que comience con la letra "E" y que sus 7 caracteres restantes son números. | No válido |
| CP02      | Verificar que el código del estudiante cumpla con los requisitos para poder validarlo para el evento, teniendo en cuenta el numero de caracteres, que empiece por la letra "E" y que sus 7 valores restantes sean numéricos  | El estudiante debe estar registrado | El código del estudiante contiene 8 caracteres, empieza por "E" y sus 7 valores restantes son numéricos. | 1. Ingresa el código del estudiante.  2. Se verifica que el código cumpla con los requisitos. 3. Se permite el registro | El sistema verifica que tiene 8 caracteres, que comience con la letra "E" y que sus 7 caracteres restantes son números. | Válido |


## 5. Trazabilidad

## 6. Gestion de Versiones (GitFlow)
