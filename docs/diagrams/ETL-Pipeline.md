```mermaid
flowchart TD
    A[S3 Raw Data] --> B{Data Validation}
    B -->|Valid| C[Player Transformation]
    B -->|Valid| D[Team Transformation]
    B -->|Valid| E[Game Transformation]
    B -->|Invalid| F[Error Handling]
    
    C --> G[Player Dimension Load]
    C --> H[Player Stats Fact Load]
    D --> I[Team Dimension Load]
    D --> J[Team Stats Fact Load]
    E --> K[Game Dimension Load]
    E --> L[Player Game Stats Load]
    E --> M[Team Game Stats Load]
    
    G --> N[PostgreSQL Data Warehouse]
    H --> N
    I --> N
    J --> N
    K --> N
    L --> N
    M --> N
    
    N --> O[Data Quality Check]
    O -->|Pass| P[Fantasy Point Calculation]
    O -->|Fail| F
    
    P --> Q[Fantasy Projections]
    
    R[Airflow DAG Orchestration] --> |Controls| A
    R --> |Controls| B
    R --> |Controls| O
    R --> |Controls| P
    R --> |Controls| Q
    
    F --> S[Notification System]
    S --> T[Slack Alert]
    S --> U[Email Alert]
    ```