# 2. Modelo de Casos de Uso

## 2.1 Identificación de Actores y Matriz de Objetivos

| Actor | Tipo | Objetivo en el Sistema |
| :--- | :--- | :--- |
| **Usuario Principal** | Humano (Directo) | Registrar datos biométricos, definir metas nutricionales, calcular porciones por gramaje, registrar comidas diarias, consultar el balance calórico e historial. |
| **Sistema (Calculadora Metabólica)** | Sistema Interno | Ejecutar fórmulas matematico-biométricas, calcular densidad nutrimental por gramaje y mantener la consistencia transaccional del diario. |

## 2.2 Repertorio Completo de Casos de Uso

| Código | Nombre del Caso de Uso | Categoría / Módulo | Nivel de Detalle |
| :--- | :--- | :--- | :--- |
| **CU01** | Registrar Datos Biométricos | Perfil de Usuario | *Fully Dressed* |
| **CU02** | Configurar Objetivo Nutricional | Perfil de Usuario | *Fully Dressed* |
| **CU03** | Buscar Alimento en Catálogo | Catálogo Nutricional | *Fully Dressed* |
| **CU04** | Calcular Macronutrientes por Porción | Calculadora por Gramaje | *Fully Dressed* |
| **CU05** | Registrar Comida en Diario | Diario Alimentario | *Fully Dressed* |
| **CU06** | Consultar Balance Diario | Diario Alimentario | *Fully Dressed* |
| **CU07** | Registrar Alimento Personalizado | Catálogo Nutricional | *Fully Dressed* |
| **CU08** | Consultar Historial Nutricional | Historial y Seguimiento | *Fully Dressed* |

---

### 2.3 Especificación Detallada de Casos de Uso

### Caso de Uso CU01: Registrar Datos Biométricos

---

### Caso de Uso CU02: Configurar Objetivo Nutricional

---

### Caso de Uso CU03: Buscar Alimento en Catálogo

---

### Caso de Uso CU04: Calcular Macronutrientes por Porción

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal / Sistema (Calculadora).
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Quiere saber exactamente cuántas calorías y macros consumir al servir una porción específica expresada en gramos.
- **Precondiciones:** El alimento seleccionado existe en el catálogo y posee definidos sus valores nutrimentales base por cada 100 g.
- **Garantía de Éxito (Postcondiciones):** Se calculan y muestran los valores exactos ajustados al gramaje consumido, dejándolos listos para ser añadidos al diario.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal selecciona un alimento desde el Catálogo o desde la vista de registro del Diario.
  2. El Sistema despliega la pantalla de la Calculadora de Gramaje mostrando la densidad base por 100 g.
  3. El Usuario Principal introduce la cantidad exacta en gramos consumidos (ej. 180 g de pechuga de pollo).
  4. El Sistema aplica la fórmula de regla de tres directa para escalar cada macronutriente:
     $$\text{Macro}_{\text{calculado}} = \left( \frac{\text{Macro}_{\text{base100g}}}{100} \right) \times \text{Gramos}_{\text{ingresados}}$$
  5. El Sistema calcula las calorías totales resultantes:
     $$\text{Kcal}_{\text{totales}} = (\text{Proteína}_g \times 4) + (\text{Carbohidrato}_g \times 4) + (\text{Grasa}_g \times 9)$$
  6. El Sistema muestra en pantalla el desglose final ajustado por gramaje.
- **Extensiones (o Flujos Alternativos):**
  - *3a. Gramaje igual a cero o valor negativo:*
    1. El Sistema detecta que el usuario ingresó un valor $\le 0$.
    2. El Sistema deshabilita el botón de cálculo/confirmación y muestra una alerta: *"Ingrese una cantidad mayor a 0 gramos."*
- **Requerimientos Especiales:** Manejo de precisión decimal (redondeo a 1 decimal) para evitar errores acumulativos.
- **Tecnología y Lista de Variaciones de Datos:** Entrada de texto numérico decimal; actualización reactiva de resultados.
- **Frecuencia de Ocurrencia:** Alta (cada vez que se prepara o registra una comida).

---

### Caso de Uso CU05: Registrar Comida en Diario

---

### Caso de Uso CU06: Consultar Balance Diario


---

### Caso de Uso CU07: Registrar Alimento Personalizado

---

### Caso de Uso CU08: Consultar Historial Nutricional
