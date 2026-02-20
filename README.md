# GuCuChiara-Explorador-de-Conceptos-de-SNOMED-CT-SQLite3
Explorador SNOMED-CT Argentina – Streamlit + SQLite3

🏗️ Arquitectura (alto nivel)
flowchart TD
  A[SNOMED CT Snapshot (TXT)\n- Descriptions\n- Relationships] -->|One-time ETL| B[ETL Builder (Pandas)]
  B -->|Filtrado\nactive=1, language=es| C[SQLite DB\nsnomed_argentina.db]
  C -->|Índices\nterm, conceptId,\nsourceId, destinationId| C

  subgraph App[Streamlit App]
    D[UI Layer\n- Search Input\n- Selectbox\n- Data Editor\n- Download Button] --> E[Query Engine (SQLite)]
    E --> C
    E --> F[Bulk Resolver\nSCTID → FSN (1 query)]
    F --> D

    D --> G[State Manager\nst.session_state\n(query, selection)]
    H[Floating Action Button\nHTML/CSS + Tooltip] --> I[Param Trigger\n?fab=1]
    I -->|Clear state + rerun| G
    G --> D
  end

  D -->|Select descendants\n(checkbox)| J[Export Builder\nBytesIO + OpenPyXL]
  J --> K[Excel Output\n- Info\n- Descendientes_Refset\n- Detalle_Atributos]
