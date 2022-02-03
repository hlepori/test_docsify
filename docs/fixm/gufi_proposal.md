# Proposal for the GUFI

## Needs 

The introduction of the GUFI as a universally unique flight identifier comes with two questions:
-	The GUFI generation question: how to ensure that the GUFI is generated in a way that guarantees that it is universally unique, i.e. unique within the universe of the FF-ICE domain? 
  -	A corollary of this question is: how to manage/mitigate the case whereby two distinct participants would generate the same GUFI?
-	The GUFI allocation question: how to ensure that a given real world flight is allocated only one GUFI? 
  -	A corollary of this question is: how to manage/mitigate multiple GUFIs allocations to the same flight across different domain participants?

### GUFI generation

The ISO UUID v4, without any modification, is a well-established and trusted standard for unique identifier creation. Therefore, the GUFI shall be an unaltered UUID v4.

|Associated risks|Mitigation|
|:-|:-|
|Proper generation of a UUID v4 cannot be strictly enforced.| Guidance is available on the FIXM User Manual about which off-the-shelf IT libraries should be used for proper UUID 4 generation.|
|||

### GUFI allocation
Chapter xxx of the FF-ICE Manual indicates 

Appendix F - Association checks 


## Resulting GUFI requirements

### GUFI format

> The GUFI shall be an unaltered UUID v4.

JUSTIFICATION: The ISO UUID v4, without any modification, is a well-established and trusted standard for unique identifier creation.

### GUFI quality

>



JUSTIFICATION

>  

## 
