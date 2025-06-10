# Documentation for the Personal-AI APIs

This document explains the APIs interactions of the Personal AI backend for the **Karrera - Personal AI** project. It details the entire flow from user creation to the end results, detailing all the methods with their respective inputs and outputs.

## API Interactions

The user will begin by creating a session and then choosing between three different methods for providing the application with information pertaining to himself, searching the web, uploading a resume (CV) or just having a conversation with an AI agent.
All three methods can be used in conjunction and will contribute to a better overall understanding of the user. 

The main order of interaction will be as detailed in the following diagram:

```mermaid
graph LR
    A[User Init API]
    B[Upload CV]
    C[Scrape Web]
    subgraph Chat with AI
        direction LR
        D1[Create Conversation]
        D2[Send Chosen Question]
        D3[Chat Session]
        D4[Extract Chat Information]
    end
    E[Filter Entities]
    F[JSON Processor]
   
    A --> B
    A --> C
    A --> D1
    D1 --> D2
    D2 --> D3
    D3 --> D4
    B --> E
    C --> E
    D4 --> E
    E --> F
```

```mermaid
graph LR
    A[Combined JSON]
    B[Extract Biography]
    C[Generate Picture]
    subgraph Edit Biography
        direction LR
        D1[Get Selected Bio]
        D2[Save Edited Bio]
    end
    
    A --> B
    B --> D1
    B --> C
    D1 <--> D2
    
    
```