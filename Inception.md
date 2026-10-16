# Universidad Autónoma de Zacatecas
## Ingeniería de Software

**Materia:** Análisis y Diseño Orientado a Objetos  
**Actividad:** Tarea 2: Inception  
**Alumna:** Vanessa Berenice Rodríguez Nava  
**Fecha:** 15 de octubre de 2026  

---

## Artefacto 1. Visión y Caso de Negocio

### Resumen Ejecutivo
**Fuely** es una aplicación para seguimiento nutricional y balance energético personalizado. Resuelve la falta de precisión al registrar comidas mediante la conversión automática de nutrientes por gramaje específico, conectando las necesidades metabólicas del usuario con su ingesta diaria.

### Caso de Negocio
Calcular de forma rústica las porciones de los macronutrientes para cada comida, según el objetivo del usuario, representa dificultades y un obstáculo para su progreso. Además, la mayoría de las aplicaciones alimentarias fallan por falta de flexibilidad en el ajuste de porciones reales o no respaldan su información con la de organizaciones de salud. **Fuely** automatiza la relación entre requerimientos calóricos/macronutrientes e ingesta real, aumentando la adherencia a objetivos físicos (pérdida, mantenimiento o ganancia de masa muscular), al comparar los detalles nutrimentales con instituciones oficiales (Secretaría de Salud y *Food And Drug Administration*).

### Objetivos de Alto Nivel
1. Permitir la configuración de un perfil biométrico preciso (peso, edad, sexo, estatura, nivel de actividad).
2. Ofrecer un cálculo dinámico proporcional de macronutrientes según los gramos consumidos.
3. Proporcionar un diario intuitivo de monitoreo diario frente a la meta fijada.

### Limitaciones
El alcance inicial no contempla escaneo de código de barras, integración en vivo de actividad física con smartwatches, o análisis con IA de alimentos a través de fotografías.

---

## 2. Modelo de Casos de Uso

### Casos de Uso
* **CU01** Registrar Datos Biométricos
* **CU02** Configurar Objetivo Nutricional
* **CU03** Buscar Alimento en Catálogo
* **CU04** Calcular Macronutrientes por Porción
* **CU05** Registrar Comida en Diario
* **CU06** Consultar Balance Diario
* **CU07** Registrar Alimento Personalizado

### Detalle de Casos de Uso CU04: Calcular Macronutrientes por Porción

| Elemento | Descripción |
| :--- | :--- |
| **Actor Principal** | Usuario Principal / Sistema (Calculadora) |
| **Precondiciones** | El alimento seleccionado existe en el catálogo y tiene definidos sus valores por cada 100 g (proteínas, carbohidratos, grasas, calorías base). |
| **Flujo Principal** | 1. El usuario selecciona un alimento del catálogo.<br>2. El usuario ingresa la cantidad exacta en gramos consumidos (ej. 180 g).<br>3. El sistema aplica la fórmula de proporción.<br>4. El sistema despliega el desglose final de macronutrientes. |
| **Postcondiciones** | Los datos calculados quedan listos para guardarse en el diario del usuario. |

---

## 3. Especificación Suplementaria

| Atributo | Especificación |
| :--- | :--- |
| **Usabilidad** | El cálculo de porciones y resumen diario debe responder en un tiempo ≤200 ms. |
| **Fiabilidad** | La base de datos debe mantener consistencia transaccional al guardar o modificar registros en el diario. |
| **Arquitectura** | Diseño basado en capas simples o MVC (Modelo-Vista-Controlador), separando la lógica de cálculo metabólico. |
| **Restricciones Metodológicas** | Desarrollo bajo paradigma Orientado a Objetos. |

---

## 4. Glosario

| Término | Definición |
| :--- | :--- |
| **TMB (Tasa Metabólica Basal)** | Cantidad mínima de energía (calorías) que el cuerpo necesita en reposo. |
| **Macronutrientes (Macros)** | Nutrientes principales que aportan energía: Proteínas, Carbohidratos y Grasas. |
| **Densidad Nutrimental** | Proporción de nutrientes y calorías contenidos en una cantidad base de 100 g de alimento. |
| **Gramaje Específico** | Peso real en gramos consumido por el usuario para escalar los macronutrientes base. |

---

## 5. Lista de Riesgos y Plan de Gestión de Riesgos

### Fórmulas calóricas imprecisas

| Categoría / Impacto | Plan de Mitigación |
| :--- | :--- |
| **Técnico / Dominio** *(Alto)* | Validar algoritmos con estándares médicos/nutricionales (ej. revisar Guía de Alimentos para la población Mexicana, utilizar fórmula de Harris-Benedict o Mifflin-St Jeor). |

### Inconsistencia en conversión de gramajes

| Categoría / Impacto | Plan de Mitigación |
| :--- | :--- |
| **Técnico** *(Medio)* | Diseñar la clase alimento con pruebas unitarias específicas para divisiones decimales y redondeos. |

### Desvío en el cronograma

| Categoría / Impacto | Plan de Mitigación |
| :--- | :--- |
| **Proyecto / Recursos** *(Medio)* | Reducir el alcance inicial dejando fuera funciones avanzadas (como exportación PDF o historial mensual) para asegurar la entrega del núcleo. |

---

## 6. Prototipos y Prueba de Conceptos

* **Prototipo GUI:** Mockups.

---

## 7. Plan de Iteración (Elaboración 1)

| Elemento | Descripción |
| :--- | :--- |
| **Objetivo de la iteración** | Implementar el núcleo del modelo de dominio y la arquitectura de cálculo. |
| **Tareas Clave** | 1. Diseñar el diagrama de clases conceptual (Usuario, Alimento, RegistroComida, Diario).<br>2. Implementar los Casos de Uso CU01 (Perfil) y CU04 (Cálculo de porciones por gramaje).<br>3. Ejecutar pruebas unitarias sobre los métodos de cálculo nutricional. |

---

## 8. Plan de Desarrollo de Software

### Estimación General del Proyecto
* **Inicio:** 2-3 semanas — *Definición de requisitos, alcance y arquitectura general.*
* **Elaboración:** 4-6 semanas — *Diseño Orientado a Objetos, diagramas UML, patrones de diseño e implementación del núcleo.*
* **Construcción:** 4 semanas — *Interfaz de usuario final, persistencia de datos e historial.*
* **Transición:** 1-2 semanas — *Pruebas de usuario y corrección de bugs.*

### Recursos
* Un desarrollador, un equipo de cómputo, entorno IDE, herramientas UML.

---

## 9. Caso de Desarrollo (Personalización de UP)

### Entregables
* Visión y Caso de Negocio (Documento de propuesta).
* Diagramas UML (Casos de uso, Diagrama de Clases de Dominio).
* Código Fuente estructurado en capas (Lógica OO y UI).
