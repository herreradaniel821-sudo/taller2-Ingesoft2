# Documento de Pruebas

## 1. Descripción del Sistema

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

## 4. Casos de Prueba Diseñados
## RF01 Registro de Estudiante (Edad)

## Casos de Prueba

| ID   | Descripción                                                             | Precondiciones                     | Datos de prueba | Pasos                                                                 | Resultado esperado                                                        | Estado    |
|------|-------------------------------------------------------------------------|------------------------------------|-----------------|----------------------------------------------------------------------|----------------------------------------------------------------------------|-----------|
| CP01 | Verificar que el sistema acepte una edad que cumpla con los requisitos | El usuario debe ingresar su edad   | 18 años         | 1. Ingresa la edad <br> 2. Completa el registro <br> 3. Envía registro | El sistema valida la edad y permite completar el registro                 | Pendiente |
| CP02 | Verificar que el sistema rechace una edad fuera del rango permitido    | El usuario debe ingresar su edad   | 14 años         | 1. Ingresa la edad <br> 2. Completa el registro <br> 3. Envía registro | El sistema detecta edad inválida y cancela el registro                    | Pendiente |

El uso de la técnica de valor límite fue el más adecuado en este caso, ya que valida una cobertura total de todos los posibles casos de prueba.

## 5. Trazabilidad

## 6. Gestión de Versiones (GitFlow)

