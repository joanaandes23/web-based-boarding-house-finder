# UML Use Case Diagram

```mermaid id="uc3b9m"
flowchart LR
    Student([Student])
    Owner([Boarding-House Owner/Manager])
    Admin([Administrator])

    subgraph System["Web-Based Boarding House Finder"]
        UC1([Register])
        UC2([Log In])
        UC3([Browse Boarding Houses])
        UC4([Search and Filter Boarding Houses])
        UC5([View Boarding-House Details])
        UC6([Compare Boarding Houses])
        UC7([Manage Boarding-House Listings])
        UC8([Update Listing Details and Availability])
        UC9([Verify Boarding-House Information])
    end

    Student --- UC1
    Student --- UC2
    Student --- UC3
    Student --- UC4
    Student --- UC5
    Student --- UC6

    Owner --- UC1
    Owner --- UC2
    Owner --- UC7
    Owner --- UC8

    Admin --- UC2
    Admin --- UC9
```

**Diagram Type:** UML Use Case Diagram

**Scope:** This diagram identifies the primary interactions available to students, boarding-house owners or managers, and administrators within the Web-Based Boarding House Finder.

**Intended Audience:** Students, owners or managers, administrators, developers, and project evaluators.

**Risk Reduced:** This view helps reduce ambiguity about user responsibilities and the system functions expected for each role. It can also help the team identify missing or incorrectly assigned use cases.

**View Note:** The diagram focuses on the proposed system's main use cases. It does not show the sequence of steps within each use case or the internal implementation. No `include` or `extend` relationships are shown because no such dependencies have been established here.
