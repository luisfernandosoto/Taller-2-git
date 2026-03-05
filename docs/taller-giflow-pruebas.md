#Evaluacion de tecnicas de caja negra
##Sistema: Plataforma de gestion de eventos universitarios

Funcionalidades principales
-RF-01 Registro de Estudiante (Edad)
-RF-02 Código de Estudiante
-RF-03 Inscripción a Evento

##RF-01 Registro de Estudiante (Edad)
El sistema debe permitir el registro de estudiantes cuya edad esté entre 16 y 65 años inclusive:
-edad(x) = x >= 16 = permitido
-edad(x) = x < 16 = rechazado
-edad(x) = x > 65 = rechazado
-edad(x) = x <= 65 = permitido

-Tecnica de caja negra utilizada es tecnica de valores limites

-Justificacion de tecnica
El analisis de valores limites se utiliza cuando el requerimiento establece de forma explicita un rango.

-Casos de prueba 
|ID | EDAD | Resultado esperado|
|CP-01| 15 |    Rechazado |
|CP-02| 16 | permitido|
|CP-03| 30 | permitido|
|CP-04| 65 | permitido|
|CP-05| 70 | rechazado|

##Validacion
En este caso los casos de pruebas cubririan:
-Valor inferior fuera del rango
-Limite superior fuera del rango
-Limite superior permitido
-valor inferior dentro del limite 