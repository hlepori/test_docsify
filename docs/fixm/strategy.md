# FIXM Strategy

## 1	Introduction

### 1.1	Introduction to FIXM

The Flight Information Exchange Model (FIXM) is an exchange model capturing Flight and Flow information that is globally standardised. The requirement for FIXM was identified by the International Civil Aviation Organisation (ICAO) [1][2][3][4][5] Air Traffic Management Requirements and Performance Panel (ATMRPP) and endorsed at the 12th Air Navigation Conference as part of the Aviation System Block Upgrades (ASBU) and as described in Flight and Flow Information for a Collaborative Environment (FF-ICE) [6].

FIXM is the equivalent, for the Flight domain, of AIXM (Aeronautical Information Exchange Model) and WXXM (Weather Information Exchange Model) both of which were developed in order to achieve global interoperability for, respectively, AIS and MET information exchange. FIXM is therefore part of a family of technology independent, harmonized and interoperable information exchange models designed to cover the information needs of Air Traffic Management.

According to the ICAO SWIM concept [11], FIXM is one of the models that belong to the “Information Exchange Models” layer of the ICAO SWIM Global Interoperability framework.

### 1.2	Purpose of the document
This document details the high-level requirements on the FIXM content, structure and scope to guide the overall FIXM evolution.

### 1.3	Revision process

This document is approved and published by the FIXM Change Control Board (CCB). Future evolutions of the document shall be managed via the FIXM change management [10].

## 2	FIXM Requirements

This chapter lists the strategic requirements for FIXM. These requirements are expressed at a high level; they are expressed in order to ensure FIXM is developed according to a plan that is aligned with the expectations of the ICAO Aviation System Block Upgrades (ASBU) [7] and key FIXM stakeholders.

?> Interpretation: The operative verb “shall” is used for formal requirements. The operative verb “should” is used for recommendations. Formal requirements are mandatory and must be satisfied by FIXM. Recommendations are not mandatory; however, compliance is strongly advised, and non-compliance must be justified.

### 2.1	FIXM Change Management

FIXM change management shall be established to manage the development of FIXM over time in order to:
- Ensure that FIXM is developed in a transparent manner.
- Ensure the standard strives to meet the needs of all FIXM stakeholders within the ATM community. 
- Focus communication regarding FIXM development within the ATM community and beyond.

The FIXM CCB shall provide this change management.

The FIXM charter [10] describes the principles of the FIXM change management, and the exact roles and responsibilities of the FIXM actors.

### 2.2	FIXM Components and Artefacts

The term `FIXM` refers collectively to:
-	`FIXM Core`, as described in chapter 2.2.1;
-	The `FIXM Applications` managed by the FIXM CCB as described in chapter 2.2.2;
-	The supporting FIXM artefacts managed by the FIXM CCB, as described in chapter 2.2.3;
-	The `FIXM Extensions` managed by the FIXM CCB, as described in chapter 2.2.4.

#### 2.2.1	FIXM Core

FIXM Core shall contain the pieces of flight information that are globally applicable and which are endorsed by the FIXM CCB. At minimum this shall include the scope of the FF-ICE provisions. Appendix A – Eligibility criteria for FIXM Core further details the criteria for unambiguously deciding whether given pieces of information qualify for FIXM Core.

FIXM Core shall be managed by the FIXM CCB.

FIXM Core shall be composed of the following components:
- The FIXM Core Logical Model shall capture in UML all the constructs that are required for flight information exchange at a global level. It shall detail the data entities, their attributes and containment relationships. The FIXM Core Logical Model shall define an extension mechanism that allows data entities, attributes and relationships to be provided in addition to the core model. The constructs defined in the FIXM Core Logical Model shall be derived from, and traced to, the ICAO requirements for FIXM.
- A FIXM Core Physical Model shall be a realisation of the FIXM Logical Model defining a physical representation of the logical model to be used for data exchanges between systems. A FIXM Core Physical Model shall represent constructs described in the FIXM Core Logical Model. The approved physical models are listed below.
  - The FIXM Core XML Schemas shall be a physical representation, expressed as a XML Schema Definition (XSD). Its use should primarily target ground-ground exchanges, as XML is not yet considered applicable for flight information exchanges between air (aircraft) and ground. The FIXM Core XML Schemas shall be programmatically derived from the FIXM Core Logical Model.

FIXM Core may include additional physical representations of the FIXM Core Logical Model (i.e. additional physical models), as appropriate. For instance, a physical representation of the FIXM Core Logical Model supporting air-ground exchanges may be developed in the future and included in FIXM. Such additional physical representations of the FIXM Core Logical Model would officially qualify for FIXM if endorsed by the FIXM change management (see chapter 2.1).

#### 2.2.2	FIXM Applications

A FIXM Application addresses how the flight data elements from FIXM Core are packaged and used in terms of information service payload within a specific context of application.

