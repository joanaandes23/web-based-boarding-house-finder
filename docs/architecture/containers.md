# C4 Container Diagram

```mermaid
C4Container
title Container Diagram - Web-Based Boarding House Finder

UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")

Person(student, "Student", "Finds and compares boarding houses")
Person(owner, "Boarding-House Owner/Manager", "Manages listings")
Person(admin, "Administrator", "Verifies listing information")

System_Boundary(system, "Web-Based Boarding House Finder") {
    Container(web, "Web Application", "Next.js", "User interface, search, comparison, listing management, and verification")
    ContainerDb(database, "Database", "PostgreSQL", "Stores user accounts and boarding-house records")
}

Rel_D(student, web, "Searches / compares")
Rel_D(owner, web, "Manages listings")
Rel_D(admin, web, "Verifies listings")
Rel_R(web, database, "Reads / writes data, "Database connection")

UpdateRelStyle(student, web, $offsetX="-1", $offsetY="-35")
UpdateRelStyle(owner, web, $offsetX="53", $offsetY="-45")
UpdateRelStyle(admin, web, $offsetX="104", $offsetY="-35")
UpdateRelStyle(web, database, $offsetX="-50", $offsetY="-23")
```

**Diagram Type:** C4 Container Diagram

**Scope:** This view describes the proposed high-level technical structure of the Web-Based Boarding House Finder, including its web application and database. It shows how the three main user roles interact with the application and how the application accesses stored information.

**Intended Audience:** Project developers, system designers, technical evaluators, and project stakeholders who need to understand the system's main technical building blocks.

**Risk Reduced:** This view helps reduce ambiguity about the system's internal structure, the responsibility of each container, and the application's relationship with persistent data storage.

**Assumptions and Limitations:** Next.js and PostgreSQL are proposed technologies and must be confirmed against the team's actual implementation. This diagram does not describe deployment infrastructure, detailed application modules, or database table relationships.
