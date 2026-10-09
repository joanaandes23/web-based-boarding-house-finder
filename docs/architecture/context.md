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
