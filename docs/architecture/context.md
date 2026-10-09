# C4 System Context Diagram

```mermaid
C4Context
title System Context Diagram - Web-Based Boarding House Finder

UpdateLayoutConfig($c4ShapeInRow="2", $c4BoundaryInRow="1")

Person(student, "Student", "Finds and compares boarding houses")
Person(owner, "Boarding-House Owner/Manager", "Manages listings and availability")
Person(admin, "Administrator", "Verifies listing information")

System(finder, "Web-Based Boarding House Finder", "Helps students find and compare boarding houses")

Rel(student, finder, "Searches and compares")
Rel(owner, finder, "Manages listings")
Rel(admin, finder, "Verifies information")

UpdateRelStyle(student, finder, $offsetX="-35", $offsetY="-35")
UpdateRelStyle(owner, finder, $offsetY="0")
UpdateRelStyle(admin, finder, $offsetY="60")
```

**Diagram Type:** C4 System Context Diagram

**Scope:** This diagram presents the Web-Based Boarding House Finder as a single system and shows its primary users and their interactions with it. It does not describe the system's internal components or database structure.

**Intended Audience:** SorSU Bulan Campus students, boarding-house owners or managers, administrators, project developers, and project evaluators.

**Risk Reduced:** This view helps reduce misunderstandings about the system boundary, its primary users, and the responsibilities of each user. It provides a shared understanding of who interacts with the system and why.

**View Note:** This is a high-level view of the proposed system. Internal application components, data storage, and technical deployment details are described in the corresponding architecture diagrams.
