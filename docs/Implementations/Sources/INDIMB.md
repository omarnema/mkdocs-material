Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-06-20


#INDIMB (Independent IMB)

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
| Data Source Name| **Independent IMB** |
| Data Source Acronym| **INDIMB** |
| Type | **Clinical** |
| Site ID | **39** |
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
|User Name|arcadia15|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * Internal Medicine of Brighton
            * Internal Medicine of Brighton - Unknown Location
            * Internal Medicine of Brighton Main Office
            * GEORGE PLAIN MD
            * BERNEDETTE MINNELLA MD
            * CATHERINE TAN MD
            * JULIE YOON MD
            * DIEGO CAHN-HIDALGO MD

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [ChartMaker 5.6.0.420](../../Tech_Delivery/EHR-Documentation/ChartMaker.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM).  Additionally, daily maintenance is performed at 5AM, so any extracts that run into the maintenance window will likely fail. |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

*Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20INDIMB%20or%20%22Data%20Source%20Acronym%22%20~%20INDIMB)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/w3sy98phzds1yydz1d30ezorvr7lhg07)
- [Connector Handoff](https://arcadia.box.com/s/z2tvrdlq1pvcd7gqiy9shyjfj8uxau88)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)
- [DQA](https://arcadia.box.com/s/mggkum9w450xikcge88slln3c9hzyupj)