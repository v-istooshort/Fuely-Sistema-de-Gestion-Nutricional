# 5. Lista de Riesgos y Plan de Gestión de Riesgos

El análisis de riesgos en la fase de Inception permite anticipar amenazas técnicas, de dominio y de gestión de proyecto, definiendo acciones preventivas y planes de contingencia.

## 5.1 Matriz Severidad / Probabilidad

| ID | Descripción del Riesgo | Categoría | Probabilidad | Impacto | Nivel de Riesgo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R01** | **Fórmulas calóricas imprecisas o erróneas:** Uso de ecuaciones no acreditadas que generen metas calóricas nocivas o ineficaces para el usuario. | Dominio / Médico | Baja | Crítico | **Alto** |
| **R02** | **Inconsistencia y acumulativo de errores en conversión de gramajes:** Pérdida de precisión por redondeo flotante en múltiples cálculos pequeños por gramo. | Técnico / Software | Media | Alto | **Alto** |
| **R03** | **Desviación en el cronograma de desarrollo:** Retraso en la entrega de módulos debido a complejidad innecesaria en la UI o alcance mal acotado. | Gestión / Proyecto | Media | Medio | **Medio** |
| **R04** | **Baja adopción por catálogo alimentario insuficiente:** Frustración del usuario al no encontrar alimentos comunes en la base de datos inicial. | Producto / Usabilidad | Media | Alto | **Alto** |
| **R05** | **Falla de persistencia en concurrencia de escrituras al diario:** Corrupción de registros diarios por cierres intempestivos de la aplicación. | Técnico / BD | Baja | Alto | **Medio** |

## 5.2 Estrategias de Mitigación y Contingencia

### Riesgo R01: Fórmulas calóricas imprecisas
- **Mitigación Preventiva:** Validar y programar estrictamente la ecuación de Mifflin-St Jeor respaldada por la literatura médica internacional. Someter los resultados del módulo a pruebas unitarias contra valores patrón calculados manualmente por un profesional en nutrición.
- **Plan de Contingencia:** Incorporar la fórmula de Harris-Benedict revisada como método alternativo seleccionable en la configuración del perfil.

### Riesgo R02: Inconsistencia en conversión de gramajes
- **Mitigación Preventiva:** Diseñar la clase de dominio `Alimento` utilizando tipos de datos de alta precisión decimal (`BigDecimal` o `double`) para todas las operaciones intermedias, aplicando el redondeo a 1 decimal únicamente en la capa de presentación.
- **Plan de Contingencia:** Crear una suite de pruebas automatizadas con más de 50 escenarios de prueba con gramajes fraccionarios (ej. $13.7\text{ g}$, $183.5\text{ g}$) para verificar la convergencia de sumas diarios.

### Riesgo R03: Desviación en el cronograma de desarrollo
- **Mitigación Preventiva:** Congelar el alcance funcional durante Inception, dejando explícitamente fuera funciones avanzadas (escaneo de código de barras, IA de imágenes, integración con accesorios deportivos).
- **Plan de Contingencia:** Si la Fase de Construcción presenta un retraso $> 10\%$, postergar la implementación del módulo de exportación de historial y priorizar la estabilidad del núcleo (Calculadora + Diario).

### Riesgo R04: Catálogo alimentario insuficiente
- **Mitigación Preventiva:** Pre-cargar el catálogo con 100 alimentos básicos de alta disponibilidad en la dieta mexicana provenientes del SMAE. Priorizar el desarrollo del CU07 (Registrar Alimento Personalizado).
- **Plan de Contingencia:** Habilitar una función de importación masiva vía archivo CSV para permitir al usuario cargar listas completas de alimentos de forma externa.

---