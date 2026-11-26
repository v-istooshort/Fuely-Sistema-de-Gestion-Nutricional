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

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Desea ingresar su información corporal de manera precisa y sencilla para obtener una estimación calórica personalizada.
  - *Sistema:* Requiere datos numéricos válidos dentro de rangos biológicos coherentes para evitar cálculos erróneos de TMB.
- **Precondiciones:** El sistema se encuentra ejecutando y la interfaz de perfil está accesible.
- **Garantía de Éxito (Postcondiciones):** Los datos biométricos (edad, sexo, peso, estatura, nivel de actividad) quedan almacenados en la entidad Usuario y se calcula la Tasa Metabólica Basal (TMB).
- **Principal Escenario de Éxito:**
  1. El Usuario Principal accede a la sección de Perfil de Usuario.
  2. El Usuario Principal ingresa su edad (años), sexo (masculino/femenino), peso corporal ($kg$), estatura ($cm$) y selecciona su nivel de actividad física (sedentario, ligero, moderado, intenso).
  3. El Usuario Principal solicita guardar los datos ingresados.
  4. El Sistema valida que los campos estén completos y dentro de los rangos numéricos permitidos (ej. peso entre 20 kg y 300 kg; estatura entre 100 cm y 250 cm).
  5. El Sistema calcula la Tasa Metabólica Basal (TMB) utilizando la fórmula de Mifflin-St Jeor.
  6. El Sistema actualiza el perfil del usuario y despliega un mensaje de confirmación con el valor de TMB resultante.
- **Extensiones (o Flujos Alternativos):**
  - *4a. Datos fuera de rango o incompletos:*
    1. El Sistema detecta un valor no numérico, negativo o fuera de rango biológico (ej. edad = 0 o peso = -5).
    2. El Sistema resalta el campo con error y muestra una notificación: *"Por favor, ingrese un valor biométrico válido."*
    3. El Usuario Principal corrige el valor y retoma el paso 3.
- **Requerimientos Especiales:** Interfaz con controles numéricos adecuados y mensajes de validación instantáneos.
- **Tecnología y Lista de Variaciones de Datos:** Entrada mediante teclado o selector de rango (*spinner/slider*).
- **Frecuencia de Ocurrencia:** Baja (al crear la cuenta o al registrar cambios de peso significativos).

---

### Caso de Uso CU02: Configurar Objetivo Nutricional

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Quiere definir su meta física (pérdida de peso, mantenimiento o ganancia muscular) y obtener la distribución automática de macronutrientes.
- **Precondiciones:** CU01 (Registrar Datos Biométricos) completado previamente; la TMB debe estar calculada.
- **Garantía de Éxito (Postcondiciones):** Queda registrado el Gasto Energético Total (GET), las calorías meta diarias y el reparto gramo a gramo de proteínas, carbohidratos y grasas.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal selecciona la opción "Configurar Meta Nutricional".
  2. El Sistema presenta los tres objetivos disponibles: Pérdida de Grasa (Déficit Calórico), Mantenimiento (Eucalórica) y Ganancia Muscular (Superávit Calórico).
  3. El Usuario Principal selecciona el objetivo deseado.
  4. El Sistema calcula el Gasto Energético Total (GET) aplicando el factor de actividad física sobre la TMB.
  5. El Sistema ajusta las calorías totales agregando o sustrayendo el margen energético correspondiente (ej. -500 kcal para déficit, +300 kcal para superávit).
  6. El Sistema distribuye el porcentaje de macronutrientes según guías estándar (ej. 30% Proteínas, 40% Carbohidratos, 30% Grasas) y convierte los porcentajes a gramos absolutos diarios.
  7. El Sistema guarda la meta nutricional y presenta el desglose al usuario.
- **Extensiones (o Flujos Alternativos):**
  - *3a. Personalización avanzada de distribución de macronutrientes:*
    1. El Usuario Principal elige ajustar manualmente los porcentajes de macronutrientes.
    2. El Sistema verifica que la suma de porcentajes sea exactamente 100%.
    3. Si la suma difiere de 100%, el Sistema advierte: *"La suma de macronutrientes debe ser exactamente 100%."* y no permite guardar hasta corregir.
- **Requerimientos Especiales:** Cálculo exacto de calorías por gramo (Proteína: 4 kcal/g, Carbohidrato: 4 kcal/g, Grasa: 9 kcal/g).
- **Tecnología y Lista de Variaciones de Datos:** Selección mediante botones radio o deslizadores proporcionales.
- **Frecuencia de Ocurrencia:** Media (se ajusta según la fase de entrenamiento o evolución física).

