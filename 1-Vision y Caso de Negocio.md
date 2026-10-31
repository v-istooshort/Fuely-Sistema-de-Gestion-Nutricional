# 1. Visión y Caso de Negocio

## 1.1 Caso de Negocio y Declaración del Problema
En el ámbito de la salud, la nutrición y el acondicionamiento físico, llevar un control riguroso de la ingesta calórica y de macronutrientes (proteínas, carbohidratos y grasas) constituye el factor determinante para alcanzar objetivos corporales específicos, tales como la pérdida de tejido graso, el mantenimiento del peso corporal o la ganancia de masa muscular. No obstante, la mayoría de las personas enfrentan severas dificultades al intentar calcular sus porciones alimenticias de manera empírica o rústica. La falta de precisión al medir los gramos reales consumidos conduce a desviaciones significativas en el balance energético diario, provocando frustración y abandono de las metas nutricionales.

Asimismo, gran parte de las herramientas digitales existentes en el mercado presentan deficiencias operativas notables: carecen de flexibilidad para ajustar las porciones según el gramaje específico consumido en cada comida, utilizan bases de datos alimentarias genéricas o no verificadas, y omiten fundamentar sus recomendaciones en parámetros de instituciones oficiales de salud.

**Fuely** surge como un sistema de software diseñado para resolver de raíz esta problemática. La plataforma automatiza la vinculación entre los requerimientos metabólicos del usuario y su ingesta real de alimentos, escalando proporcionalmente los macronutrientes en función de la densidad nutrimental base (definida por cada 100 gramos de ingrediente) respaldada por organismos oficiales como la Secretaría de Salud de México y *Food And Drug Administration* (FDA, USA).

## 1.2 Objetivos de Alto Nivel
1. **Gestión Biométrica Personalizada:** Permitir la configuración de un perfil biométrico preciso (edad, sexo, peso, estatura y nivel de actividad física) para calcular la Tasa Metabólica Basal (TMB) y el Gasto Energético Total (GET) mediante algoritmos clínicamente validados (Mifflin-St Jeor / Harris-Benedict).
2. **Cálculo Dinámico por Gramaje Específico:** Ofrecer un motor de cálculo que escale proporcionalmente las calorías y macronutrientes de cualquier alimento según la porción exacta consumida en gramos ($g$).
3. **Monitoreo Estructurado en Diario Nutricional:** Proporcionar un diario intuitivo organizado por tiempos de comida (desayuno, comida, cena y colaciones) que muestre en tiempo real el progreso de macronutrientes consumidos frente a la meta diaria establecida, detallando calorías acumuladas y restantes.
4. **Catálogo de Alimentos Confiable:** Mantener un repositorio categorizado de alimentos ordenados por tipo y densidad nutrimental por cada 100 g base, permitiendo además el registro de alimentos personalizados por parte del usuario.
5. **Seguimiento Histórico Evolutivo:** Incorporar un módulo de historial que permita consultar dietas y registros de fechas anteriores, facilitando el ajuste continuo de metas según la evolución del rendimiento físico y la composición corporal.

## 1.3 Alcance y Limitaciones Explícitas
Para garantizar la viabilidad del proyecto dentro de la fase de Inicio y su posterior desarrollo iterativo, se establecen los siguientes límites del sistema:

- **Dentro del Alcance:**
  - Registro y actualización de perfil biométrico y objetivos físicos.
  - Calculadora de macronutrientes proporcional por gramaje consumido.
  - Diario alimentario distribuido en 4 tiempos de comida.
  - Catálogo de alimentos base (densidad nutrimental por 100 g) y registro de alimentos personalizados.
  - Consulta de historial diario y acumulado de ingesta.
  - Arquitectura en capas bajo el paradigma Orientado a Objetos (POO / MVC).

- **Fuera del Alcance Inicial:**
  - Escaneo automático de códigos de barras mediante cámara.
  - Sincronización en tiempo real con dispositivos vestibles (*smartwatches* o pulseras de actividad).
  - Reconocimiento o análisis de alimentos mediante visión por computadora o Inteligencia Artificial.
  - Exportación masiva de reportes clínicos en formato PDF o integración con expedientes médicos electrónicos externos.

## 1.4 Matriz de Stakeholders e Intereses

| Stakeholder | Rol en el Sistema | Interés Principal en el Proyecto |
| :--- | :--- | :--- |
| **Usuario Principal (Deportista / Paciente)** | Actor Principal | Requiere calcular de forma rápida y sin errores las porciones exactas en gramos de sus alimentos, monitorear su meta diaria y ajustar su dieta según su objetivo corporal. |
| **Desarrollador / Arquitecto de Software** | Equipo de Desarrollo | Desea construir un sistema modular, mantenible y robusto bajo el paradigma de Objetos, aplicando patrones de diseño (MVC) y Proceso Unificado. |
| **Nutriólogo / Asesor Nutricional** | Consultor de Dominio | Le interesa que los cálculos de TMB/GET y las tablas nutrimentales de densidad por 100 g se apeguen estrictamente a estándares oficiales (Secretaría de Salud / FDA / SMAE). |

## 1.5 Análisis de Viabilidad Operativa
El proyecto Fuely demuestra una viabilidad técnica y operativa óptima. Al estar concebido como una aplicación orientada a objetos desarrollada en capas (Interfaz de Usuario, Lógica de Dominio y Persistencia Local), no requiere de infraestructura de servidores de alto rendimiento para su ejecución inicial. Los algoritmos matemáticos de conversión por gramaje implican operaciones aritméticas de baja complejidad computacional $O(1)$, lo que garantiza tiempos de respuesta muy cortos. La disponibilidad de bases de datos alimentarias oficiales (como el Sistema Mexicano de Alimentos Equivalentes - SMAE) asegura la validez de los datos de entrada sin incurrir en costos de licenciamiento de terceros.