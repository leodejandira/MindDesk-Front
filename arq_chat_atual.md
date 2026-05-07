graph TD
    %% Cores e Estilos
    classDef front fill:#dcf8c6,stroke:#333,stroke-width:2px;
    classDef back fill:#b3d4ff,stroke:#333,stroke-width:2px;
    classDef ia fill:#fff5b1,stroke:#333,stroke-width:2px;
    classDef db fill:#ffcccc,stroke:#333,stroke-width:2px;

    %% Elementos
    A[Front-end HTML <br/> Porta 5000]:::front
    B(Back-end Node.js <br/> Frank - Porta 3000):::back
    C{Microsserviço Python <br/> Léo - Porta 8000}:::ia
    D[(Supabase <br/> Gustavo)]:::db
    E((OpenAI API)):::ia

    %% Conexões
    A -->|POST /chat/perguntar <br/> query, tenant_id| B
    B -->|Injeta chaves do .env <br/> via ai_service| C
    C -->|1. Busca Contexto| D
    C -->|2. Envia Prompt + Contexto| E
    E -->|3. Resposta Gerada| C
    C -->|Retorna JSON| B
    B -->|Exibe na Tela| A