
# Flow chart example

````mermaid 
flowchart TD

    Beginning(Before we start...) --> IsDev{Are you a developer?}

    IsDev -->|Yepp!| Great[Great!]

    IsDev --> |No| IsDevFalse[Ok, no problem!]

    Great --> LikesArchitecture{Do you prefer <br>just coding, or can I interest you <br> in architecture design too?}

    LikesArchitecture --> |Just plain coding for me please!| IsArchFalse[Ok.]

    IsArchFalse --> CanChange{Will you<br />permit me to try to<br />change your mind?}
    CanChange --> |Ok, you get one chance!| Great

    IsDevFalse --> IsInterested{But you are <br>interested in technology<br>and innovation, right?}

    LikesArchitecture --> |Sure, I love architecture!| Welcome
    IsInterested ---> |Of course!| Welcome["`**Welcome to my talk!**`"]

    CanChange --> |Forget it!| Goodbye
    IsInterested --> |Nope.| Goodbye[Ok. The door is over there.<br />Have a nice day!]

```` 