# Metadata for FIXM

## GUFI

```xml
<ffice:FficeMessage xmlns:ffice="http://www.fixm.aero/app/ffice/1.0" xmlns:fx="http://www.fixm.aero/flight/4.2" xmlns:fb="http://www.fixm.aero/base/4.2">
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
