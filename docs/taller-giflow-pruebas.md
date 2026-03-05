# Evaluacion de tecnicas de caja negra
## Sistema: Plataforma de gestion de eventos universitarios

Funcionalidades principales
- RF-01 Registro de Estudiante (Edad)
- RF-02 Código de Estudiante
- RF-03 Inscripción a Evento

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

# Personas 3 y 4 → RF-02 Código de Estudiante

## Análisis del Requerimiento

El código del estudiante debe cumplir las siguientes reglas:

- Tener exactamente 8 caracteres
- Iniciar con la letra E
- Los 7 caracteres restantes deben ser numéricos

Ejemplo válido:

E1234567

Cualquier código que no cumpla estas reglas debe ser rechazado.

---

## Técnica de Caja Negra Seleccionada

**Partición de Equivalencia**

---

## Justificación de la Técnica

La técnica de partición de equivalencia permite dividir las entradas posibles en **clases de equivalencia**, donde todos los valores de una clase producen el mismo comportamiento en el sistema.

En este caso se identifican:

- una clase válida
- varias clases inválidas

Esto permite reducir la cantidad de pruebas necesarias manteniendo una buena cobertura.

---

## Casos de Prueba

### Casos válidos

| ID | Código | Resultado Esperado |
|----|--------|-------------------|
| CP-06 | E1234567 | Código aceptado |

---

### Casos inválidos

| ID | Código | Motivo | Resultado Esperado |
|----|--------|--------|-------------------|
| CP-07 | A1234567 | No inicia con E | Rechazado |
| CP-08 | E123456 | Menos de 8 caracteres | Rechazado |
| CP-09 | E12345678 | Más de 8 caracteres | Rechazado |
| CP-10 | E1234A67 | Contiene letra en parte numérica | Rechazado |
| CP-11 | 12345678 | No inicia con E | Rechazado |

---

## Verificación de Cobertura

Los casos de prueba cubren las siguientes clases de equivalencia:

- código con prefijo incorrecto
- código con longitud menor a la requerida
- código con longitud mayor a la requerida
- código con caracteres inválidos
- código completamente válido

Esto asegura que todas las reglas de validación del código sean verificadas.

---

