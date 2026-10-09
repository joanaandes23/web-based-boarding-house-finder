# Sequence Diagram – Listing Submission and Verification

This sequence diagram illustrates the submission and verification of boarding-house listings in the Web-Based Boarding House Finder. It shows how the Owner/Manager submits listing details, how the Web Application and Listing API Route validate and store the information in PostgreSQL, and how the Administrator reviews the listing. Alternative flows cover invalid details, approval, and correction with resubmission.

```mermaid
sequenceDiagram
    title Listing Submission and Verification
    autonumber

    actor Owner as Boarding-House Owner/Manager
    participant Web as Web Application
    participant API as Listing API Route
    participant DB as PostgreSQL Database
    actor Admin as Administrator

    Owner->>Web: Enter listing details and submit
    Web->>API: Submit listing details
    API->>API: Validate required fields

    alt Listing details are invalid
        API-->>Web: Return validation errors
        Web-->>Owner: Display validation errors
    else Listing details are valid
        API->>DB: Save listing as PendingVerification
        DB-->>API: Return saved listing and ID
        API-->>Web: Return submission confirmation
        Web-->>Owner: Display pending verification status

        loop Until listing is verified
            Admin->>Web: Open pending listings
            Web->>API: Request pending listings
            API->>DB: Fetch pending listings
            DB-->>API: Return pending listing records
            API-->>Web: Return pending listings
            Web-->>Admin: Display pending listings

            Admin->>Web: Review listing and submit decision
            Web->>API: Send verification decision

            alt Listing is approved
                API->>DB: Set status to Verified
                DB-->>API: Confirm status update
                API-->>Web: Return verification result
                Web-->>Admin: Display verified status
            else Listing needs correction
                API->>DB: Set status to NeedsCorrection and save notes
                DB-->>API: Confirm status update
                API-->>Web: Return correction-required status
                Web-->>Owner: Notify owner of required corrections

                Owner->>Web: Open listing and correction notes
                Web->>API: Request listing details and notes
                API->>DB: Fetch listing and correction notes
                DB-->>API: Return listing details and notes
                API-->>Web: Return listing and notes
                Web-->>Owner: Display required corrections

                Owner->>Web: Edit and resubmit listing
                Web->>API: Submit corrected listing
                API->>API: Validate corrected details
                API->>DB: Update listing and set status to PendingVerification
                DB-->>API: Confirm resubmission
                API-->>Web: Return resubmission confirmation
                Web-->>Owner: Display pending verification status
            end
        end
    end
```

**Diagram Type:** UML Sequence Diagram

**Scope:** This diagram shows the interactions involved in submitting a boarding-house listing, validating its details, storing it, reviewing it, and handling approval or correction with resubmission.

**Intended Audience:** Project developers, system designers, boarding-house owners or managers, administrators, and project evaluators.

**Risk Reduced:** This view helps reduce misunderstandings about the order of system interactions, validation responses, database updates, and the handling of listings that require correction.

**Key:**
- Solid arrows (`->>`) represent requests or messages.
- Dashed arrows (`-->>`) represent replies or returned results.
- `alt` represents alternative outcomes, including invalid versus valid details and approval versus correction.
- `loop` represents the repeated review process until the listing is verified.

**Architecture Note:** The Listing API Route is modeled as an internal application component, while PostgreSQL is the database. Confirm that these match the architecture agreed upon by the team.

**View Note:** This diagram describes the intended interaction flow. It does not independently confirm that the implementation behaves exactly as shown.
