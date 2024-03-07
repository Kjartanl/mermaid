# Class diagram example

````Mermaid

classDiagram

    class ISomeInterface{
        <<interface>>
        DoWork()
    }

    class Alpha{
        Id
        PrimaryValue
        DoWork()
    }

    class Beta{
        Id
        OtherValue
        DoWork()
        DoSomethingElse()
    }

    class Gamma{
        Id
        OtherValue
        DoWork()
        DoSomethingElse()
    }

    class Delta{
        Id
        OtherValue
        DoWork()
        DoSomethingElse()
    }

    class Iota {
        Id
        OtherValue
        DoWork()
        DoSomethingElse()
    }

    Alpha --|> ISomeInterface
    Beta --|> ISomeInterface
    Delta --* Gamma : Composition
    Iota --o Gamma : Aggregation
    Delta -- Beta : linked
    Delta ..> Alpha : dependency

```` 