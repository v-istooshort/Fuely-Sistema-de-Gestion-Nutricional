# 3. Especificación Suplementaria (Metodología FURPS+)

La Especificación Suplementaria captura todos los requisitos del sistema que no están contenidos en los casos de uso, enfocándose fundamentalmente en los atributos de calidad no funcionales bajo el modelo **FURPS+** (Funcionalidad, Usabilidad, Confiabilidad, Rendimiento y Soportabilidad, más las restricciones auxiliares).

## 3.1 Funcionalidad (Functionality)
- **Algoritmos Metabólicos Validados:** El sistema debe emplear las fórmulas clínicas de **Mifflin-St Jeor** o **Harris-Benedict** para determinar la Tasa Metabólica Basal (TMB), considerando las variables de peso ($kg$), estatura ($cm$), edad (años) y sexo biológico.
- **Cálculo Proporcional Exacto:** Las operaciones de escalado por gramaje alimentario deben aplicar reglas aritméticas sobre la densidad base de 100 g sin aplicar factores de redondeo prematuros que distorsionen los resultados.
- **Seguridad de Datos Biométricos:** La información del perfil de usuario y sus métricas corporales deben ser almacenadas localmente de forma privada, garantizando que no sean accesibles por otras aplicaciones del sistema operativo.
- **Flexibilidad de Categorización:** El sistema debe permitir la clasificación de alimentos en al menos 5 grupos alimenticios principales: Proteínas, Carbohidratos, Grasas Saludables, Verduras y Frutas.

## 3.2 Usabilidad (Usability)
- **Tiempo de Aprendizaje Intuitivo:** Un usuario sin experiencia previa en aplicaciones de nutrición debe ser capaz de calcular un alimento y registrarlo en su diario en menos de 3 minutos durante su primer uso.
- **Eficiencia en la Entrada de Datos:** La calculadora debe solicitar únicamente el gramaje consumido una vez seleccionado el alimento, reduciendo los clics o toques requeridos para completar un registro a un máximo de 3 interacciones.
- **Claridad Visual e Iconografía:** La distribución de macronutrientes y balances calóricos debe representarse mediante indicadores numéricos claros y contrastantes, facilitando su lectura a una distancia de 50 cm en pantallas móviles o de escritorio.
- **Diseño Responsivo y Adaptable:** La interfaz gráfica debe adaptarse fluidamente a resoluciones de pantalla desde $360 \times 640$ píxeles (dispositivos móviles) hasta $1920 \times 1080$ píxeles (escritorio).

## 3.3 Confiabilidad / Fiabilidad (Reliability)
- **Integridad Transaccional:** El guardado o modificación de registros en el diario alimentario debe cumplir con las propiedades ACID. Si ocurre un fallo durante la escritura, el sistema debe restaurar el estado anterior (*rollback*) sin corromper el diario del día.
- **Tolerancia a Errores de Entrada:** El motor de cálculo debe prevenir fallos de ejecución (*crashes*) ante entradas de texto no numéricas, cadenas vacías o valores nulos, respondiendo siempre con capturas de excepción amigables.
- **Preservación de Datos:** Ante un cierre inesperado de la aplicación o apagado del dispositivo, los datos guardados en la base de datos local no deben sufrir pérdidas ni corrupción de archivos.
- **Precisión Decimal en Redondeos:** Los macronutrientes deben mantener una precisión flotante interna de doble precisión (`double`) y mostrarse al usuario final redondeados a un decimal ($0.1\text{ g}$), evitando discrepancias donde la suma de comidas no coincida con el total diario.

## 3.4 Rendimiento (Performance)
- **Tiempo de Respuesta en Cálculos:** El tiempo transcurrido desde que el usuario introduce el gramaje hasta que la pantalla despliega el desglose recalculado de macronutrientes no debe exceder los **200 milisegundos** ($< 200\text{ ms}$).
- **Velocidad de Búsqueda en Catálogo:** La consulta de alimentos en la base de datos local debe retornar los primeros 20 resultados coincidentes en un tiempo inferior a **100 milisegundos**.
- **Consumo Eficiente de Recursos:** La aplicación no debe consumir más de 120 MB de memoria RAM en ejecución activa ni superar el 5% de uso de CPU durante períodos de reposo o navegación estática.
- **Tiempo de Carga Inicial:** El arranque de la aplicación desde estado frío hasta estar lista para recibir interacción no debe demorar más de 2 segundos en hardware estándar.

## 3.5 Soportabilidad (Supportability)
- **Arquitectura Orientada a Objetos (POO):** El sistema debe estar diseñado bajo el patrón **Modelo-Vista-Controlador (MVC)** o Arquitectura en Capas, garantizando un desacoplamiento estricto entre la interfaz de usuario, la lógica metabólica de dominio y la capa de persistencia.
- **Mantenibilidad del Código:** La base de código debe seguir las convenciones estándar de desarrollo OO, permitiendo que un nuevo desarrollador comprenda la estructura en menos de 2 días.
- **Extensibilidad de Catálogo:** La capa de datos debe estar estructurada de modo que sea posible importar nuevas tablas nutrimentales sin necesidad de recompilar la lógica de dominio.
- **Independencia de Plataforma:** La lógica de cálculo de dominio debe estar aislada de librerías nativas del sistema operativo para facilitar su migración.

## 3.6 Restricciones Auxiliares (+)

### Requisitos de Implementación
- **Lenguaje de Programación:** Desarrollo implementado en un lenguaje fuertemente orientado a objetos.
- **Persistencia de Datos:** Utilización de un motor de base de datos relacional ligero y embebidoo persistencia basada en objetos.
- **Control de Versiones:** Repositorio administrado mediante Git con una estrategia de ramas ordenada.

### Requisitos de Interfaz
- **Restricción de Entradas:** Los campos de gramaje únicamente aceptarán dígitos numéricos y un separador decimal.
- **Retroalimentación Visual:** Cualquier acción de guardado, actualización o eliminación debe ser acompañada de un mensaje informativo de breve duración.

### Requisitos de Operaciones
- **Despliegue Local:** La aplicación debe funcionar de manera autónoma y *offline*, sin depender de conexión a servidores remotos ni APIs externas para sus funciones centrales.
- **Carga de Datos:** El sistema debe incluir un script de instalación que cargue el catálogo base con al menos 50 alimentos comunes y su información por 100 g.

### Requisitos Legales y Normativos
- **Aviso de Exención de Responsabilidad Médica (*Disclaimer*):** El sistema debe incluir una leyenda visible indicando que Fuely es una herramienta de apoyo nutricional y de acondicionamiento físico, lo cual no sustituye la prescripción o diagnóstico de un profesional de la salud o nutriólogo clínico.
- **Fuentes de Datos Certificadas:** Los valores nutrimentales base de la aplicación deben estar respaldados explícitamente en tablas del Sistema Mexicano de Alimentos Equivalentes (SMAE), la Secretaría de Salud o la FDA.