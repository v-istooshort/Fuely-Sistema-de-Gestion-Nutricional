# 🥗 Fuely - Sistema de Gestión Nutricional

**Fuely** es un sistema de gestión nutricional orientado a ayudar a los usuarios a calcular, personalizar y llevar el seguimiento diario de sus metas de macronutrientes y calorías. Basado en parámetros individuales (peso, talla, edad, nivel de actividad y objetivo personal), el sistema automatiza el cálculo de porciones nutricionales y permite registrar comidas a través de un catálogo inteligente y una calculadora por gramaje.

---

## Repositorio

Este repositorio contiene la especificación formal del sistema estructurada bajo la metodología del **Proceso Unificado (UP)** y los estándares **FURPS+**:

```text
.
├── README.md                              # Presentación del repositorio
└── docs/
    ├── 00-Propuesta.md 
    ├── 01-Vision.md 
    ├── 02-Casos-de-Uso.md 
    ├── 03-Especificacion-FURPS.md 
    ├── 04-Glosario-y-Diccionario.md 
    ├── 05-Matriz-de-Riesgos.md 
    ├── 06-Plan-de-Desarrollo.md 
    └── 07-Diagramas-UML.md
```

---

## 📄 Índice de Artefactos del Proyecto

1. **[Visión del Proyecto y Caso de Negocio]**
   - Justificación del problema y objetivos del sistema.
   - Perfil de usuarios y *stakeholders*.

2. **[Modelo de Casos de Uso]**
   - **CU-01:** Registrar Usuario y Crear Perfil Fisiológico.
   - **CU-02:** Calcular Metas Nutricionales Automáticas.
   - **CU-03:** Buscar y Consultar Alimentos en el Catálogo.
   - **CU-04:** Calcular Porciones por Gramaje.
   - **CU-05:** Registrar Consumo Diario en el Diario de Alimentos.
   - **CU-06:** Visualizar Historial y Progreso Nutricional.
   - **CU-07:** Crear y Personalizar Receta / Platillo.
   - **CU-08:** Configurar Recordatorios y Notificaciones de Comida.

3. **[Especificación Suplementaria]**
   - **F (Functionality):** Seguridad, auditoría, autenticación y persistencia.
   - **U (Usability):** Interfaz intuitiva, diseño adaptativo y accesibilidad.
   - **R (Reliability):** Disponibilidad (99.5%), tolerancia a fallos y recuperación de datos.
   - **P (Performance):** Tiempos de respuesta (<1.5s) y gestión de peticiones concurrentes.
   - **S (Supportability):** Arquitectura modular en capas, mantenibilidad y soporte multiplataforma.
   - **+ (Restricciones):** Cumplimiento legal (protección de datos de salud), interfaces externas y licencias.

4. **[Glosario]**
   - Definición de términos técnicos y nutricionales (TMB, GET, Macronutrientes, Gramaje, Equivalentes).

5. **[Matriz y Lista de Riesgos]**
   - Evaluación de impacto, probabilidad y planes de contingencia para riesgos técnicos y de negocio.

6. **[Plan de Desarrollo y Planificación de Iteraciones]**
   - Distribución temporal por fases UP (Inicio, Elaboración, Construcción, Transición) e hitos del proyecto.

7. **[Diagramas UML]**

---
