
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

**Note:** This is a proposed conceptual design. Confirm that the attributes and relationships match the team's agreed requirements and actual implementation before treating them as implemented database fields.
