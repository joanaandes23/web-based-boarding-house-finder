# Use Case Diagram — Web-Based Boarding House Finder

This diagram shows the main interactions between students, boarding-house owners/managers, and the administrator in the Web-Based Boarding House Finder system.

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

Key: Each solid line represents an association between an actor and a use case.