A FIXM Application should be composed of the following components:
-	A logical representation capturing in UML all the relevant message data items exchanged in the context of application, and (at least) one physical realisation derived from the logical representation.
-	A set of message templates defining the restricted message and flight data subsets that are relevant for the given message transactions.

A FIXM Application can evolve independently from FIXM Core and should be extensible.

The FIXM Applications managed by the FIXM CCB shall cover at least the use of FIXM Core in the context of FF-ICE.

#### 2.2.3	FIXM Supporting artefacts

The supporting FIXM artefacts should include, at least:
- The FIXM Primer: this document shall serve as a high-level introduction to FIXM, targeting the widest possible audience. It shall include references to the main FIXM components, to the FIXM artefacts listed below, and to this FIXM Strategy document.
- Requirements Traceability Reports for FIXM Core and the FIXM Application for FF-ICE: these reports shall provide evidence that the content of FIXM Core and of the FIXM Application for FF-ICE satisfy, and are duly traceable to, the applicable ICAO requirements for FF-ICE.
- Release Notes: these notes shall list the FIXM CCB-approved changes integrated into the different versions of the FIXM components.
- The FIXM User Manual: this document shall provide guidance and clarifications for the implementation of FIXM. It shall cover rules and guidance for the good use of FIXM in all contexts, rules and guidance for the good use of FIXM in the specific context of FF-ICE, including the translation of FF-ICE Messages into ATS messages, illustrative data samples, and guidance for the development FIXM Applications and Extensions by third parties. The FIXM User Manual should be made available as an online documentation.
- Online FIXM model and schema documentation: this is an online HTML description of the content of the FIXM components. This documentation shall be derived programmatically from the logical and physical representations of the FIXM components.
- FIXM Supporting Tools: these are automation tools developed and used to support the development of the XML Schemas for FIXM Applications and FIXM Extensions.
For practical reasons, the evolution of FIXM will necessitate the update and recognition of these artefacts in a managed fashion by the use of recognised releases.

#### 2.2.4	FIXM Extensions 

FIXM, like AIXM and WXXM [9], shall support an extension mechanism, and should comply with the core and regional extension concept of ICAO Document 9965. Supporting extensions is paramount in order to:
- Enable Communities of Interest to capture application-specific requirements, without undermining global interoperability of flight information exchanges;
- Support the interface between implementers of different versions of FIXM;
- Facilitate the Change Management Process of FIXM.

FIXM Extensions shall supplement FIXM Core or FIXM Applications managed by the FIXM CCB in order to support additional (e.g. regional) requirements from particular communities of interest or organisations. An extension shall add elements beyond the provisions for FIXM Core or the FIXM Applications managed by the FIXM CCB, but shall never supersede them.

FIXM Extensions may serve as an operational “incubator” prior to being “promoted” to FIXM Core.

### 2.3	Catalogue of FIXM Applications and FIXM Extensions

FIXM Core and FIXM Applications are extensible by design. Therefore, extensions may be developed over time by third parties in order to satisfy domestic or regional needs. Likewise, new FIXM Applications may be developed by third parties in order to address the use of FIXM Core - and possibly their extensions to FIXM Core - within their own application contexts.

These developments are good from a FIXM adoption perspective. However, they may lead to a proliferation of FIXM Applications and FIXM Extensions having possibly overlapping content or being incompatible . This situation may undermine the global interoperability objectives for the Flight domain and may increase the cost of implementations for FIXM stakeholders being exposed to, and having to reconcile, a myriad of FIXM Extensions and FIXM Applications.

The FIXM CCB should support the identification of these issues and contribute to their resolution by building and maintaining a catalogue of FIXM Applications and FIXM Extensions developed by third parties, and by liaising with the appropriate stakeholders when potential synergies and collaboration opportunities are identified. 
Appendix B – Third-parties FIXM Applications and Extensions provides additional considerations about this catalogue.

### 2.4	FIXM, one of many ATM standards

Many initiatives have been historically conducted by various ATM communities of interest in order to specify standards supporting the exchange of domain-specific information. ATM modernisation programmes are now moving towards integrated ATM information where these existing standards, developed to meet domain-specific requirements, have to be brought together and aligned to a certain extent.

FIXM, in this context, is one ATM standard, among many others, that will enable the exchange of elements of ATM information, restricted to the Flight domain. Its development shall therefore be aligned with other relevant ATM initiatives.

This chapter lists a number of strategic requirements for FIXM with regards to the alignment and connection with other ATM standard developments.

#### 2.4.1	AIXM, WXXM and FIXM

The AIXM (Aeronautical Information Exchange Model) is designed to enable the management and distribution of AIS (Aeronautical Information Services) data in digital format. More information about this data exchange model can be found in the website www.AIXM.aero.
The WXXM (Weather Information Exchange Model) is designed to enable a platform independent, harmonized and interoperable meteorological information exchange covering all the needs of the air transport industry. More information about this data exchange model can be found in the website www.WXXM.aero.

