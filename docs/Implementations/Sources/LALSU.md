Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-17


#LHCQF LSU Eligibility (LHCQF LSU Eligibility)

**Client(s)**: [LHCQF](../LHCQF.md)  
**Density Area**: Southeast   

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture

This is a 3rd party eligibility that will interact with the data genreated from EDRegistry feed. It will leverage the connectors used from [LHCQF Molina Medicaid Eligibility - (LAMOELG)](../Implementations/~Sources/LAMOELG/index.html).

| Overview ||
|-----|-----|
| Data Source Name| **LHCQF LSU Eligibility** |
| Data Source Acronym| **LALSU** |
| Type | **** |
| Site ID | **136** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|LHCQFSQLPRD02|
|Port|1433|
|Name|LALSU_PRESTAGING_PRD|
|User Name|LALSU_PRD_PRESTAGING|  


###Location Hierarchy Configuration

N/A - Claims

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0656-PR-LALSU_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|EDRegistrySubscriber||
|-----|-----|
| Table Name | EDRegistrySubscriber|
| File Name Patterne | .|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: OriginalID(13),ProviderID(7),PlanName(11),EligibilityBeginDate(8),EligibilityEndDate(8),CancelReason(3),MedicarePartAIndicator(1),MedicarePartBIndicator(1),FirstName(20),MiddleInitial(1),LastName(25),Gender(1),HomePhoneNumber(10),BirthDate(8),DeathDate(8),SocialSecurityNumber(9),Race(1),AddressType(1),AddressLine1(25),AddressLine2(25),City(25),State(2),ZipCode(9),ParishCode(2),CurrentID(13),CardNumber(16),EnrollmentType(1),AidCategoryCode(2),TypeCaseCode(3),MedicaidEligibilityFlag(1),BayouHealthPlanEligibilityFlag(1),BayouHealthBeginDate(8),BayouHealthEndDate(8)  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None (prestaging)|
|Is the database production?| N/A (prestaging)  |
|Frequency of Extracts| Nightly. |

##Known Issues

*Not documented at this time.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20LAMOELG%20or%20%22Data%20Source%20Acronym%22%20~%20LAMOELG)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
