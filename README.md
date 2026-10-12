# eduhub## 2. Sơ đồ lớp (Class Diagram)

```mermaid
classDiagram
    class Member {
        +Guid Id
        +string Name
        +string Email
        +string StudentCode
        +DateTime JoinedAt
        +Create()
    }
    class Club {
        +Guid Id
        +string Name
        +IReadOnlyList~Member~ Members
        +Create()
        +AddMember()
    }
    class Event {
        +Guid Id
        +Guid ClubId
        +string Title
        +DateTime Date
        +int Capacity
        +Create()
        +HasCapacity()
    }
    class Registration {
        +Guid Id
        +Guid MemberId
        +Guid EventId
        +RegistrationStatus Status
        +Create()
        +Confirm()
        +Cancel()
    }
    class CheckIn {
        +Guid Id
        +Guid RegistrationId
        +DateTime CheckedInAt
        +Create()
    }

    Club "1" --> "*" Event : ClubId
    Member "1" --> "*" Registration : MemberId
    Event "1" --> "*" Registration : EventId
    Registration "1" --> "0..1" CheckIn : RegistrationId
