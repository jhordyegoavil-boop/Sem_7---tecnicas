# Tarea: Mi prompt avanzado

## Tarea elegida
Generar casos de prueba detallados y estructurados para el formulario de registro de usuarios de una tienda web.

## Version 1: prompt basico
```text
Dame casos de prueba para un registro de usuarios.
```
* **Qué técnica se agregó/usó:** Ninguna, es un prompt directo y genérico de una sola oración.
* **Por qué se usó:** Para establecer una línea base y observar el comportamiento estándar del modelo sin restricciones.
* **Qué mejoró en la respuesta:** La respuesta fue muy general, teórica y estructurada en viñetas informativas, pero carecía de datos de entrada específicos, valores de frontera reales ni el formato estructurado que un equipo de QA necesita.

## Version 2
```text
Actua como analista de pruebas de software.
Necesito casos de prueba para el formulario de registro de una tienda web (nombre, correo, contrasena y confirmar contrasena). La contrasena debe tener minimo 8 caracteres, una mayuscula y un numero. No se permite un correo ya registrado.
Escribe 8 casos de prueba en una tabla con las columnas: ID, escenario, datos de entrada, resultado esperado. Responde en espanol.
```
* **Qué técnica se agregó:** **Role Prompting** ("Actúa como analista...") y **Definición de Formato** (Tabla con columnas específicas).
* **Por qué se usó:** Para forzar al modelo a adoptar una perspectiva profesional técnica y obligarlo a entregar la información de manera compacta e inmediatamente utilizable.
* **Qué mejoró en la respuesta:** La salida cambió drásticamente a una tabla organizada. El modelo incluyó datos ficticios de prueba y alineó los escenarios a las reglas del negocio de la tienda virtual.

## Version 3: prompt final
```text
<rol>Actua como analista de pruebas de software con experiencia en aplicaciones web, que prepara casos de prueba para un equipo de estudiantes de desarrollo.</rol>
 
<contexto>Formulario de registro de una tienda web con los campos: nombre, correo, contrasena y confirmar contrasena. Reglas: la contrasena debe tener minimo 8 caracteres, al menos una mayuscula y al menos un numero; las dos contrasenas deben ser iguales; no se permite un correo ya registrado.</contexto>
 
<ejemplos>

| ID | escenario | datos de entrada | resultado esperado |
| CP-01 | Registro correcto | nombre: Ana Ruiz, correo: ana@correo.com, contrasena: Clave2024, confirmar: Clave2024 | Se crea la cuenta y se muestra "Registro exitoso" |
| CP-02 | Contrasena sin numero | nombre: Luis Paz, correo: luis@correo.com, contrasena: ClaveSegura, confirmar: ClaveSegura | No se crea la cuenta y se muestra "La contrasena debe tener un numero" |
</ejemplos>
 
<tarea>Piensa paso a paso: primero lista cada regla del formulario y que puede fallar en ella (incluye valores limite, campos vacios y datos con formato incorrecto). Luego escribe 10 casos de prueba distintos, sin repetir los ejemplos.</tarea>
 
<formato>Tabla con las columnas: ID, escenario, datos de entrada, resultado esperado. Los IDs siguen el formato de los ejemplos (CP-03, CP-04, ...). Responde en espanol.</formato>
 
<revision>Al final, revisa tu propia tabla: si faltan casos limite (por ejemplo, contrasena de exactamente 8 caracteres, nombre vacio o correo con espacios) o hay casos repetidos, corrigelos e indica cuales agregaste o quitaste.</revision>
```
* **Qué técnica se agregó:** **Prompt Estructurado** (etiquetas XML), **Few-Shot Prompting** (ejemplos), **Chain of Thought** (pensar paso a paso) y **Autocrítica** (fase de revisión final).
* **Por qué se usó:** Para modularizar las instrucciones, guiar el razonamiento lógico del modelo y garantizar que la salida final no tuviera omisiones ni duplicados con los ejemplos del profesor.
* **Qué mejoró en la respuesta:** La IA ejecutó primero un desglose técnico exhaustivo de riesgos antes de escribir la matriz. Los casos de prueba resultantes fueron mucho más avanzados, incluyendo valores límite exactos (como contraseñas de exactamente 7 u 8 caracteres) y validaciones de usabilidad idóneas para capacitar a alumnos de desarrollo.

## Tecnicas usadas en el prompt final

| Parte del Prompt Final | Técnica Correspondiente |
| :--- | :--- |
| `<rol>Actua como analista de pruebas de software con experiencia...</rol>` | **Role Prompting** (Rol específico sin usar la palabra "experto") |
| `<ejemplos> ... </ejemplos>` | **Few-Shot Prompting** (Muestra el estándar esperado de salida) |
| `<tarea>Piensa paso a paso: primero lista cada regla... </tarea>` | **Chain of Thought / Descomposición** (Obliga al desglose lógico previo) |
| `<revision>Al final, revisa tu propia tabla... </revision>` | **Autocrítica / Self-Correction** (Control de calidad interno del modelo) |
| Uso de etiquetas `<rol>`, `<contexto>`, `<tarea>`, etc. | **Prompt Estructurado** (Uso de delimitadores claros) |

## Evaluacion del resultado

| Criterio de Evaluación | Cumplimiento (Sí / No) | Observaciones |
| :--- | :---: | :--- |
| ¿El rol adoptado es específico y no genérico? | **Sí** | Se definió como un analista enfocado en preparar material didáctico para estudiantes. |
| ¿El formato de la salida coincide con lo solicitado? | **Sí** | Entregó exactamente una tabla con los nombres de columna requeridos. |
| ¿Se evitaron redundancias con los ejemplos provistos? | **Sí** | Los identificadores iniciaron en CP-03 y los escenarios fueron completamente nuevos. |
| ¿El modelo analizó de forma efectiva los valores límites? | **Sí** | Evaluó los bordes exactos de 7 y 8 caracteres para la validación de la contraseña. |

## Por que elegi estas tecnicas
Elegí la combinación de **Role Prompting**, **Few-Shot**, **Chain of Thought** y **Autocrítica** porque el aseguramiento de la calidad de software (QA) requiere una precisión absoluta y un razonamiento riguroso. Al forzar al modelo a "pensar paso a paso" antes de generar los casos, se emula el proceso mental que un analista real sigue al mapear historias de usuario. Además, la técnica de autocrítica es vital aquí, ya que los modelos de lenguaje tienden a omitir escenarios negativos o valores límite sutiles si no se les exige explícitamente revisar su propio trabajo antes de finalizar la respuesta.
