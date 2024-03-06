# Sequence Diagram Example

The flow of control and information for a hypothetical use case:

```mermaid
sequenceDiagram

###########################
### Define the participants 

participant U as user
   
box Front end
    participant FE as GUI / WebPage / App?
end

box Middle Tier
    participant Auth as User Auth Service
    participant Svc as Primary Service
    participant Cc as Click Count Service
    participant Dal as Data Access Service
end

box Back End
    participant DB as Data Storage
end

###########################
### User logs in 

U->>+FE: Log in
FE->>+Auth: LogIn(UserId)
Auth->>Auth: AuthenticateUser(UserId)
Auth->>Dal: GetUserRoles()
Dal->>DB: GetUserRoles()
DB-->>Dal: List<Roles>
Dal-->>Auth: List<Roles>
Auth->>Auth: GenerateAccessToken()
Auth-->>-FE: Return AccessToken
FE-->>-U: Return AccessToken and display message <br />"Please don't click this button"

U->>+FE: Clicks button 
FE->>+Svc: RegisterClick(userId)

Svc->>+Auth: CheckUserAccess(token)
alt Invalid Token
    Auth-->>Svc: False
    Svc-->>FE: Access denied!
    FE-->>U: Respond: "Please log in!"

else Valid Token

    Auth-->>-Svc: True

    Svc->>+Cc: GetUserClickCount(userId)
    Cc->>+Dal: GetClickCount(userId)
    Dal->>+DB: SelectClickCount(userId)
    DB-->>-Dal: Return Number
    Dal-->>-Cc: Return NrOfClicks 
    Note right of Cc: Return the nr of clicks <br /> the user so far.
    Cc-->>-Svc: Return NrOfClicks

    alt NrOfClicks = 0
        Svc->>+Cc: IncrementClickCount(userId)
        Cc->>+Dal: IncrementClickCount(userId)
        Dal->>+DB: UpdateClickCount(userId)
        Svc-->>FE: Return status: UPDATE_WARNING
        FE-->>U: Display message:<br />"DO NOT CLICK THIS BUTTON AGAIN!"
    else NrOfClicks > 0
        Svc->>Auth: ReportUser(userId)
        Auth->>Auth: InvalidateToken()
        Svc->>+Cc: IncrementClickCount(userId)
        Cc->>+Dal: IncrementClickCount(userId)
        Dal->>+DB: UpdateClickCount(userId)
        Svc-->>-FE: Return status: USER_LOGGED_OUT
        FE-->>-U: Display message:<br />"You have been logged out."
    end
end
```