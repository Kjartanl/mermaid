# Class diagram example

````Mermaid

classDiagram

    Vehicle <|-- Car
    Vehicle <|-- Plane
    Vehicle <|-- Ship

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