FIXM (Flight Information Exchange Model) is designed to enable the interoperability of flight and flow information at a global level.

FIXM may overlap in scope with the AIM and MET domains. FIXM shall therefore be able to reference AIXM and WXXM when deemed relevant, and shall not redefine their content items.

FIXM shall rely, as much as possible, on the same foundations as AIXM and WXXM, in order to allow greater interoperability between different ATM data domains. These common foundations may include:
- Standards from the ISO 19100 series;
- OGC standards and best practices.

#### 2.4.2	FIXM and AIDX

The International Air Transport Association (IATA) (http://www.iata.org) has established the Passenger and Airport Data Interchange Standards (PADIS) Board to develop Electronic Data Interchange message standards and also XML message standards for passenger travel and airport-related passenger service activities. One component of this project is AIDX, the Aviation Information Data Exchange, which is being used by ACI Airport Community Recommended Information Services (ACRIS) for Airport Collaborative Decision Making (A-CDM). 

FIXM may capture pieces of flight information also captured in AIDX; therefore, FIXM shall be at least semantically consistent with AIDX, in case of an overlap of information.  

#### 2.4.3	FIXM and the AIRM

ICAO endorsed during the 12th Air Navigation Conference the creation of an ATM Information Reference Model (AIRM) [12] acting as an overarching reference for the ATM domains: Flight, AIM, MET, Surveillance, etc.

As of May 2021, based on the work of the ICAO Information Management Panel (IMP), semantic interoperability of the information service payload is expected to be achieved by aligning the meaning of the information exchanged with the AIRM. The EUROCONTROL Specification on SWIM Information Definition [13] also requires the preservation of meaning of the AIRM concepts when describing exchanged ATM information (requirement SWIM-INFO-009).

It is recognised as a strategic objective for FIXM to establish the appropriate coordination and to gradually achieve semantic alignment with the AIRM. More generally, it is recognised as a strategic objective for FIXM to monitor the work and conclusions of the ICAO Information Management Panel (IMP) with regards to Information Management and SWIM and to align FIXM with any relevant recommendations from this panel, as appropriate.

### 2.5	FIXM Scope and Schedule

It is the role of the FIXM CCB to produce the FIXM Release Plan which:
- Provides the scope / content of FIXM;
- Details the FIXM implementation/evolution timelines;
- Balances expectations of system implementations.

The main intention is to achieve information exchange interoperability between stakeholders for all phases of flights and types of operations, but it does not preclude any beneficial usage within the stakeholders’ environment. The expectations are that ICAO would look to focus on the global expectations whilst allowing more advanced regional developments. 

The FF-ICE concept and the applicable ICAO provisions drive the common and international development of FIXM, and impose requirements on what FIXM will deliver. FIXM shall cover the ICAO requirements on FF-ICE information. The scope of FIXM can however go beyond the strict provisions for FF-ICE if approved by the FIXM change management.

The scope of an individual release of FIXM is decided by the FIXM CCB prior to the development, under the supervision of ICAO ATMRPP. The availability of operational inputs will drive the development of a given FIXM version. The FIXM CCB will provide the de facto focal point for collecting such operational drivers, unless other working arrangements are approved by the FIXM CCB and duly described in the FIXM CCB charter.

## 3	FIXM Relationship to Services and Messages

### 3.1	Use of FIXM by Services

FIXM, through the FIXM Applications, address how the flight data elements from FIXM Core can be packaged and used in terms of information service payload. Other service considerations are, strictly speaking, not within the formal scope of FIXM. 

However, the supporting FIXM artefacts, and in particular the FIXM User Manual, may capture additional service-related considerations in order to help service implementers use FIXM in the context of their services. This technical guidance, if provided, should be released as informative guidance and shall not be prescriptive.

### 3.2	FIXM Relationship to ATS Messages
The FF-ICE/R1 Implementation Guidance Manual [14] chapter 3.6 explains that for a significant period of time it will be necessary to operate within a “mixed mode” environment, i.e., one in which both current ATS messages and their associated procedures will apply in addition to FF-ICE messages and associated procedures, and requires that FF-ICE messages can be mapped or translated to their ATS messages counterparts.

Therefore, FIXM shall ensure it retains and releases content that remains compatible with the ATS Messages and that enables the FF-ICE Messages to ATS Messages translation required by the FF-ICE Concept. The FIXM User Manual should provide guidance for realising this translation.

However, whilst needing to retain compatibility with the ATS Message content, FIXM shall ensure it is not constrained to just meeting such message-based needs and is thus also able to provide the additional and enhanced content needs for the evolving ATM needs, in line with ICAO requirements.

