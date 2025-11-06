# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="600" height="914" alt="image" src="https://github.com/user-attachments/assets/ca85d65c-2800-42d0-b5cf-7e4e529ee0c0" />


### Entities and Attributes

| Entity     | Attributes (PK, FK)                                       | Notes                                                 |
| ---------- | --------------------------------------------------------- | ----------------------------------------------------- |
| Member     | MemberID (PK), Name, MembershipType, StartDate            | Each member has unique ID                             |
| Program    | ProgramID (PK), ProgramName, Duration                     | Each program can have multiple trainers and members   |
| Trainer    | TrainerID (PK), Name, Specialization, ContactInfo         | Trainers can be assigned to multiple programs         |
| Session    | SessionID (PK), Date, Time, MemberID (FK), TrainerID (FK) | Represents booked sessions between member and trainer |
| Attendance | AttendanceID (PK), SessionID (FK), MemberID (FK), Status  | Resolves M:N between Member and Session               |
| Payment    | PaymentID (PK), MemberID (FK), Amount, Date, Type         | Tracks payments for memberships or sessions           |


### Relationships and Constraints

| Relationship                  | Cardinality                   | Participation            | Notes                                                 |
| ----------------------------- | ----------------------------- | ------------------------ | ----------------------------------------------------- |
| Member – Payment              | 1:N                           | Total on Payment side    | One member can make multiple payments                 |
| Member – Session              | 1:N                           | Total on Session side    | One member can book multiple sessions                 |
| Trainer – Session             | 1:N                           | Total on Session side    | One trainer can handle many sessions                  |
| Member – Attendance – Session | M:N (resolved via Attendance) | Total on Attendance side | Attendance connects members and sessions              |
| Trainer – Program             | M:N                           | Partial on both sides    | Trainers can conduct multiple programs and vice versa |
| Member – Program              | M:N                           | Partial on both sides    | Members can join multiple programs                    |


### Assumptions
Each member has a unique MemberID.

Payments for membership and sessions are both recorded in one table.

Attendance is only tracked for scheduled sessions.

Trainers can handle multiple programs.

Members can join multiple programs.

Programs may have multiple trainers concurrently.

All payments are assumed to be successful (no failed transactions).

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1335" height="943" alt="image" src="https://github.com/user-attachments/assets/f28760a5-86f5-448f-851a-66576569f2f3" />


### Entities and Attributes

| Entity            | Attributes (PK, FK)                                                       | Notes                                           |
| ----------------- | ------------------------------------------------------------------------- | ----------------------------------------------- |
| Member            | MemberID (PK), Name, Address, Phone                                       | Each member has a unique ID                     |
| Book              | BookID (PK), ISBN, Title, Author, Category                                | A book can be borrowed multiple times           |
| Loan              | LoanID (PK), LoanDate, ReturnDate, FineAmount, MemberID (FK), BookID (FK) | Resolves M:N between Member and Book            |
| Event             | EventID (PK), Title, Description, Date, Time, RoomID (FK)                 | Each event occurs in one room                   |
| EventRegistration | RegistrationID (PK), RegistrationDate, MemberID (FK), EventID (FK)        | Resolves M:N between Member and Event           |
| Speaker           | SpeakerID (PK), Name, Expertise                                           | Each speaker may participate in multiple events |
| Room              | RoomID (PK), RoomName, Type, Capacity                                     | Each event is assigned to one room              |


### Relationships and Constraints

| Relationship                       | Cardinality                          | Participation                   | Notes                                 |
| ---------------------------------- | ------------------------------------ | ------------------------------- | ------------------------------------- |
| Member – Loan                      | 1:N                                  | Total on Loan side              | Each loan belongs to one member       |
| Loan – Book                        | N:1                                  | Total on Loan side              | Each loan involves one book           |
| Member – Book (via Loan)           | M:N (resolved via Loan)              | Total via Loan                  | Many members can borrow many books    |
| Member – EventRegistration – Event | M:N (resolved via EventRegistration) | Total on EventRegistration side | Members register for multiple events  |
| Event – Speaker                    | M:N                                  | Partial on both sides           | Events can have multiple speakers     |
| Event – Room                       | 1:N                                  | Total on Event side             | Each event occurs in exactly one room |
| Room – Event                       | 1:N                                  | Partial on Room side            | A room can host multiple events       |


### Assumptions
Each member and book has a unique ID.

FineAmount is calculated only for overdue returns.

Registration must occur before the event date.

Each event takes place in exactly one room.

An event can have multiple speakers.

A room’s capacity limits event registrations.

Speakers can present at multiple events.

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1110" height="857" alt="image" src="https://github.com/user-attachments/assets/f6cb9fc7-42fa-48a5-a1b1-3ca44065354e" />


### Entities and Attributes

| Entity      | Attributes (PK, FK)                                                                      | Notes                                        |
| ----------- | ---------------------------------------------------------------------------------------- | -------------------------------------------- |
| Customer    | CustomerID (PK), Name, PhoneNo, Email                                                    | Each customer can make multiple reservations |
| Table       | TableID (PK), Capacity, Location                                                         | Each table can be reserved multiple times    |
| Reservation | ReservationID (PK), Date, Time, NoOfGuests, CustomerID (FK), TableID (FK), WaiterID (FK) | Represents table booking by a customer       |
| Waiter      | WaiterID (PK), Name, Phone                                                               | A waiter serves multiple reservations        |
| Order       | OrderID (PK), OrderTime, ReservationID (FK), CustomerID (FK)                             | Orders are linked to reservations            |
| Dish        | DishID (PK), DishName, Category, Price                                                   | Each dish belongs to a specific category     |
| OrderDetail | OrderID (PK, FK), DishID (PK, FK), Quantity                                              | Resolves M:N between Order and Dish          |
| Bill        | BillID (PK), ReservationID (FK), Amount, ServiceCharge                                   | One bill per reservation                     |


### Relationships and Constraints

| Relationship                   | Cardinality                    | Participation             | Notes                                      |
| ------------------------------ | ------------------------------ | ------------------------- | ------------------------------------------ |
| Customer – Reservation         | 1:N                            | Total on Reservation side | One customer can make many reservations    |
| Reservation – Table            | 1:N                            | Total on Reservation side | A table can be reserved many times         |
| Waiter – Reservation           | 1:N                            | Total on Reservation side | A waiter can serve multiple reservations   |
| Reservation – Order            | 1:N                            | Total on Order side       | Each reservation can place multiple orders |
| Order – Dish (via OrderDetail) | M:N (resolved via OrderDetail) | Total on OrderDetail side | Multiple dishes per order                  |
| Reservation – Bill             | 1:1                            | Total on both sides       | One bill per reservation                   |


### Assumptions
Each reservation is linked to a specific customer and table.

A reservation cannot exceed the table’s capacity.

Each reservation is served by exactly one waiter.

Orders are tied to reservations (no walk-in orders tracked).

A single bill is generated per reservation.

Each dish has a unique ID and fixed price during ordering.

Waiters can handle multiple reservations at once.

