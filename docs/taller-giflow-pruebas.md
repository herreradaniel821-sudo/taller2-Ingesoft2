# Documento de Pruebas

## 1. Descripcion del Sistema

Un estudiante podrá inscribirse a un evento solo si:

Está registrado.
El evento tiene cupos disponibles.
No está previamente inscrito.
Si alguna condición no se cumple, el sistema no debe permitir la inscripción.

## 2. Requerimientos a Evaluar
RF-03 Inscripción a Evento
## 3. Tecnicas de Prueba Aplicadas
Tabla de decisión
Justificacion: elegimos esta tecnica por que es la unica que nos permite combinar diferentes escenarios para los cuales el sistema acepta o rechaza la inscripcion al evento. ninguna de las otras tecnicas nos permite hacer esto, salvo los arreglos ortogonales pero en este caso al ser pocos datos podemos permitirnos usar esta tecnica
Cobertura de Tabla: Se han cubierto todas las combinaciones lógicas que resultan en éxito y los fallos individuales de cada condición, logrando una cobertura del 100% de las reglas de decisión factibles.

| Esta registrado | Cupos disponilbes | Está previamente inscrito | Inscipción |
| :-------------: | :---------------: | :-----------------------: | :--------: |
| esta registrado | si hay            | no                        | aceptada   |
| esta registrado | si hay            | si                        | rechazada  |
| esta registrado | no hay            | si                        | rechazada  |
| esta registrado | no hay            | no                        | rechazada  |
| no lo está      | si hay            | si                        | rechazada  |
| no lo está      | si hay            | no                        | rechazada  |
| no lo está      | no hay            | si                        | rechazada  |
| no lo está      | no hay            | no                        | rechazada  |
## 4. Casos de Prueba Diseñados
| ID | Descripcion| Precondiciones| Datos de prueba | Pasos | Resultado esperado | Estado |
| CP05 | Registrar un estudiante al evento | Para inscribirse al evento deberia estar registrado, el evento deberia estar disponible, no debe estár previamente inscrito.| esta registrado, si hay cupos disponibles, no esta previamente inscrito | el sistema evalua las condiciones | el sistema acepta la inscripcion | inscrito al evento
| CP06 | Registrar un estudiante al evento |  Para inscribirse al evento deberia estar registrado, el evento deberia estar disponible, no debe estár previamente inscrito. | No esta registrado, no hay cupos disponibles, si esta previamente inscrito |  el sistema evalua las condiciones | el sistema rechaza la inscripcion | no esta inscrito al evento |
## 5. Trazabilidad

## 6. Gestion de Versiones (GitFlow)
