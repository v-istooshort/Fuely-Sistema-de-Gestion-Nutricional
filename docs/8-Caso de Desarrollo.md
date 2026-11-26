# 8. Caso de Desarrollo

El Proceso Unificado se adapta al proyecto Fuely bajo un enfoque ágil (Agile UP), reduciendo la burocracia documental y priorizando la entrega de código ejecutable comprobable en cada iteración.

## 8.1 Adaptación del Proceso Unificado para Fuely

| Disciplina UP | Práctica Adaptada para Fuely | Nivel de Formalidad |
| :--- | :--- | :--- |
| **Modelado de Negocio** | Identificación de la problemática de porciones y metabólica mediante Visión y Caso de Negocio. | Ligera / Esencial |
| **Requerimientos** | Captura mediante Casos de Uso *Fully Dressed* (Cockburn) y Especificación Suplementaria FURPS+. | Alta / Formal |
| **Análisis y Diseño** | Diseño Orientado a Objetos basado en patrones (MVC, DAO) y Diagramas UML de Clases de Dominio. | Media / Enfocada en Núcleo |
| **Implementación** | Programación orientada a objetos en capas con pruebas unitarias integradas. | Alta / Rigurosa |
| **Pruebas** | Pruebas unitarias automatizadas de la lógica metabólica y pruebas de aceptación de usuario en UI. | Alta |
| **Gestión de Configuración** | Control de versiones estricto con Git y entregas incrementales por iteración. | Alta |

## 8.2 Mapeo de Artefactos y Prácticas Requeridas

```
MAPEO DE ARTEFACTOS UP ÁGIL - PROYECTO FUELY
┌──────────────────────────────────────────────────────────────────┐
│ FASE DE INICIO (INCEPTION)                                       │
│  ├── Visión y Caso de Negocio (Documento de Propuesta)          │
│  ├── Modelo de Casos de Uso (Especificación Completa CU01-CU08)  │
│  ├── Especificación Suplementaria (Matriz FURPS+)                │
│  ├── Glosario y Diccionario de Datos                             │
│  ├── Lista de Riesgos y Plan de Gestión                         │
│  ├── Plan de Desarrollo y Caso de Desarrollo                     │
│  └── Diagrama de Clases de Dominio UML                     │
└──────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌──────────────────────────────────────────────────────────────────┐
│ FASES SIGUIENTES (ELABORACIÓN / CONSTRUCCIÓN / TRANSICIÓN)        │
│  ├── Diagramas de Secuencia (Interacción entre Objetos)          │
│  ├── Código Fuente Ejecutable (Capa UI, Controlador, Modelo, DAO)│
│  └── Suite de Pruebas Unitarias e Integración                    │
└──────────────────────────────────────────────────────────────────┘
```