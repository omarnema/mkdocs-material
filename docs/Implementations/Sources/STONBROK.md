Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-04-27
ModifyDate: 2016-05-17


#STONBROK (Stony Brook Peds)

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
| Data Source Name| **Stony Brook Peds** |
| Data Source Acronym| **STONBROK* |
| Type | **Clinical** |
| Site ID | **60** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MySQL|
|Host|10.210.1.14|
|Port|4928|
|Name|mobiledoc|
|User Name|SBPPC|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [eCW](../../Tech_Delivery/EHR-Documentation/eCW.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Light queries can be run during the day, but given that this is a production environment we should save any heavy lifting until outside of business hours (6 PM - 6 AM) |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20ARNOT%20or%20%22Data%20Source%20Acronym%22%20~%20ARNOT)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)