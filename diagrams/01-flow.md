
# Flow chart example

````mermaid 
flowchart TD

    Start(Before we start...) --> IsDev{Are you a developer?}
    IsDev -->|Yes| Great[Great!]

    Great --> IsArch{Do you prefer <br>just coding, or can I interest you <br> in architecture design too?}

    IsDev --> |No| IsDevFalse[Ok, no problem!]

    IsArch --> |Just plain coding for me please!| IsArchFalse[Ok.]
    IsArch --> |Sure, I love architecture!| Welcome

    IsArchFalse --> CanChange{Will you<br />permit me to try to<br />change your mind?}
    CanChange --> |Ok, you get one chance!| Great

    IsDevFalse --> IsInterested{But you are <br>interested in technology<br>and innovation, right?}

    CanChange --> |Forget it!| Goodbye
    IsInterested ---> |Of course!| Welcome["`**Welcome to my talk!**`"]
    IsInterested --> |Nope.| Goodbye[Ok. The door is over there.<br />Have a nice day!]

```` 