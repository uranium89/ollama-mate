```mermaid
graph TD
    A[AnythingLLM] --- |User Interface| O[Ollama]
    A --- |Vector Storage| Q[Qdrant]
    A --- |Workflow Trigger| N[n8n]
    
    N[n8n] --- |Workflow Storage| P[(PostgreSQL)]
    N --- |Model Inference| O
    N --- |Vector Search| Q
    
    O[Ollama] --- |Generate Embeddings| Q
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style O fill:#bbf,stroke:#333,stroke-width:2px
    style N fill:#bfb,stroke:#333,stroke-width:2px
    style P fill:#fb9,stroke:#333,stroke-width:2px
    style Q fill:#ff9,stroke:#333,stroke-width:2px
    
    classDef default fill:#fff,stroke:#333,stroke-width:2px;
```

## Component Descriptions

- **AnythingLLM**: Frontend interface that users interact with for LLM operations
- **Ollama**: Handles AI model serving and inference tasks
- **n8n**: Manages workflow automation and orchestrates the entire process
- **PostgreSQL**: Stores workflow configurations and system data
- **Qdrant**: Vector database that manages embeddings for semantic search
