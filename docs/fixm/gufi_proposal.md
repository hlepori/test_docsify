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
|Proper generation of a UUID v4 cannot be strictly enforced.| - Guidance is available about which off-the-shelf IT libraries should be used for proper UUID 4 generation. <br> - Make the number space of UUID larger, by adding more variable information from the eFPL.  |
|||

The generation of the UUID v4 may be implemented by an FF-ICE participant in its systems but may also be performed by a third-party service provided an organisation not necessarily involved in FF-ICE Operations. By design, the UUID v4 solution guarantees that flights will be uniquelly identified without significant central coordination. In other terms, the solution is agnostic to the way the business is organised.

### GUFI allocation


|Associated risks|Mitigation|
|:-|:-|
| | |

Appendix F - Association checks 

### GUFI traceability



## Resulting GUFI requirements

### GUFI format

> The GUFI shall be an unaltered UUID v4.

JUSTIFICATION: The ISO UUID v4, without any modification, is a well-established and trusted standard for unique identifier creation.

### GUFI quality

>



JUSTIFICATION

>  

## 

# FF-ICE/R1 IG

## 3.7	GUFI & FLIGHT PLAN ASSOCIATION
### 3.7.1	General
3.7.1.1	The Global Unique Flight Identifier (GUFI) is intended to provide a unique reference to a specific flight, civil or military. Its purpose is to assist in associating a message to the correct flight and to help in distinguishing between similar flights. There can be multiple flight plans with the same aircraft identification and departure point and it is not always readily apparent when two flight plans are different versions for the same flight, or different intended flights. The GUFI will resolve such situations.
3.7.1.2	Most ATM systems today rely upon a comparison of various “key fields”, such as Aircraft Identification, Aerodrome of Departure, EOBT, etc., to identify a flight and to distinguish one flight from another. This method can however give an unreliable result particularly if, for example, a flight is delayed and/or the aircraft identification is the registration and therefore the same for each flight.
3.7.1.3	The introduction of FF-ICE together with SWIM-type functionality facilitates a working environment in which many transactions would be performed in an automated manner. Such an environment, with potentially many transactions per flight, requires a quick and reliable identification of the flight concerned and cannot depend on an unreliable mechanism with frequent manual interventions to assist in determining the correct target flight.
3.7.1.4	An important principle behind the introduction of a globally unique identifier (PANS-ATM 17.4.1) is that it should identify only one flight plan and each flight plan should be identified by a single identifier.
If a flight plan is cancelled, for whatever reason, and a new flight plan is submitted, the new flight plan shall contain a new GUFI even if the new flight plan relates to what the operator will consider to be the same flight. Alternatively, in place of the cancel and re-file option, the new flight plan can be provided with the same GUFI but with an incremented flight plan version and as a consequence it will be treated as a complete replacement of the existing data. See 3.7.4.3 and 6.4.3.7.
3.7.1.5	As the GUFI identifies an individual flight it is therefore understood that the operator will only assign a GUFI to a flight when it is prepared to engage in communications concerning a specific flight. A GUFI will therefore not be allocated to schedule information which is repetitive by nature and therefore relates to multiple flights.
3.7.1.6	In addition to identifying the correct flight to which a message or transaction should be associated, the GUFI will also assist in distinguishing between different flight plans e.g., answering the question “do these two flight plans concern one flight or two different flights?”
3.7.1.7	Although the GUFI should help to provide a clear indication of the target flight and of the operator’s intent with regard to the operation of one or more flights, in the early days of implementation, before GUFI allocation and handling by all parties can be completely verified in operations, it would be more reliable to continue to use additional information to verify flight association. Furthermore it needs to be considered that in a mixed mode environment, some flight plans will not include a GUFI.
3.7.1.8	An incorrect GUFI indication can result in data being applied to the wrong flight plan and must be avoided. While this is a significant error the introduction of the GUFI as an additional keyfield means the frequency with which it happens should be reduced in comparison to current practices. It is interesting to note that an update which contains a significant change (e.g., aircraft type changed to a C172, wrongly applied to a long haul commercial flight) will quickly fail further processing while a less significant change may go undetected.
It is therefore recommended that, at least during initial implementation of FF-ICE and/or initial implementation by a new eFPL provider, some data validation that includes the GUFI is performed, particularly upon reception of a flight plan.
### 3.7.2	 Determination of “A Flight”
3.7.2.1	For the purpose of GUFI allocation “a flight” is considered to be the operation of an aircraft with a specified aircraft identification, at a specified departure aerodrome, at a specified date and time, from first submission of the flight plan (Preliminary or Filed) until in-blocks at an arrival aerodrome.