---

### Caso de Uso CU03: Buscar Alimento en Catálogo

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Requiere localizar rápidamente un ingrediente o platillo en el catálogo para conocer su información nutrimental base o usarlo en el diario.
- **Precondiciones:** El catálogo de alimentos cuenta con registros iniciales almacenados.
- **Garantía de Éxito (Postcondiciones):** Se despliega el listado de alimentos coincidentes con sus valores por cada 100 g base.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal ingresa al módulo de Catálogo de Alimentos.
  2. El Usuario Principal escribe el nombre o término de búsqueda en la barra de consulta (ej. "pechuga de pollo").
  3. El Sistema filtra el catálogo en tiempo real buscando coincidencias en la denominación o categoría del alimento.
  4. El Sistema muestra una lista de resultados especificando: Nombre, Categoría (Proteínas, Carbohidratos, Grasas, Verduras, Frutas), y la densidad nutrimental por 100 g (Calorías, Proteínas, Carbohidratos, Grasas).
  5. El Usuario Principal selecciona un alimento de la lista para ver su detalle completo.
- **Extensiones (o Flujos Alternativos):**
  - *3a. No se encuentran coincidencias:*
    1. El Sistema no detecta alimentos que coincidan con la palabra ingresada.
    2. El Sistema muestra el mensaje: *"No se encontraron alimentos con esa denominación."* y sugiere la opción de ejecutar el **CU07 (Registrar Alimento Personalizado)**.
- **Requerimientos Especiales:** Búsqueda ágil en memoria o base de datos con tiempo de respuesta < 100 ms.
- **Tecnología y Lista de Variaciones de Datos:** Filtro por texto (*string matching*) e iconos por categoría alimenticia.
- **Frecuencia de Ocurrencia:** Alta (múltiples veces al día).

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

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Desea asociar un alimento calculado a un tiempo de comida específico para llevar su bitácora del día.
- **Precondiciones:** El cálculo por gramaje (CU04) ha sido realizado y se ha seleccionado la fecha actual o una fecha válida.
- **Garantía de Éxito (Postcondiciones):** El alimento con sus gramos y macronutrientes calculados queda anexado al tiempo de comida correspondiente en el diario diario.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal elige la opción "Agregar al Diario" tras realizar un cálculo o desde el propio Diario.
  2. El Sistema presenta la selección de tiempos de comida: Desayuno, Comida, Cena o Colación.
  3. El Usuario Principal selecciona el tiempo de comida destino.
  4. El Usuario Principal confirma el registro.
  5. El Sistema guarda la entrada alimenticia vinculándola a la fecha seleccionada y al tiempo de comida elegido.
  6. El Sistema recalcula los totales acumulados del tiempo de comida y del día completo.
  7. El Sistema retorna al diario mostrando la nueva entrada insertada.
- **Extensiones (o Flujos Alternativos):**
  - *5a. Error de persistencia en la base de datos:*
    1. El Sistema sufre una interrupción al guardar la transacción.
    2. El Sistema revierte la operación (*rollback*), notifica al usuario: *"No se pudo guardar la comida. Intente de nuevo."* y conserva los datos en pantalla para reintentar.
- **Requerimientos Especiales:** Consistencia transaccional ACID en la base de datos local.
- **Tecnología y Lista de Variaciones de Datos:** Listas desplegables o tarjetas seleccionables por tiempo de comida.
- **Frecuencia de Ocurrencia:** Entre 3 y 6 veces al día por usuario.

---

### Caso de Uso CU06: Consultar Balance Diario

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Necesita visualizar de forma rápida cuánto ha consumido y cuánto le resta por consumir en el día para no exceder su meta.
- **Precondiciones:** Se ha configurado la meta nutricional (CU02).
- **Garantía de Éxito (Postcondiciones):** Se presenta una vista resumida del avance calórico y de macronutrientes del día seleccionado.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal accede a la pantalla principal del Diario.
  2. El Sistema recupera todas las entradas registradas para la fecha seleccionada.
  3. El Sistema suma el total de calorías, proteínas, carbohidratos y grasas consumidas hasta el momento.
  4. El Sistema compara los acumulados contra la Meta Nutricional Diaria del usuario.
  5. El Sistema calcula el remanente calórico y de macronutrientes:
     $$\text{Remanente} = \text{Meta}_{\text{diaria}} - \text{Consumido}_{\text{acumulado}}$$
  6. El Sistema despliega barras de progreso numéricas y métricas visuales del balance energético (Calorías Consumidas vs. Calorías Restantes).
