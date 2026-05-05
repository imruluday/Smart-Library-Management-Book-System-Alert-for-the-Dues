# Smart-Library-Management-Book-System-Alert-for-the-Dues

## Group Name: Team Tech

## Project Members

1. Gazi Shariar Alam – 2232629042
2. Imrul Kayes Uday – 2231002042
3. Maisha Subat – 2231161042
   

## Course
Software Engineering

## Project Description

The **Smart Library Management & Book System** is a software system designed to manage library activities efficiently. The system allows librarians to manage books, register users, issue and return books, and track borrowing records.

A special feature of this system is the **Due Alert Notification System**, which alerts users when the return date of a borrowed book is near or overdue. This helps students avoid late submission and helps the library maintain proper records.

## Main Features

 Book Management (Add, Update, Delete Books)
 Student/User Registration
 Book Issue and Return System
 Due Date Tracking
 Due Alert Notification System
 Book Search System


## Future Improvements

Email Notification for Due Dates
 Online Book Reservation
 Admin Dashboard

## GitHub Repository

## Final Project Report 
Proposed Functional Requirements: 
1. User Management: The system must allow administrators to register, update, and delete member and staff accounts. 
2. Catalog Management: Librarians must be able to add, update, and remove library items (Books, Journals, DVDs). 
3. Search and Filter: Users must be able to search for items by title, author, genre, or publication year. 
4. Transaction Processing: The system must handle the checking out, returning, and renewing of items. 
5. Hold/Reserve System: Patrons must be able to place a hold on an unavailable item and receive notifications when it is returned. 
6. Fine Management: The system must automatically calculate overdue fines based on the user's membership type and the item's delay period.

Completed Functional Requirements:
1. User Management System: 
Code: 
UI: 

2. Catalog Management: 
Code:
UI:  

3. Search & Filter: Not completed 

4. Transaction Processing 
Code:
UI: 

5. Hold/Reserve System: Not completed 

6. Fine Management:
Code:
UI: 

Non-Functional Requirements: 
1. Performance: The system should return search queries in under 2 seconds. 
2.  Security: Passwords must be encrypted, and unauthorized users must not be able to access staff-only portals. 
3. Scalability: The system must support up to 10,000 concurrent users and a catalog of over 500,000 items. 
4.  Reliability: The system should have an uptime of 99.9%

Completed non-functional requirements: 

1. Performance: 
Code: 
 






2. Security:
 







3. Scalability: 
 
4. Reliability: 
 
Strategy Design Pattern:
 
 
This design pattern is used to calculate fine algorithms. It has FineCalculator class that has different strategies. StandardFine strategy is instantiated and used to calculate the fine according to daysLate. This allows the library to swap logic without changing much inventory logic. 

Observer Design Pattern
 
 
 
 
 
 
This design pattern is used for notification systems in the application. While it mentions for “Book Availability,” the code demonstrates it through an email notification system. While registering, the system sends emailNotifier.sendVerificationEmail asynchronously. This decouples the registration logic from the notification delivery mechanism.
Factory Design Pattern
 
 
The library item creation is created by factory design pattern. It has ItemFactory class which includes createItem method and it takes an itemType string (e.g., "BOOK") and returns the corresponding object (e.g., new Book(title)). This encapsulates object creation, allowing the system to support new media types (DVDs, Journals) without modifying the admin dashboard logic.
Decorator Design Pattern (Premium Features)
 
 
 
This design pattern is designed for premium account features. An AccountDecorator class implements the MemberAccount interface and wraps a decoratedAccount object. This is used to "wrap" standard users with Premium behaviors, such as the extendBook functionality, which allows specific members to add 7 days to their due date.
Repository Design Pattern (Database Access)
 
 
 
The system uses Spring Data JPA's Repository pattern. Interfaces like MemberRepository extend JpaRepository, abstracting complex SQL queries into simple method calls like findByEmail or save.

Singleton Design Pattern
 
This design pattern identifies for the DatabaseManager to ensure a single shared connection instance. Additionally, the LibraryApiController utilizes static shared members like totalFinesCollected and a notifications list to maintain global state across the application.

Diagram vs. Implementation Analysis

Class Diagram Match:
•	Strategy Pattern: The diagram shows a FineStrategy interface with a StandardFine implementation. This matches the code exactly, where FineCalculator sets a strategy of type StandardFine. 
•	Singleton Pattern: The diagram lists DatabaseManager with a static instance and getInstance() method. This aligns with the architectural goal of preventing resource exhaustion by sharing a single connection. 
•	Changes: The Class Diagram illustrates a MediaCreator and BookCreator hierarchy for the Factory pattern. However, the actual implementation uses a simplified Static Factory (ItemFactory) with a switch-case/if-else block rather than a full class inheritance structure for the creators. 

Sequence Diagram Match:
•	Borrowing Process: The sequence diagram shows the Patron requesting a book through the System UI, which then communicates with an AuthProxy and InventoryMgr. 
•	Changes:
o	Proxy Logic: While the diagram depicts a separate AuthProxy object, the implementation shows role-based access checks (e.g., checking for "PREMIUM") directly within the Controller methods using the HttpSession. 
o	Inventory Management: The "InventoryMgr" in the diagram is implemented via the itemRepository in the code. The code successfully follows the sequence of checking item availability, updating status to "Borrowed," and saving the transaction to the database. 


https://github.com/imruluday/Smart-Library-Management-Book-System-Alert-for-the-Dues
