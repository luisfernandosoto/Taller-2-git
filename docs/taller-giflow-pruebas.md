# Documento de Pruebas

## 1. Descripción del Sistema

La Plataforma de Gestión de Eventos Universitarios es un sistema que permite administrar la participación de estudiantes en eventos académicos organizados por la universidad.

Las principales funcionalidades del sistema son:

- Registro de estudiantes en la plataforma.
- Validación del código estudiantil.
- Inscripción de estudiantes a eventos disponibles.

El objetivo de este documento es diseñar y documentar pruebas utilizando técnicas de caja negra, con el fin de verificar que el sistema cumpla con los requerimientos funcionales establecidos.

---

# 2. Requerimientos a Evaluar

### RF-01 Registro de Estudiante (Edad)

El sistema debe permitir el registro de estudiantes cuya edad esté entre 16 y 65 años inclusive.

---

### RF-02 Código de Estudiante

El código del estudiante debe cumplir las siguientes condiciones:

- Tener exactamente 8 caracteres.
- Iniciar con la letra E.
- Los 7 caracteres restantes deben ser numéricos.

Ejemplo válido:

E1234567

---

### RF-03 Inscripción a Evento

Un estudiante podrá inscribirse a un evento únicamente si:

- Está registrado en el sistema.
- El evento tiene cupos disponibles.
- No está previamente inscrito en el evento.

Si alguna de estas condiciones no se cumple, el sistema debe **rechazar la inscripción**.

---

# 3. Técnicas de Prueba Aplicadas

Para evaluar los requerimientos del sistema se aplicaron diferentes técnicas de **pruebas de caja negra**.

### RF-01 Registro de Edad

**Técnica aplicada:** Análisis de Valores Límite.

**Justificación:**  
El requerimiento establece un rango de valores numéricos (16 a 65). La técnica de análisis de valores límite permite verificar el comportamiento del sistema en los extremos del rango, donde suelen presentarse errores de validación.

---

### RF-02 Código de Estudiante

**Técnica aplicada:** Partición de Equivalencia.

**Justificación:**  
El requerimiento define reglas estructurales del código. La partición de equivalencia permite dividir las entradas en clases válidas e inválidas, reduciendo el número de pruebas necesarias sin perder cobertura.

---

### RF-03 Inscripción a Evento

**Técnica aplicada:** Tabla de Decisión.

**Justificación:**  
El comportamiento del sistema depende de múltiples condiciones lógicas. La tabla de decisión permite evaluar todas las combinaciones posibles entre dichas condiciones para garantizar que el sistema responda correctamente.

---

# 4. Casos de Prueba Diseñados

## RF-01 Registro de Estudiante (Edad)

| ID | Edad | Resultado Esperado |
|----|------|-------------------|
| CP-01 | 15 | Registro rechazado |
| CP-02 | 16 | Registro permitido |
| CP-03 | 30 | Registro permitido |
| CP-04 | 65 | Registro permitido |
| CP-05 | 66 | Registro rechazado |

---

## RF-02 Código de Estudiante

### Casos válidos

| ID | Código | Resultado Esperado |
|----|--------|-------------------|
| CP-06 | E1234567 | Código aceptado |

### Casos inválidos

| ID | Código | Motivo | Resultado Esperado |
|----|--------|--------|-------------------|
| CP-07 | A1234567 | No inicia con E | Rechazado |
| CP-08 | E123456 | Menos de 8 caracteres | Rechazado |
| CP-09 | E12345678 | Más de 8 caracteres | Rechazado |
| CP-10 | E1234A67 | Contiene letra en parte numérica | Rechazado |
| CP-11 | 12345678 | No inicia con E | Rechazado |

---

## RF-03 Inscripción a Evento

| Caso | Registrado | Cupos Disponibles | Ya Inscrito | Resultado Esperado |
|-----|------------|------------------|------------|-------------------|
| CP-12 | Sí | Sí | No | Inscripción permitida |
| CP-13 | Sí | No | No | Inscripción rechazada |
| CP-14 | No | Sí | No | Inscripción rechazada |
| CP-15 | Sí | Sí | Sí | Inscripción rechazada |
| CP-16 | No | No | No | Inscripción rechazada |
| CP-17 | No | Sí | Sí | Inscripción rechazada |
| CP-18 | Sí | No | Sí | Inscripción rechazada |
| CP-19 | No | No | Sí | Inscripción rechazada |

---

# 5. Trazabilidad



| Requerimiento | Casos de Prueba |
|---------------|----------------|
| RF-01 Registro de Edad | CP-01, CP-02, CP-03, CP-04, CP-05 |
| RF-02 Código de Estudiante | CP-06, CP-07, CP-08, CP-09, CP-10, CP-11 |
| RF-03 Inscripción a Evento | CP-12, CP-13, CP-14, CP-15, CP-16, CP-17, CP-18, CP-19 |


---

# 6. Gestión de Versiones (GitFlow)

Para el control de versiones del proyecto se utilizó la estrategia **GitFlow**, la cual permite organizar el desarrollo y las pruebas del sistema mediante ramas específicas.

Las ramas utilizadas fueron:

### main
Contiene la versión estable del proyecto.

### develop
Integra los cambios realizados durante el desarrollo y pruebas.

### feature
En este caso como estoy solo solamente hacia commit por cada RF
feature/RF-01-pruebas-edad  
feature/RF-02-validacion-codigo  
feature/RF-03-inscripcion-eventos  

Flujo de trabajo:

1. Crear una rama feature desde develop.
2. Implementar cambios o diseño de pruebas.
3. Realizar commit de los cambios.
4. Hacer merge hacia develop.
5. Una vez validado el sistema, realizar merge hacia main.

