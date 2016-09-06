Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-05-25


#ABBA (Abbasey Medical PLLC)

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
| Data Source Name| **Abbasey Medical PLLC** |
| Data Source Acronym| **ABBA** |
| Type | **Clinical** |
| Site ID | **45** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|STIAPPSERVER\STISQL|
|Port|1433|
|Name|pcare|
|User Name|abbasey15|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * Abbasey Medical PLLC
            * Abbasey Medical PLLC - Unknown Location
            * Abbasey Medical PLLC Main Office
            * Abbasey Medical, PLLC

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
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20ABBA%20or%20%22Data%20Source%20Acronym%22%20~%20ABBA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/eku91ddx7scdp59absmu17lp4v2lp4y8)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)
- [DQA](https://arcadia.box.com/s/cuab6839jld3tynmja2dfyt36jd0udut)