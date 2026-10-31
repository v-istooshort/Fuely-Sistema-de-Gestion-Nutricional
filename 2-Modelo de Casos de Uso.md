# 2. Modelo de Casos de Uso

## Casos de Uso
* **CU01** Registrar Datos Biométricos
* **CU02** Configurar Objetivo Nutricional
* **CU03** Buscar Alimento en Catálogo
* **CU04** Calcular Macronutrientes por Porción
* **CU05** Registrar Comida en Diario
* **CU06** Consultar Balance Diario
* **CU07** Registrar Alimento Personalizado

## Detalle de Casos de Uso CU04: Calcular Macronutrientes por Porción

| Elemento | Descripción |
| :--- | :--- |
| **Actor Principal** | Usuario Principal / Sistema (Calculadora) |
| **Precondiciones** | El alimento seleccionado existe en el catálogo y tiene definidos sus valores por cada 100 g (proteínas, carbohidratos, grasas, calorías base). |
| **Flujo Principal** | 1. El usuario selecciona un alimento del catálogo.<br>2. El usuario ingresa la cantidad exacta en gramos consumidos (ej. 180 g).<br>3. El sistema aplica la fórmula de proporción.<br>4. El sistema despliega el desglose final de macronutrientes. |
| **Postcondiciones** | Los datos calculados quedan listos para guardarse en el diario del usuario. |