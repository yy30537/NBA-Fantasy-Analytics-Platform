# NBA-Fantasy-Analytics-Platform
End-to-end data pipeline and analytics dashboard that help fantasy basketball players make better decisions.



```
nba-fantasy-analytics/
│
├── README.md                           # Project overview and setup instructions
├── requirements.txt                    # Python dependencies
├── .gitignore                          # Git ignore file
├── config/                             # Configuration files
│   ├── database.ini                    # Database connection parameters
│   └── scraper_config.ini              # Scraper configuration
│
├── docs/                               # Documentation
│   ├── diagrams/                       # Mermaid diagrams
│   │   ├── data-acquisition-pipeline.mmd
│   │   ├── database-schema.mmd
│   │   ├── etl-pipeline.mmd
│   │   └── deployment-architecture.mmd
│   └── implementation-roadmap.md       # Implementation plan
│
├── sql/                                # SQL scripts
│   ├── schema.sql                      # Database schema creation script
│   ├── indexes.sql                     # Index creation script
│   └── views.sql                       # Views for analytics
│
├── nba_scraper/                        # Web scraper package
│   ├── __init__.py
│   ├── main.py                         # Scraper core functionality
│   ├── run_scraper.py                  # CLI script to run scraper
│   └── utils/
│       ├── __init__.py
│       └── helpers.py                  # Helper functions
│
├── nba_etl/                            # ETL package
│   ├── __init__.py
│   ├── transformers.py                 # Data transformation logic
│   ├── loaders.py                      # Database loading logic
│   └── validators.py                   # Data validation
│
├── airflow/                            # Airflow DAGs
│   ├── dags/
│   │   └── nba_fantasy_dag.py          # Main data pipeline DAG
│   └── plugins/
│       └── nba_operators/              # Custom operators if needed
│
├── api/                                # API services
│   ├── __init__.py
│   ├── app.py                          # FastAPI application
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── players.py                  # Player endpoints
│   │   └── teams.py                    # Team endpoints
│   └── models/
│       ├── __init__.py
│       └── schemas.py                  # Pydantic models
│
├── analytics/                          # Analytics and prediction models
│   ├── __init__.py
│   ├── fantasy_scoring.py              # Fantasy points calculation
│   ├── player_projections.py           # Player projection models
│   └── optimization.py                 # Lineup optimization
│
└── tests/                              # Test suites
    ├── test_scraper.py
    ├── test_etl.py
    └── test_api.py
```