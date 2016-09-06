Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-03-21


#NOYES (Noyes Employed)

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
| Data Source Name| **Noyes Employed** |
| Data Source Acronym| **NOYES** |
| Type | **Clinical** |
| Site ID | **53** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MySQL|
|Host|nmh-ecwdb10|
|Port|4928|
|Name|mobiledoc|
|User Name|SA|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * Creekside Family Medicine
            * Creekside Family Medicine - Unknown Location
            * Creekside Family Medicine Main Office

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [eCW 10](../../Tech_Delivery/EHR-Documentation/eCW.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM) |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20NOYES%20or%20%22Data%20Source%20Acronym%22%20~%20NOYES)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/wjr3924ibfjjjd811craw62pk2wtl76a)
- [Connector Handoff](https://arcadia.box.com/s/qpvjshp92ql476wnv17mba0m1qw2zduo)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)