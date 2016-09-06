Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-03-30


#NORALLE (Northern Allegany Medical Group)

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
| Data Source Name| **Northern Allegany Medical Group** |
| Data Source Acronym| **NORALLE** |
| Type | **Clinical** |
| Site ID | **50** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|Toad for SQL Server|
|Host|NAMG2014\AMAZINGCHARTS|
|Port|61067|
|Name|AmazingCharts|
|User Name|arcadia2|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * Northern Allegany Medical Group
            * Northern Allegany Medical Group - Unknown Location
            * Northern Allegany Medical Group Main Office


##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [Amazing Charts 8.2.2](../../Tech_Delivery/EHR-Documentation/Amazing-Charts.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM) |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20NORALLE%20or%20%22Data%20Source%20Acronym%22%20~%20NORALLE)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/sgi0vvd91w6gwn9dn0d93sjn1b5eibkb)
- [Connector Handoff](https://arcadia.box.com/s/j1xug3l1lvzcwriy91ua3o0vitavh720)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)