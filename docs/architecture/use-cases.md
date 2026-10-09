# UML Use Case Diagram

```mermaid
usecase-beta
direction LR

actor Student("Student")
actor Owner("Boarding-House Owner/Manager")
actor Admin("Administrator")

systemBoundary "Web-Based Boarding House Finder"
    Register("Register")
    Login("Log In")
    Browse("Browse Boarding Houses")
    Search("Search and Filter Boarding Houses")
    ViewDetails("View Boarding-House Details")
    Compare("Compare Boarding Houses")
    ManageListings("Manage Boarding-House Listings")
    VerifyInfo("Verify Boarding-House Information")
end

Student --> Register
Student --> Login
Student --> Browse
Student --> Search
Student --> ViewDetails
Student --> Compare

Owner --> Register
Owner --> Login
Owner --> ManageListings

Admin --> Login
Admin --> VerifyInfo
```

**Diagram Type:** UML Use Case Diagram

**Scope:** This diagram identifies the primary interactions available to students, boarding-house owners or managers, and administrators within the Web-Based Boarding House Finder.

**Intended Audience:** Students, owners or managers, administrators, developers, and project evaluators.

**Risk Reduced:** This view helps reduce ambiguity about user responsibilities and the system functions expected for each role. It can also help the team identify missing or incorrectly assigned use cases.

**View Note:** The diagram focuses on the proposed system's main use cases. It does not show the sequence of steps within each use case or the internal implementation. No `include` or `extend` relationships are shown because no such dependencies have been established here.
