# Workflow Diagram: Kilocode Modes + Memory Bank + GitFlow

The following diagram illustrates the integrated workflow between Kilocode modes, Memory Bank, and GitFlow for feature development.

## Mermaid Diagram

```mermaid
graph TD
    %% Main workflow nodes
    FR[Feature Request] --> AM[Architect Mode]
    AM --> AB[Architecture Branch Creation]
    AB --> FP[Feature Planning]
    FP --> APR[Architecture PR Review]
    APR --> FB[Feature Branch Creation]
    FB --> CM[Code Mode]
    CM --> Implementation
    Implementation --> DM[Debug Mode]
    DM --> Testing
    Testing --> CR[Code Review]
    CR --> Integration
    Integration --> OM[Orchestrator Mode]
    OM --> Release
    
    %% Memory Bank interactions
    MB[Memory Bank] <--> AM
    MB <--> CM
    MB <--> DM
    MB <--> OM
    
    %% GitFlow branches
    Develop[Develop Branch] --> AB
    AB --> APR
    APR --> Develop
    Develop --> FB
    FB --> PR[Pull Request]
    PR --> Develop
    Develop --> RB[Release Branch]
    RB --> Main[Main Branch]
    RB --> Develop
    
    %% Mode transitions
    AM --> CM
    CM --> DM
    DM --> ASK[Ask Mode]
    ASK --> CM
    DM --> OM
    
    %% Subgraphs for organization
    subgraph PlanningPhase[Planning Phase]
        FR
        AM
        AB
        FP
        APR
    end
    
    subgraph DevPhase[Development Phase]
        FB
        CM
        Implementation
        DM
        Testing
    end
    
    subgraph ReviewPhase[Review Phase]
        CR
        ASK
        PR
    end
    
    subgraph IntegrationPhase[Integration & Release Phase]
        Integration
        OM
        Release
    end
    
    subgraph MemoryBank[Memory Bank]
        MB
        Brief[brief.md]
        Product[product.md]
        Context[context.md]
        Architecture[architecture.md]
        Tech[tech.md]
        Tasks[tasks.md]
    end
    
    subgraph GitFlowGraph[GitFlow]
        Main
        Develop
        AB
        FB
        RB
    end
    
    %% Memory Bank file relationships
    MB --> Brief
    MB --> Product
    MB --> Context
    MB --> Architecture
    MB --> Tech
    MB --> Tasks
    
    %% Styling
    classDef kiloMode fill:#f9f,stroke:#333,stroke-width:2px;
    classDef gitBranch fill:#bbf,stroke:#333,stroke-width:2px;
    classDef memoryBank fill:#bfb,stroke:#333,stroke-width:2px;
    classDef phase fill:#fff,stroke:#333,stroke-width:1px;
    
    class AM,CM,DM,ASK,OM kiloMode;
    class Main,Develop,AB,FB,RB,PR,APR gitBranch;
    class MB,Brief,Product,Context,Architecture,Tech,Tasks memoryBank;
    class PlanningPhase,DevPhase,ReviewPhase,IntegrationPhase,MemoryBank,GitFlowGraph phase;
```

## Simplified Workflow Diagram

```mermaid
flowchart LR
    FR[Feature Request] --> AM[Architect Mode]
    AM --> APR[Architecture PR]
    APR --> CM[Code Mode]
    CM --> DM[Debug Mode]
    DM --> CR[Code Review]
    CR --> OM[Orchestrator Mode]
    OM --> Release
    
    MB[Memory Bank] <--> AM
    MB <--> CM
    MB <--> DM
    MB <--> OM
    
    AB[Architecture Branch] --> APR
    APR --> FB[Feature Branch]
    FB --> PR[Pull Request]
    PR --> DB[Develop Branch]
    DB --> RB[Release Branch]
    RB --> Main[Main Branch]
    
    AM -.-> AB
    APR -.-> FB
    CM -.-> FB
    DM -.-> FB
    CR -.-> PR
    OM -.-> RB
    Release -.-> Main
    
    classDef kiloMode fill:#f9f,stroke:#333,stroke-width:2px;
    classDef gitBranch fill:#bbf,stroke:#333,stroke-width:2px;
    classDef memoryBank fill:#bfb,stroke:#333,stroke-width:2px;
    
    class AM,CM,DM,CR,OM kiloMode;
    class AB,APR,FB,PR,DB,RB,Main gitBranch;
    class MB memoryBank;
```

## Key

- **Pink Boxes**: Kilocode Modes
- **Blue Boxes**: GitFlow Branches
- **Green Boxes**: Memory Bank Components
- **Solid Lines**: Direct Workflow
- **Dotted Lines**: Relationships/Interactions

This diagram illustrates how the different components interact throughout the feature development lifecycle, from initial planning through to release.