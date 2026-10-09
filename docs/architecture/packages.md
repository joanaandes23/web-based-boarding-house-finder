
# Package Diagram — Web-Based Boarding House Finder

**Project:** Web-Based Boarding House Finder  
**Team:** Fourward Devs  
**Block:** BSIS 4-1  
**School:** Sorsogon State University (SorSU), Bulan Campus

## Scope

This package diagram presents the proposed folder structure and dependencies of the Web-Based Boarding House Finder. It separates presentation, application logic, domain rules, infrastructure, and shared utilities to support maintainability and clear responsibility boundaries.

## Package Diagram

```mermaid
flowchart TB

    subgraph PRESENTATION["Presentation Layer"]
        direction LR
        PAGES["app/<br/>Pages and Layouts"]
        COMPONENTS["components/<br/>Reusable UI"]
    end

    subgraph APPLICATION["Application Layer"]
        direction LR
        AUTH["features/auth/<br/>Authentication"]
        LISTINGS["features/boarding-houses/<br/>Listing Use Cases"]
    end

    subgraph DOMAIN["Domain Layer"]
        direction LR
        MODELS["domain/models/<br/>User and BoardingHouse"]
        RULES["domain/rules/<br/>Listing and Verification Rules"]
        CONTRACTS["domain/repositories/<br/>Repository Interfaces"]
    end

    subgraph INFRASTRUCTURE["Infrastructure Layer"]
        direction LR
        REPOSITORIES["lib/repositories/<br/>Repository Implementations"]
        DATABASE["lib/db/<br/>Database Connection"]
    end

    subgraph SHARED["Shared Utilities"]
        direction LR
        VALIDATION["lib/validation/<br/>Input Validation"]
        TYPES["types/<br/>Shared Types"]
    end

    PAGES --> COMPONENTS
    PAGES --> AUTH
    PAGES --> LISTINGS

    AUTH --> CONTRACTS
    AUTH --> MODELS
    AUTH --> VALIDATION
    AUTH --> TYPES

    LISTINGS --> RULES
    LISTINGS --> CONTRACTS
    LISTINGS --> VALIDATION
    LISTINGS --> TYPES

    RULES --> MODELS
    CONTRACTS --> MODELS

    REPOSITORIES -. implements .-> CONTRACTS
    REPOSITORIES --> MODELS
    REPOSITORIES --> DATABASE

    PAGES --> TYPES

    classDef presentation fill:#E8F1FC,stroke:#6B93C8,color:#24364B,stroke-width:1.2px
    classDef application fill:#EEE9FA,stroke:#9884C5,color:#382D55,stroke-width:1.2px
    classDef domain fill:#E3F3E8,stroke:#78A889,color:#244A32,stroke-width:1.2px
    classDef infrastructure fill:#F8EBDD,stroke:#C59A70,color:#5A3D24,stroke-width:1.2px
    classDef shared fill:#F0F1F3,stroke:#9AA1AA,color:#343A40,stroke-width:1.2px

    class PAGES,COMPONENTS presentation
    class AUTH,LISTINGS application
    class MODELS,RULES,CONTRACTS domain
    class REPOSITORIES,DATABASE infrastructure
    class VALIDATION,TYPES shared

    style PRESENTATION fill:#F7FAFE,stroke:#B7CAE5,stroke-width:1px
    style APPLICATION fill:#FAF8FE,stroke:#CFC3E8,stroke-width:1px
    style DOMAIN fill:#F6FBF7,stroke:#B9D8C2,stroke-width:1px
    style INFRASTRUCTURE fill:#FFFAF5,stroke:#E4C9AE,stroke-width:1px
    style SHARED fill:#FAFAFB,stroke:#D3D6DA,stroke-width:1px
```

## Package Descriptions

- **Presentation Layer:** Contains application pages, layouts, and reusable user interface components.
- **Application Layer:** Coordinates authentication and boarding-house listing use cases.
- **Domain Layer:** Defines core domain models, business rules, and repository interfaces.
- **Infrastructure Layer:** Handles repository implementations and database connectivity.
- **Shared Utilities:** Provides reusable input-validation utilities and shared types.

## Dependency Key

- **Solid arrow (`-->`):** Indicates a dependency or usage relationship between packages.
- **Dashed arrow (`-.->`):** Indicates that a repository implementation fulfills a domain repository interface.

## Layering Rule

Dependencies should point toward application and domain abstractions where appropriate. Domain rules and repository interfaces must remain independent of presentation and database implementation details.

## Design Note

This is a proposed package structure for the project. Confirm the folders, framework conventions, and dependency relationships with the team and actual implementation before treating them as the final codebase structure.

## Intended Audience

Developers, system analysts, project advisers, and team members responsible for designing and maintaining the system architecture.

## Risk Reduced

Reduces the risk of unclear module responsibilities, tightly coupled components, and inconsistent handling of business rules and database operations.

## View Note

This diagram presents a proposed logical package structure and dependency relationships. The folder names and architecture may be revised based on the team's selected framework, approved requirements, and actual implementation.