- **Extensiones (o Flujos Alternativos):**
  - *4a. El usuario supera la meta diaria (Superávit no planificado / Exceso):*
    1. El Sistema detecta que el valor consumido excede la meta diaria.
    2. El Remanente se calcula como valor negativo y el Sistema aplica un estilo de alerta (ej. indicador numérico destacado) notificando: *"Ha superado su meta calórica por X kcal."*
- **Requerimientos Especiales:** Tiempo de renderizado de la pantalla $\le 200\text{ ms}$.
- **Tecnología y Lista de Variaciones de Datos:** Componentes de interfaz reactivos (barras de avance numéricas).
- **Frecuencia de Ocurrencia:** Alta (múltiples consultas al día).

---

### Caso de Uso CU07: Registrar Alimento Personalizado

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Quiere agregar un alimento comercial o receta propia que no existe en el catálogo base de la aplicación.
- **Precondiciones:** El usuario dispone de la tabla nutrimental del producto (valores por 100 g).
- **Garantía de Éxito (Postcondiciones):** El nuevo alimento queda registrado en el catálogo del usuario y disponible para futuros cálculos.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal presiona el botón "Agregar Alimento Personalizado" en el Catálogo.
  2. El Sistema presenta un formulario pidiendo: Nombre del Alimento, Categoría, y datos nutrimentales base por cada 100 g (Calorías, Proteínas, Carbohidratos, Grasas).
  3. El Usuario Principal ingresa la información requerida.
  4. El Usuario Principal guarda el registro.
  5. El Sistema valida que los campos estén completos, que las calorías sean coherentes con la suma de los macronutrientes expresados y que no sea un nombre duplicado.
  6. El Sistema almacena el nuevo alimento etiquetándolo como "Personalizado por Usuario".
  7. El Sistema notifica: *"Alimento guardado con éxito en su catálogo."*
- **Extensiones (o Flujos Alternativos):**
  - *5a. Incoherencia matemática en datos ingresados:*
    1. El Sistema detecta que las calorías declaradas difieren significativamente ($> 15\%$) del cálculo teórico ($\text{Proteína}\times 4 + \text{Carbohidrato}\times 4 + \text{Grasa}\times 9$).
    2. El Sistema advierte al usuario sobre la discrepancia y sugiere un auto-cálculo de calorías base.
    3. El Usuario Principal acepta la corrección sugerida o confirma sus valores manuales.
- **Requerimientos Especiales:** Formulario estructurado con validadores de rango.
- **Tecnología y Lista de Variaciones de Datos:** Formulario de captura estándar con persistencia relacional.
- **Frecuencia de Ocurrencia:** Baja a Media (ocasional cuando se adquieren productos nuevos).

---

### Caso de Uso CU08: Consultar Historial Nutricional

- **Alcance:** Sistema de Control Nutricional Fuely.
- **Nivel:** Objetivo del Usuario.
- **Actor Principal:** Usuario Principal.
- **Stakeholders e Intereses:**
  - *Usuario Principal:* Desea revisar su apego a la dieta en días o semanas anteriores para evaluar sus resultados físicos.
- **Precondiciones:** Existen registros de comidas almacenados en fechas pasadas.
- **Garantía de Éxito (Postcondiciones):** El sistema despliega el desglose del diario y el balance calórico de la fecha histórica seleccionada.
- **Principal Escenario de Éxito:**
  1. El Usuario Principal ingresa al módulo de Historial.
  2. El Sistema presenta un selector de fecha o calendario.
  3. El Usuario Principal selecciona un día anterior específico.
  4. El Sistema recupera la bitácora alimentaria de esa fecha (alimentos, gramos, tiempos de comida y balance final frente a la meta vigente en ese día).
  5. El Sistema despliega el resumen histórico completo de solo lectura.
- **Extensiones (o Flujos Alternativos):**
  - *4a. Sin registros para la fecha seleccionada:*
    1. El Sistema no encuentra entradas para la fecha consultada.
    2. El Sistema muestra el mensaje: *"No hay registros alimentarios guardados para la fecha seleccionada."*.
- **Requerimientos Especiales:** Vista de solo lectura para evitar alterations accidentales a registros pasados.
- **Tecnología y Lista de Variaciones de Datos:** Selector de fecha (*DatePicker*).
- **Frecuencia de Ocurrencia:** Media (1 o 2 veces por semana).