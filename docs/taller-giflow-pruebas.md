#Evaluacion de tecnicas de caja negra
##Sistema: Plataforma de gestion de eventos universitarios

Funcionalidades principales
-RF-01 Registro de Estudiante (Edad)
-RF-02 Código de Estudiante
-RF-03 Inscripción a Evento

##RF-01 Registro de Estudiante (Edad)
El sistema debe permitir el registro de estudiantes cuya edad esté entre 16 y 65 años inclusive:
15
16
17
64
65
66

-Tecnica de caja negra utilizada es tecnica de valores limites

-Justificacion de tecnica
El analisis de valores limites se utiliza cuando el requerimiento establece de forma explicita un rango.

-Casos de prueba 
|ID | EDAD | Resultado esperado|
|CP-01| 15 | Rechazado |
|CP-02| 16 | permitido|
|CP-03| 17 | permitido|
|CP-04| 65 | permitido|
|CP-05| 66 | rechazado|

##Validacion
En este caso los casos de pruebas cubririan:
-Valor inferior fuera del rango
-Limite superior fuera del rango
-Limite superior permitido
-valor inferior dentro del limite 

##RF-02 Código de Estudiante
El codigo de estudiantes debe cumplir con estas condiciones:
-Tener exactamente 8 caracteres.
-Iniciar con la letra “E”.
-Los 7 caracteres restantes deben ser numéricos.
