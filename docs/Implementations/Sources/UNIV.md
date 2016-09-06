Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-03-21


#UNIV (University Health Services)

**Client(s)**: [AHP](../AHP.md), [XCLS](../XCLS.md)  
**Density Area**: New York   

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture

| Overview ||
|-----|-----|
| Data Source Name| **University Health Services** |
| Data Source Acronym| **UNIV** |
| Type | **Clinical** |
| Site ID | **44** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|ORACLE|
|Host|uhsdbprod1.its.rochester.edu|
|Port|1521|
|Name|P5PROD.rochester.edu|
|User Name|arcadia|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * University Health Service
            * University Health Service - Unknown Location
            * University Health Service Main Office
            * River Campus
            * UCC - RCO
            * Medical Center
            * Psychiatry - RCO
            * Eastman School
            * OH - Off Site
            * PT - RC
            * PT - Eastman
            * UCC - ESM
            * UCC - MCO
            * Psychiatry - MCO
            * Psychiatry - ESM

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [PyraMED 0](../../Tech_Delivery/EHR-Documentation/PyraMED.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM) |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

*Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20UNIV%20or%20%22Data%20Source%20Acronym%22%20~%20UNIV)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/21wxjwkqf8222b5ynkunmp6rj0gomelc)
- [Connector Handoff](https://arcadia.box.com/s/xvqz1j4l8lysvkox8r7uqajqpcc6rwu5)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)