It is worth noting that each leg of a multi-leg operation is therefore defined as a different flight (it will depart from a different specified aerodrome), from an ATM perspective, and shall be allocated a different GUFI.
3.7.2.2	A flight is considered to have taken place once the aircraft has completed its planned operation at its destination aerodrome or, it has landed at a diversion aerodrome. Therefore, following a diversion a subsequent attempt to reach the destination aerodrome will require a new flight plan and a new GUFI. Likewise, a flight which needs to return and land (a diversion from its planned operation) at its departure aerodrome immediately after becoming airborne will require a new flight plan and a new GUFI if it wishes to re-attempt the flight.
3.7.2.3	An aircraft that is obliged to return to its parking stand prior to becoming airborne; i.e. a “ground return” or an aborted take-off, may retain the flight plan and its GUFI if it is intended to continue the flight. This is based on the concept that ATC systems can perform a “roll-back” of the flight prior to it becoming airborne. If there is no intention to continue the flight, the flight plan should be cancelled.
### 3.7.3	Flight Plan Association
3.7.3.1	The process of determining whether or not two flight plans actually refer to just one flight, or the difficulties sometimes encountered in determining the correct flight to which an update should be applied, is not new. ATM systems have been dealing with these problems for many years, sometimes having to resort to manual intervention.
3.7.3.2	The introduction of FF-ICE, GUFI and more data sharing processes will provide an opportunity to perform better association of received information with a specific flight, and to detect inconsistencies (e.g., two flight plans for the same flight). To avoid differences in acceptance of a flight plan between different eASPs, it is strongly recommended that a flight plan that will be relevant to multiple ASPs be subject to the flight plan association checks in APPENDIX F – Association Checks. A flight plan for a flight that remains within the scope of a single ASP can be validated against local rules.
3.7.3.3	In determining whether or not two flight plans refer to the same flight, it is common practice to use the aircraft identification, the departure aerodrome and the off-block date and time. Use of the destination aerodrome is not recommended on the basis that two flights departing the same aerodrome at the same time using the same identification should probably not be accepted even if they have different destinations. 
3.7.3.4	Most of the issues encountered today concern timing aspects; i.e. how far apart the EOBTs have to be before two flight plans with the same aircraft identification and aerodrome of departure can be accepted as two distinct flights. Different ASPs will have implemented different solutions with differing complexity based on factors such as the total estimated elapsed time of each flight, whether or not the two flights would exist in the same airspace at the same time, etc. The most significant ASP in making this determination is the ASP responsible for the departure aerodrome. It is therefore suggested that eASPs which are not responsible for the departure area  i.e., downstream eASPs, could place greater reliance on the GUFIs.
3.7.3.5	Assessment of the timing aspects for flight plan association should not be rigidly applied in the processing of modifications to the EOBT. An operator who has planned to fly a series of flights should not be obliged to delay each flight in reverse chronological order to achieve a delay to the first flight.
### 3.7.4	GUFI Procedure
3.7.4.1	The operator, or its designated representative, is required to generate and allocate a GUFI to its FF-ICE flight plan. It is important that only one GUFI is allocated to a flight and this can only be assured by ensuring that the GUFI is allocated at source by the operator, or its representative, upon creation of the flight plan.
3.7.4.2	The operator should ensure that all flight data submitted for a flight is submitted using the same GUFI. This applies to both the Preliminary and Filed versions of the flight plan. It also applies to a Trial Request when a Preliminary or Filed Flight Plan already exists for the flight. This will enable the ATM system to ensure that, in assessing the impact of a Trial Request, it doesn’t include the same flight twice.
3.7.4.3	An eASP on reception of a Preliminary or Filed Flight Plan (a new flight plan creation) should use the logic in APPENDIX F – Association Checks to verify that:
•	the same Preliminary Flight Plan or the same Filed Flight Plan does not already exist with a different GUFI. It is of course normal that, upon Filing, a Preliminary Flight Plan may already exist for the same flight with the same GUFI;
•	the same GUFI does not already exist, at least within the operational database, for a different flight plan. 
If the same Preliminary Flight Plan or the same Filed Flight Plan does exist with the same GUFI and the new submission has a later version number, it should be treated by the eASP as a complete replacement of the existing data. See also 6.4.3.7.
3.7.4.4	On reception of an update or cancellation message, an eASP will use the GUFI as an index to obtain the target flight plan. It is nevertheless recommended that, having obtained the flight data using the GUFI, the eASP performs a verification of the GUFI by ensuring that the other key fields used for message association are consistent. However, in circumstances in which the operator and service provider systems have successfully achieved some form of integrity testing the eASP might choose to rely purely upon the GUFI without further verification.
3.7.4.5	In the case of a missing flight plan an eASP would be expected to obtain the flight plan, and the GUFI, through the use of the Flight Data Request service as described in section 8. 
3.7.4.6	In translating an eFPL into a FPL for transmission to non-enabled ASPs the GUFI will not be provided.
### 3.7.5	GUFI Format
3.7.5.1	A GUFI shall be provided as a version 4 “Universally Unique Identifier" (UUID), as standardised by IETF RFC 4122 of the Open Software Foundation (OSF) and documented by the International Standards Office (ISO/IEC 9834-8:2005) and the International Telecommunications Union. 
3.7.5.2	According to RFC 4122, a UUID is 128 bits of information, usually described as 16 octets, each of which can be represented by 2 hexadecimal digits (thus, a total of 32 hexadecimal digits). As a total of 6 bits are set to pre-defined values, up to 122 bits are available for the GUFI information, which provides a high likelihood for uniqueness over an extremely large number of flights. 
3.7.5.3	A detailed description of the character encoding for a GUFI is provided in Appendix G-1. 
3.7.5.4	The most important feature of the GUFI lies in its uniqueness. The uniqueness of an UUID, in turn, relies upon its method of generation. RFC 4122 identifies several methods of generation, including time-based, namebased, random number-based and others. Each method can have potential duplication issues when different nodes are each creating UUIDs. RFC 4122 also addresses mitigations that are possible to avoid duplication, i.e. in section 4.5 it states: “In addition, items such as the computer's name and the name of the operating system, while not strictly speaking random, will help differentiate the results from those obtained by other systems.”
### 3.7.6	GUFI Content Overview
3.7.6.1	For FF-ICE, the UUID will have two parts: 
1.	A namespace identifier as described in Appendix G-2. This namespace identifier will ensure that no GUFI generated by a flight plan originator can duplicate that of any other originator.
2.	The remaining bits will be a number chosen by the originator to be unique with respect to other flight plans generated by that originator over a period of interest.
### 3.7.7	GUFI Namespace Identifier
3.7.7.1	Described in detail in APPENDIX G – GUFI Construction, the namespace identifier is constructed from readily available information such as ICAO Doc. 8585, ICAO Doc. 7910, and/or the relevant state aircraft registry.
### 3.7.8	GUFI Flight-Specific Identifier
3.7.8.1	The second part of the GUFI is a flight-specific identification generated by the flight plan originator. The scheme to be used is up to the originator. Each scheme has implications as to the processing required to ensure uniqueness.
3.7.8.2	The requirement to achieve uniqueness of the flight ID covers a period of at least 10 years. The namespace identifier means that the only possible duplication would be between two flights from the same originator (i.e. with the same namespace identifier), so the scope of the problem is completely within the control of each flight plan originator.
3.7.8.3	Possible methods of generation for the flight-specific identifier and their implications:
1.	Random (or pseudo-random) number. A large random number, if truly random, will have a small probability of repeating within the time frame of interest, nominally a couple of days. If a pseudorandom number generator is selected for use, it should be chosen carefully to ensure appropriate characteristics (i.e. low probability of regeneration of a number used recently). A standard such as ISO/IEC 18031:2011 should be followed.
a)	Since there is a possibility of duplication, even if small, the flight plan originator should consider checking against other still operational and recently completed (or cancelled) flights to ensure a duplicate number was not generated.
b)	After a system restart (normal or after failure), if pseudo-random number generation was used then a good seed management procedure should be used to avoid re-generating part of the same sequence previously generated.
2.	Sequential number. Assigning the numbers sequentially will provide the maximum period before a number repeats, and there is no chance of a duplication until all possible numbers have been used.
a)	This also requires that after a system restart (normal or after failure), care is taken to establish a starting point that does not result in reuse of previously assigned numbers. This can be done by check-pointing the last assigned number.
b)	Alternatively, a date-based scheme could be used, i.e. always start at a “check point” calculated from the date. The checkpoints would have to be farther apart than the maximum number of GUFIs needed since the last checkpoint day. For example, 10 years is 315,360,000 seconds. If we assign a block of 70-bit numbers to each second over the 10-year period, then we have over 3x1012 GUFIs available in each one-second bucket. Whenever the system starts, it can begin at the bucket of numbers assigned to the current time.
3.	Date, Time, Flight Information. In the 70 bits available one could attempt to fill in the UUID using characteristics of the flight, including when filed.
a)	Depending on the resolution desired, it could be challenging to describe the flight adequately to ensure uniqueness. For example, including aircraft ID, departure, and destination alone (which would not be adequate) requires (7+4+4) = 15 characters. Using the 6 bits per character scheme described in Appendix G, that is 90 bits—more than is available. One might need to compress the information to make such a scheme work.
b)	Using time of filing could work, as long as there is a method to ensure two flights cannot be assigned the same filing time by the system. In 70 bits, a 10-year period of time can be split into sub-microsecond increments.
### 3.7.9	Validation of a GUFI Generator
3.7.9.1	Testing can validate the proper generation of the namespace portion of the GUFI. It will be static for a given station, and can be readily examined for correctness.
3.7.9.2	Validation of the flight-specific portion of the GUFI will depend somewhat on the method chosen. For a random number generator, the primary validation should be to verify use of a suitable generation method per appropriate standards. Testing can be appropriate to verify checks for duplication with a recently assigned number, and for behaviour after a restart.
3.7.9.3	Other methods (sequential number; date/time/flight information) can use testing since the results of each GUFI should be deterministic.
### 3.7.10	Validation of the assigned GUFI
3.7.10.1	In addition to mitigating any small residual risk of GUFI duplication at generation there is also a risk associated with miss-managing the assignment of a generated GUFI to a flight plan. It is absolutely critical that two flights in the operational ATM system not have the same GUFI. Operators are therefore encouraged to consider additional safeguards that ensure an assigned GUFI has not already been assigned to another flight within a period of at least 48 hours, including one that may have been subsequently cancelled.
 

