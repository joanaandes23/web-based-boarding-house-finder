
# Activity Diagram – Web-Based Boarding House Finder

This activity diagram illustrates the workflow for submitting and verifying boarding-house listings and searching for suitable boarding houses. It includes the Owner/Manager, Administrator, System, and Student swimlanes.

```mermaid
flowchart TB

    subgraph Owner["1. Boarding-House Owner/Manager"]
        direction TB
        O1([Start])
        O2["Add or update listing details"]
        O3["Submit listing for verification"]
        O4["Correct listing details"]
        O1 --> O2 --> O3
        O4 --> O3
    end

    subgraph Admin["2. Administrator"]
        direction TB
        A1["Review listing information"]
        A2{"Information accurate and complete?"}
        A3["Request listing correction"]
        A1 --> A2
        A2 -->|No| A3
    end

    subgraph System["3. Web-Based Boarding House Finder System"]
        direction TB
        S1["Save listing as pending verification"]
        S2["Make verified listing searchable"]
        S3["Process student search and filters"]
        S4{"Matching listings found?"}
        S5["Display matching listings"]
        S6["Display no matching listings"]
        S1 ~~~ S2
        S2 ~~~ S3
        S3 --> S4
        S4 -->|Yes| S5
        S4 -->|No| S6
    end

    subgraph Student["4. Student"]
        direction TB
        T1["Search or filter boarding houses"]
        T2["View boarding-house details"]
        T3["Compare boarding houses"]
        T4["Adjust search filters"]
        T5["Select a suitable option"]
        E([End])
        T1 --> T2 --> T3 --> T5 --> E
        T4 --> T1
    end

    O3 --> S1
    S1 --> A1
    A2 -->|Yes| S2
    A3 --> O4
    S2 --> T1
    T1 --> S3
    S5 --> T2
    S6 --> T4

    Owner ~~~ Admin
    Admin ~~~ System
    System ~~~ Student
```

Key:
- `Yes` – The listing information is accurate and complete, or matching boarding houses are found.
- `No` – The listing needs correction, or no matching boarding houses are found.
- The correction loop returns the listing to the Owner/Manager.
- The search loop allows the Student to adjust filters and search again.
