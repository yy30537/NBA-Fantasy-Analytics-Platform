# Full vs. Incremental Loads

Why distinguish between them:

- Full loads replace entire datasets, ensuring data consistency but are resource-intensive
- Incremental loads add only new/changed data, more efficient but can miss changes if poorly designed

For NBA data, both are necessary:

- Full loads: Beginning of season, after major schema changes
- Incremental loads: Daily game updates, injury updates

```mermaid
flowchart TD
    subgraph "Load Type Decision"
        A[ETL Trigger] --> B{Is Season Start?}
        B -->|Yes| C[Full Load]
        B -->|No| D{Has Schema Change?}
        D -->|Yes| C
        D -->|No| E{Reprocessing Historical?}
        E -->|Yes| C
        E -->|No| F[Incremental Load]
    end
    
    subgraph "Full Load Process"
        C --> G[Archive Current Data]
        G --> H[Empty Target Tables]
        H --> I[Process All Source Data]
        I --> J[Load All Records]
        J --> K[Update Data Version]
    end
    
    subgraph "Incremental Load Process"
        F --> L[Identify New/Changed Records]
        L --> M[Process Delta Only]
        M --> N[Upsert Records]
        N --> O[Update Data Version]
    end
    
    K --> P[Data Quality Checks]
    O --> P
    P --> Q[Update ETL Run Stats]
```