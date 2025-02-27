![[Screenshot 2025-02-24 at 11.01.09 PM.png]]


```
flowchart TD
    subgraph "Frontend Application"
        A[DAO Profile Creation] --> B[Store in Supabase]
        C[Connect Me Button] --> D[AI Matching Engine]
        E[Create Proposal] --> F[Smart Contract Integration]
        G[View Matches] --> H[Collaboration Interface]
        I[View Proposals] --> J[Proposal Management]
    end

    subgraph "Backend Services"
        B --> K[Supabase Database]
        D --> K
        F --> L[Blockchain Network]
        M[Event Listener] --> L
        M --> N[AI Proposal Analyzer]
        K --> D
    end

    subgraph "AI Components"
        D --> O[DAO Similarity Analysis]
        N --> P[Collaboration Plan Generator]
        P --> Q[Recommendation Engine]
    end

    L --> M
    N --> H
    Q --> H
    O --> G
```