
# Class Diagram — Web-Based Boarding House Finder

**Project:** Web-Based Boarding House Finder  
**Team:** Fourward Devs  
**Block:** BSIS 4-1  
**School:** Sorsogon State University (SorSU), Bulan Campus

## Scope

This class diagram presents the core domain classes of the Web-Based Boarding House Finder, including user roles, boarding-house information, address details, and listing verification records.

```mermaid
classDiagram
    direction TB

    class User {
        +int userId
        +String fullName
        +String email
        +String passwordHash
        +UserRole role
    }

    class BoardingHouse {
        +int boardingHouseId
        +String title
        +String description
        +Decimal monthlyRent
        +String livingConditions
        +AvailabilityStatus availability
        +ListingStatus listingStatus
        +DateTime createdAt
        +DateTime updatedAt
    }

    class Address {
        +int addressId
        +String streetAddress
        +String barangay
        +String municipality
        +String province
    }

    class ListingReview {
        +int reviewId
        +VerificationDecision decision
        +String notes
        +DateTime reviewedAt
    }

    class UserRole {
        <<enumeration>>
        STUDENT
        OWNER_MANAGER
        ADMINISTRATOR
    }

    class AvailabilityStatus {
        <<enumeration>>
        AVAILABLE
        FULL
        UNKNOWN
    }

    class ListingStatus {
        <<enumeration>>
        DRAFT
        PENDING_VERIFICATION
        VERIFIED
        NEEDS_CORRECTION
        INACTIVE
    }

    class VerificationDecision {
        <<enumeration>>
        APPROVED
        NEEDS_CORRECTION
    }

    User "1" --> "0..*" BoardingHouse : owns or manages
    BoardingHouse "1" *-- "1" Address : has location
    BoardingHouse "1" --> "0..*" ListingReview : has review history
    User "1" --> "0..*" ListingReview : reviews as administrator

    User ..> UserRole : uses
    BoardingHouse ..> AvailabilityStatus : uses
    BoardingHouse ..> ListingStatus : uses
    ListingReview ..> VerificationDecision : uses

    note for ListingReview "Only users with the ADMINISTRATOR role may create reviews."
```

## Design Constraints

- Only users with the `ADMINISTRATOR` role may create listing reviews.
- Each boarding house has one owner or manager and one address.
- A boarding house may have multiple listing reviews over time.
- The enumerations define the allowed user roles, availability values, listing statuses, and verification decisions.

## Intended Audience

Project developers, system designers, database designers, and project evaluators who need to understand the system's core domain entities, attributes, relationships, and allowed status values.

## Risk Reduced

This view helps reduce ambiguity about the system's data model, the relationships between users and boarding houses, the recording of listing verification history, and the allowed values for roles and statuses.

## View Note

This is a proposed conceptual design. The class attributes, associations, and constraints should be checked against the team's agreed requirements and actual implementation. The administrator-only review rule is a role constraint that must be enforced by the application.
