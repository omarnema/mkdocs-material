Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-05-25


#BAYOU (Bayoumi Medical PLLC)

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
| Data Source Name| **Bayoumi Medical PLLC** |
| Data Source Acronym| **BAYOU** |
| Type | **Clinical** |
| Site ID | **46** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|STIAPPSERVER\STISQL|
|Port|1433|
|Name|PCare|
|User Name|abay15|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * Bayoumi Medical PLLC
            * Bayoumi Medical PLLC Main Office
            * BAYOUMI MEDICAL
            * AHMED BAYOUMI
            * Bayoumi Medical PLLC - Unknown Location

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [ChartMaker 5.6.0.436](../../Tech_Delivery/EHR-Documentation/ChartMaker.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM).  Additionally, daily maintenance is performed at 5AM, so any extracts that run into the maintenance window will likely fail. |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20BAYOU%20or%20%22Data%20Source%20Acronym%22%20~%20BAYOU)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/8c5he6966om0iy3qv2mpwiqe2rgjc5gm)
- [Connector Handoff](https://arcadia.box.com/s/2059fc6ztsx6kuxz9le1g1jggyecp73j)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)