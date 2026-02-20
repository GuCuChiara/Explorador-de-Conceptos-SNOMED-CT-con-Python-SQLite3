# GuCuChiara-Explorador-de-Conceptos-de-SNOMED-CT-SQLite3
Explorador SNOMED-CT Argentina – Streamlit + SQLite3

---
📌 Overview

## Aplicación interactiva para exploración semántica de SNOMED-CT Edición Argentina (Snapshot), diseñada para:

* Auditoría médica
* Curación terminológica
* Construcción de refsets
* Exploración jerárquica offline
* Soporte a interoperabilidad clínica (FHIR / ValueSets)

La solución implementa un pipeline ETL local optimizado, motor de consultas SQL y una interfaz en Streamlit.

---
🖥️ ## Arquitectura de Despliegue (Local / Portable):
* 100% local
* No requiere:
* Snowstorm
* Elasticsearch
* Servidor externo
* **Portable** (puede ejecutarse en cualquier entorno Python compatible)
---

⚙️ ## Componentes Técnicos:

| Capa         | Tecnología         | Función                        |
| ------------ | ------------------ | ------------------------------ |
| ETL          | Pandas             | Procesamiento inicial Snapshot |
| DB           | SQLite             | Persistencia optimizada        |
| Query Engine | SQL parametrizado  | Exploración semántica          |
| Resolver     | Bulk SQL query     | Traducción eficiente SCTID→FSN |
| UI           | Streamlit          | Interfaz interactiva           |
| Export       | OpenPyXL + BytesIO | Generación Excel en memoria    |

---
## Estructura del Proyecto:
├── Buscador_SNOMED-CT_5_Sqlite3.py
├── snomed_argentina.db (auto-generado)
├── README.md
└── Snapshot/
    ├── sct2_Description_*.txt
    └── sct2_Relationship_*.txt
---
🧩## Funcionalidades
🔎 ## Búsqueda por FSN (Español)

Filtro activo (active = 1)

Limitación a 50 resultados

⬆️ Jerarquía

Ancestros (Is-A)

Descendientes (inversa de Is-A)

🧩 Atributos

Agrupados por relationshipGroup

Visualización estructurada tipo JSON

🌳 Construcción de Refset

Selección de descendientes con checkbox

Exportación Excel multi-hoja:

Concepto raíz

Descendientes seleccionados

Atributos detallados

🧹 UX Enterprise

Botón flotante estilo SaaS

Tooltip contextual

Manejo limpio de estado (session_state)

Reinicio controlado (st.rerun())


