Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-05-25


#QURESHI (Dr. Qureshi)

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
| Data Source Name| **Dr. Qureshi** |
| Data Source Acronym| **QURESHI** |
| Type | **Clinical** |
| Site ID | **48** |
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
|User Name|soha15|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
        * Dr. Qureshi
            * Dr. Qureshi Main Office
            * Sohail A. Qureshi, M.D.
            * Dr. Qureshi - Unknown Location

##Custom Configurations

N/A

##Data Source

The data for this connector is pulled from [ChartMaker 5.6.0.420](../../Tech_Delivery/EHR-Documentation/ChartMaker.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM).  Additionally, daily maintenance is performed at 5AM, so any extracts that run into the maintenance window will likely fail.  |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily  |

##Known Issues

This practice hard deletes patients instead of leveraging a delete indicator field.

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20QURESHI%20or%20%22Data%20Source%20Acronym%22%20~%20QURESHI)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/6b8bhyra2vwdhffom2ogoa883vis0b3u)
- [Connector Handoff](https://arcadia.box.com/s/2l7pzsxw5jrekdj0p6e5ycpcqv8z01t6)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)