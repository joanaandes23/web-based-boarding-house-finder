# UML Component Diagram — Web-Based Boarding House Finder

**Project:** Web-Based Boarding House Finder  
**Team:** Fourward Devs  
**Block:** BSIS 4-1  
**School:** Sorsogon State University (SorSU), Bulan Campus

## Scope

This diagram presents the proposed logical components and interfaces of the Web-Based Boarding House Finder. It shows how the web interface accesses authentication, boarding-house listing, and listing verification functionality, and how these application components access persistent data through a repository interface.

## UML Component Diagram

```mermaid
flowchart TB

    UI["Web Application UI<br/>Pages and Components"]

    subgraph APP_INTERFACES["Application Interfaces"]
        direction LR
        AUTH_API(["IAuthentication"])
        LISTING_API(["IBoardingHouseListing"])
        VERIFY_API(["IListingVerification"])
    end

    subgraph APP_COMPONENTS["Application Components"]
        direction LR
        AUTH["Authentication<br/>Component"]
        LISTINGS["Boarding-House Listing<br/>Component"]
        VERIFY["Listing Verification<br/>Component"]
    end

    REPO_API(["IRepository"])

    subgraph DATA_LAYER["Data Access Layer"]
        direction TB
        REPO["Repository / Data Access<br/>Component"]
        DB[("PostgreSQL<br/>Database")]
    end

    UI --> AUTH_API
    UI --> LISTING_API
    UI --> VERIFY_API

    AUTH_API -. provided by .-> AUTH
    LISTING_API -. provided by .-> LISTINGS
    VERIFY_API -. provided by .-> VERIFY

    AUTH --> REPO_API
    LISTINGS --> REPO_API
    VERIFY --> REPO_API

    REPO_API -. implemented by .-> REPO
    REPO --> DB

    classDef ui fill:#E8F1FC,stroke:#6B93C8,color:#24364B,stroke-width:1.2px
    classDef app fill:#EEE9FA,stroke:#9884C5,color:#382D55,stroke-width:1.2px
    classDef iface fill:#F0F1F3,stroke:#9AA1AA,color:#343A40,stroke-width:1.2px
    classDef data fill:#E3F3E8,stroke:#78A889,color:#244A32,stroke-width:1.2px
    classDef database fill:#F8EBDD,stroke:#C59A70,color:#5A3D24,stroke-width:1.2px

    class UI ui
    class AUTH,LISTINGS,VERIFY app
    class AUTH_API,LISTING_API,VERIFY_API,REPO_API iface
    class REPO data
    class DB database

    style APP_INTERFACES fill:#FAFAFB,stroke:#D3D6DA,stroke-width:1px
    style APP_COMPONENTS fill:#FAF8FE,stroke:#CFC3E8,stroke-width:1px
    style DATA_LAYER fill:#F6FBF7,stroke:#B9D8C2,stroke-width:1px
```

## Component Descriptions

- **Web Application UI:** Presents the pages and reusable interface components used by students, boarding-house owners or managers, and administrators.
- **Authentication Component:** Handles registration, login, and authentication-related operations.
- **Boarding-House Listing Component:** Supports browsing, searching, filtering, viewing, comparing, and managing boarding-house listings.
- **Listing Verification Component:** Supports administrator review, approval, and requests for listing corrections.
- **Repository / Data Access Component:** Implements data access operations through the repository interface.
- **PostgreSQL Database:** Represents the proposed persistent data store for user accounts, boarding-house details, availability, and verification records.

## Interface Descriptions

- **IAuthentication:** Provides authentication-related functionality to the web interface.
- **IBoardingHouseListing:** Provides boarding-house listing functionality to the web interface.
- **IListingVerification:** Provides listing verification functionality to the web interface.
- **IRepository:** Defines the data access operations required by the application components and implemented by the repository component.

## Diagram Key

- **Solid arrow (`-->`):** Represents a usage or dependency relationship.
- **Dashed arrow (`-.->`):** Indicates which component provides or implements an interface, as identified by the arrow label.
- **Rounded interface nodes:** Represent named interfaces between components.

## Design Notes

- This diagram represents a proposed logical component architecture, not confirmation of the current implementation.
- PostgreSQL is shown as the proposed database technology and should remain consistent with the team's approved container and deployment diagrams.
- The named interfaces are conceptual contracts; their actual methods and endpoints should be defined during implementation.
- The application components may be implemented as modules within one web application rather than separate deployable services.
- Confirm the components, interfaces, and dependencies with the team before treating this diagram as final.
