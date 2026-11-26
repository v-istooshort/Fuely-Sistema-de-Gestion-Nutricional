# 6. Plan de Iteración (Fase de Elaboración 1)

## 6.1 Objetivos de la Iteración E1
La primera iteración de la fase de Elaboración (E1) tiene como propósito central construir el núcleo de la arquitectura orientada a objetos de Fuely, mitigando los riesgos técnicos de mayor severidad (R01 y R02).

**Objetivos Clave:**
1. Implementar las clases de dominio fundamentales.
2. Ejecutar la prueba del algoritmo de cálculo por gramaje (CU04) con persistencia local.
3. Desarrollar la interfaz base para el registro de datos biométricos (CU01) y la configuración de metas (CU02).

## 6.2 Desglose de Trabajos (WBS) y Criterios de Aceptación

```
WBS Iteración Elaboración 1 (E1 - 2 Semanas)
├── 1. Infraestructura y Capa de Datos (20h)
│   ├── 1.1 Crear esquema de base de datos relacional (6h)
│   ├── 1.2 Implementar clases DAO / Repositorios de Persistencia (8h)
│   └── 1.3 Cargar script de datos (Catálogo base 50 alimentos) (6h)
├── 2. Lógica de Dominio y Métodos Metabólicos (25h)
│   ├── 2.1 Implementar Ecuación Mifflin-St Jeor en clase CalculadoraMetabolica (8h)
│   ├── 2.2 Programar escalado de macronutrientes por gramaje (9h)
├── 3. Interfaz de Usuario e Integración (25h)
│   ├── 3.1 Construir pantalla de Registro Biométrico y Perfil (8h)
│   ├── 3.2 Implementar pantalla de Calculadora por Gramaje y selección de alimento (10h)
│   └── 3.3 Conectar UI con Controladores y Lógica de Dominio (7h)
└── 4. Evaluación y Pruebas de Iteración (10h)
    ├── 4.1 Ejecutar pruebas de integración UI -> Dominio -> BD (6h)
    └── 4.2 Evaluación de criterios de aceptación con Stakeholders (4h)
```

### Criterios de Aceptación para la Iteración E1:
- El cálculo de TMB y GET debe arrojar una desviación de $0.0\%$ con respecto a tablas clínicas de referencia.
- El cálculo por gramaje de un alimento debe responder en menos de $200\text{ ms}$ en la interfaz gráfica.
- Las pruebas unitarias de la lógica metabólica deben alcanzar una cobertura de código $\ge 90\%$.

---