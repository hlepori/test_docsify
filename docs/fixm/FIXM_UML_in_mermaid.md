## Flight.Aircraft

```mermaid
classDiagram
class AircraftType
AircraftType : CountPositive [0..1]+numberOfAircraft
AircraftType : AircraftTypeExtension [0..*]+extension
AircraftType --> AircraftTypeChoice : [0..1]+type
link AircraftType "https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AircraftTypeType.html" "Go to XML definition"
class WakeTurbulenceCategory
<<enumeration>> WakeTurbulenceCategory
WakeTurbulenceCategory : L
WakeTurbulenceCategory : M
WakeTurbulenceCategory : H
WakeTurbulenceCategory : J
link WakeTurbulenceCategory "https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_WakeTurbulenceCategoryType.html" "Go to XML definition"
class AircraftApproachCategory
<<enumeration>> AircraftApproachCategory
AircraftApproachCategory : A
AircraftApproachCategory : B
AircraftApproachCategory : C
AircraftApproachCategory : D
AircraftApproachCategory : E
AircraftApproachCategory : H
link AircraftApproachCategory "https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AircraftApproachCategoryType.html" "Go to XML definition"
class AircraftTypeChoice
<<choice>> AircraftTypeChoice
AircraftTypeChoice : AircraftTypeDesignator +icaoAircraftTypeDesignator
AircraftTypeChoice : CharacterString +otherAircraftType
link AircraftTypeChoice "https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AircraftTypeChoiceType.html" "Go to XML definition"
class Aircraft
Aircraft : CharacterString [0..1]+coloursAndMarkings
Aircraft : AircraftAddress [0..1]+aircraftAddress
Aircraft --> AircraftApproachCategory : [0..1]+aircraftApproachCategory
Aircraft --> AircraftType : [0..*]+aircraftType
Aircraft --> FlightCapabilities : [0..1]+capabilities
Aircraft : FormationCount [0..1]+formationCount
Aircraft : List~AircraftRegistration~ [0..1]+registration
Aircraft --> WakeTurbulenceCategory : [0..1]+wakeTurbulence
Aircraft : AircraftExtension [0..*]+extension
link Aircraft "https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AircraftType.html" "Go to XML definition"
class FlightCapabilities
FlightCapabilities : FlightCapabilitiesExtension [0..*]+extension
FlightCapabilities : CommunicationCapabilities [0..1]+communication
FlightCapabilities : NavigationCapabilities [0..1]+navigation
FlightCapabilities : StandardCapabilitiesIndicator [0..1]+standardCapabilities
FlightCapabilities : SurveillanceCapabilities [0..1]+surveillance
FlightCapabilities : SurvivalCapabilities [0..1]+survival
link FlightCapabilities "https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_FlightCapabilitiesType.html" "Go to XML definition"
```

