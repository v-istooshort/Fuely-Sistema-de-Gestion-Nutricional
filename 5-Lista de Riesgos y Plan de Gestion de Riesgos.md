# 5. Lista de Riesgos y Plan de Gestión de Riesgos

El análisis de riesgos en la fase de Inception permite anticipar amenazas técnicas, de dominio y de gestión de proyecto, definiendo acciones preventivas y planes de contingencia.

### Riesgo R01: Fórmulas calóricas imprecisas
- **Mitigación Preventiva:** Validar y programar estrictamente la ecuación de Mifflin-St Jeor respaldada por la literatura médica internacional. Someter los resultados del módulo a pruebas unitarias contra valores patrón calculados manualmente por un profesional en nutrición.
- **Plan de Contingencia:** Incorporar la fórmula de Harris-Benedict revisada como método alternativo seleccionable en la configuración del perfil.

### Riesgo R02: Inconsistencia en conversión de gramajes
- **Mitigación Preventiva:** Diseñar la clase de dominio `Alimento` utilizando tipos de datos de alta precisión decimal (`BigDecimal` o `double`) para todas las operaciones intermedias, aplicando el redondeo a 1 decimal únicamente en la capa de presentación.
- **Plan de Contingencia:** Crear una suite de pruebas automatizadas con más de 50 escenarios de prueba con gramajes fraccionarios (ej. $13.7\text{ g}$, $183.5\text{ g}$) para verificar la convergencia de sumas diarios.

### Riesgo R03: Desviación en el cronograma de desarrollo
- **Mitigación Preventiva:** Congelar el alcance funcional durante Inception, dejando explícitamente fuera funciones avanzadas (escaneo de código de barras, IA de imágenes, integración con *wearables*).
- **Plan de Contingencia:** Si la Fase de Construcción presenta un retraso $> 10\%$, postergar la implementación del módulo de exportación de historial y priorizar la estabilidad del núcleo (Calculadora + Diario).

### Riesgo R04: Catálogo alimentario insuficiente
- **Mitigación Preventiva:** Pre-cargar el catálogo con una semilla de 100 alimentos básicos de alta disponibilidad en la dieta mexicana provenientes del SMAE. Priorizar el desarrollo del CU07 (Registrar Alimento Personalizado).
- **Plan de Contingencia:** Habilitar una función de importación masiva vía archivo CSV para permitir al usuario cargar listas completas de alimentos de forma externa.