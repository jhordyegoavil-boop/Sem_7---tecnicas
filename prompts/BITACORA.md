# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting.
Herramienta de IA usada: (escribe aqui cual usaste)

## Ejercicio 2: Zero-shot, one-shot y few-shot

### Resultados
 
| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|------------------------------------|
| Zero-shot | 5 | Lista numerada con la etiqueta y, en algunos casos, una explicacion corta | No |
| One-shot | 5 | Lista numerada, mas parecida al ejemplo, pero con detalles distintos en algunas lineas | No |
| Few-shot | 5 | Una linea por comentario con el formato `"texto" -> Etiqueta`, sin explicaciones | Si |

---

## Ejercicio 3: Chain of Thought
 
### Resultados
 
| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|--------------------|---------------------------|------------------|
| Directo | 318,60 | No | Si |
| Paso a paso | S/ 318,60 (con cada calculo detallado) | Si | Si |
 
---

## Ejercicio 4: Role prompting

### Resultados
 
| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|-------------------------------|-----------------------|----------------------|
| A. Sin rol | Intermedio, explicacion general | Un ejemplo corto de codigo | A cualquier persona, sin un publico definido |
| B. Rol docente | Sencillo | Comparacion de la vida diaria (una caja con etiqueta) | A quien esta empezando a programar |
| C. Rol senior | Tecnico (tipo de dato, memoria, alcance) | Codigo en Java | A un programador que ya conoce lo basico |
 
---

## Ejercicio 5: Descomposicion

### Registro por paso
 

| Paso / Elemento | Descripción / Entregable | Impacto en el Desarrollo |
| :--- | :--- | :--- |
| **Paso 1: Requisitos** | Definición de **5 funcionalidades clave**: registrar productos, controlar stock, buscar productos, alertas de bajo stock y reportes. | Estableció el alcance claro del sistema desde el inicio. |
| **Paso 2: Diseño de Clases** | Modelado de clases estructurales (`Producto`, `Categoria`, `Proveedor`, `Inventario`) con sus respectivos atributos y tipos de datos. | Creó la arquitectura de datos antes de escribir código. |
| **Paso 3: Implementación** | Codificación de la clase `Producto` en Java (atributos, constructor, *getters* y *setters*), alineada estrictamente al paso 2. | Código limpio, enfocado y fácil de revisar de manera aislada. |
| **Paso 4: Optimización** | Incorporación de **3 mejoras técnicas**: validación de datos no negativos, uso de tipos precisos para dinero (`BigDecimal`) y método `toString`. | Elevó la robustez, seguridad y calidad del código base. |
| **Comparación (Iterativo vs. Todo de una vez)** | El enfoque tradicional dio un resultado genérico y masivo. El enfoque por pasos permitió **validar cada etapa**, logrando un diseño ordenado y coherente. | Demuestra que el desarrollo modular evita la acumulación de errores de diseño. |


## Ejercicio 6: Prompt estructurado y autocritica

| Que revisar | Cumple (Si / No) |
|-------------|------------------|
| ¿Tiene las 4 columnas pedidas? | Si |
| ¿Incluye el bloqueo despues de 3 intentos? | Si |
| ¿Incluye casos con campos vacios? | No |
| ¿Indica que casos agrego en la autocritica? | Si |
| ¿Hay algun caso repetido o que no tenga sentido? | Si |
 


