# Class diagram example

````Mermaid

classDiagram

    Vehicle : ID
    Vehicle : MaxSpeed
    Vehicle: Travel()

    class Car{
        RegNr
        EngineType
    }

    class Plane{
        MaxCruisingAltitude
        Model
    }

    class Ship{
        MaxTonnage
    }
    
    Vehicle <|-- Car
    Vehicle <|-- Plane
    Vehicle <|-- Ship
