# Metadata for FIXM

## GUFI

### Assumptions:
- The GUFI is an unaltered ISO UUID v4
- There is a need to record and exchange the time at which the GUFI was generated to support some traceability objectives and to help simplify the process for confirming a GUFI is unique over some timeframe.    
- There is a need to record and exchange information about the GUFI origination process

### Leveraging the ISO 19115 standard 
The ISO 19115-1 standard defines the schema required for describing geographic information and services by means of metadata. It provides information about the identification, the extent, the quality, the spatial and temporal aspects, the content, the spatial reference, the portrayal, distribution, and other properties of digital geographic data and services.

The ISO 19115-1 defines in particular `Lineage` data structures that support the provision of metadata concerning the sources and production processes used in producing a resource.

These data structures may be considered for exchanging information about the sources and production processes used in producing the GUFI, in line with the candidate requirements above.

The next chapter explore how these ISO 19115-1 structures could be used in FIXM. 

### Coding examples

#### General approach
- Do not import the ISO 19115 schema which is known for its complexity (i.e. self-references) which make it difficult to implement.
- Instead, mimic the relevant ISO 19115 data structures into the Base package of FIXM (xmlns:fb="http://www.fixm.aero/base/4.3") 
- Preserve the ISO 19115 semantics, to ensure semantic alignement of FIXM with this ISO standard and the AIRM (the AIRM uses ISO 19115)  

#### Example 1
The GUFI is generated directly by the eAU hen creating the first Filed FLight Plan or Preliminary Flight Plan for a given flight.
No third-party service is used for the generation of the GUFI.

##### OPTION 1 
Use a generic property defined under `fx:Flight` called `flightMetadata`. This property is of type `Metadata`, which mimics the ISO 19115 `MD_Metadata` data element.   

```xml
<ffice:FficeMessage xmlns:ffice="http://www.fixm.aero/app/ffice/1.1" xmlns:fx="http://www.fixm.aero/flight/4.3" xmlns:fb="http://www.fixm.aero/base/4.3">
  <ffice:flight>
    <fx:flightMetadata>
      <fb:resourceLineage>
        <fb:processStep>
          <fb:description>GUFI Origination</fb:description>
          <fb:processor>
            <fb:organisationName>My Organisation</fb:organisationName>
          </fb:processor>
          <fb:source>
            <fb:sourceCitation>
              <fb:onlineResource>
                <fb:linkage>https://eur-registry.swim.aero/services/uuid_generation_service</fb:linkage>
                <fb:name>UUID Generation Service</fb:name>
              </fb:onlineResource>
            </fb:sourceCitation>
          </fb:source>
          <fb:stepDateTime>2020-09-01T00:00:00Z</fb:stepDateTime>					
        </fb:processStep>
      </fb:resourceLineage>
    </fx:flightMetadata>
    <fx:gufi codeSpace="urn:uuid">AAAAAAAA-AAAA-4AAA-8AAA-AAAAAAA23041</fx:gufi>
  </ffice:flight>	
  <ffice:type>FILED_FLIGHT_PLAN</ffice:type>
</ffice:FficeMessage>
```
OPTION 2
