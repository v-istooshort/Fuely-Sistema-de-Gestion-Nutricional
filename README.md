# 🥗 Fuely - Sistema de Gestión Nutricional

**Fuely** es un sistema de gestión nutricional orientado a ayudar a los usuarios a calcular, personalizar y llevar el seguimiento diario de sus metas de macronutrientes y calorías. Basado en parámetros individuales (peso, talla, edad, nivel de actividad y objetivo personal), el sistema automatiza el cálculo de porciones nutricionales y permite registrar comidas a través de un catálogo inteligente y una calculadora por gramaje.

---

## Repositorio

Este repositorio contiene la especificación formal del sistema estructurada bajo la metodología del **Proceso Unificado (UP)** y los estándares **FURPS+**:

```text
.
├── README.md   # Presentación del repositorio
└── img/
    ├── Caso Uso.png
    └── Dominio.png                           
└── docs/
    ├── 00-Propuesta.md 
    ├── 01-Vision.md 
    ├── 02-Casos-de-Uso.md 
    ├── 03-Especificacion-FURPS.md 
    ├── 04-Glosario-y-Diccionario.md 
    ├── 05-Matriz-de-Riesgos.md
    ├── 06-Plan-de-Iteraciones.md
    ├── 07-Plan-de-Desarrollo.md
    ├── 08-Caso-de-Desarrollo.md
    └── 09-Diagramas-UML.md
```

---

## 📄 Índice de Artefactos del Proyecto

1. **[Visión del Proyecto y Caso de Negocio](<./docs/1-Vision y Caso de Negocio.md>)**
   - Justificación del problema y objetivos del sistema.
   - Perfil de usuarios y *stakeholders*.

2. **[Modelo de Casos de Uso](<./docs/2-Modelo de Casos de Uso.md>)**
   - **CU-01:** Registrar Usuario y Crear Perfil Fisiológico.
   - **CU-02:** Calcular Metas Nutricionales Automáticas.
   - **CU-03:** Buscar y Consultar Alimentos en el Catálogo.
   - **CU-04:** Calcular Porciones por Gramaje.
   - **CU-05:** Registrar Consumo Diario en el Diario de Alimentos.
   - **CU-06:** Visualizar Historial y Progreso Nutricional.
   - **CU-07:** Crear y Personalizar Receta / Platillo.
   - **CU-08:** Configurar Recordatorios y Notificaciones de Comida.

3. **[Especificación Suplementaria](<./docs/3-Especificacion Suplementaria.md>)**
   - **F (Functionality):** Seguridad, auditoría, autenticación y persistencia.
   - **U (Usability):** Interfaz intuitiva, diseño adaptativo y accesibilidad.
   - **R (Reliability):** Disponibilidad (99.5%), tolerancia a fallos y recuperación de datos.
   - **P (Performance):** Tiempos de respuesta (<1.5s) y gestión de peticiones concurrentes.
   - **S (Supportability):** Arquitectura modular en capas, mantenibilidad y soporte multiplataforma.
   - **+ (Restricciones):** Cumplimiento legal (protección de datos de salud), interfaces externas y licencias.

4. **[Glosario](<./docs/4-Glosario.md>)**
   - Definición de términos técnicos y nutricionales.

5. **[Matriz y Lista de Riesgos](<./docs/5-Lista de Riesgos y Plan de Gestion de Riesgos.md>)**
   - Evaluación de impacto, probabilidad y planes de contingencia para riesgos técnicos y de negocio.

6. **[Planificación de Iteraciones y](<./docs/6-Plan de Iteracion.md>) [Plan de Desarrollo](<./docs/7-Plan de Fases y Plan de Desarrollo de Software.md>)**
   - Distribución temporal por fases UP e hitos del proyecto.

7. **[Caso de Desarrollo](<./docs/8-Caso de Desarrollo.md>)**
   Proceso Unificado adaptado al proyecto Fuely bajo un enfoque ágil (Agile UP).

8. **[Diagramas UML](<./docs/9-Modelado y Diagramas UML.md>)**
   Diagramas de Casos de Uso y Modelo de Dominio conceptual.
---
