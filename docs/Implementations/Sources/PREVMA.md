Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-02-10
ModifyDate: 2016-05-17


#PREVMA (Preventive Medicine Associates)

**Client(s)**: [XCLS](../XCLS.md)  
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
| Data Source Name| **Preventive Medicine Associates** |
| Data Source Acronym| **PREVMA** |
| Type | **** |
| Site ID | **70** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MySQL|
|Host|192.168.10.17|
|Port|4928|
|Name|mobiledoc|
|User Name|ecwtest|  


###Location Hierarchy Configuration

* Crouse IPA
    * Preventive Medicine Associates
      * Preventive Medicine Associates Unknown Location
      * Preventive Medicine Associates PLLC
      * VAN DUYN CENTER
      * BELLEVUE MANOR
      * NY HEART CENTER
      * CAMILLUS RIDGE
      * CGH ACUTE CARE
      * COMMUNITY HOSPITAL
      * DR LAVANYA GALI

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [eCW 10](../../Tech_Delivery/EHR-Documentation/eCW.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Yes, given that this is a production environment we should access outside of business hours (6 PM - 6 AM) |
|Is the database production?| Yes  |
|Frequency of Extracts| Daily |

##Known Issues

Not necessarily an issue, but it's worth noting that there is a backup taken at PREVMA at 6:45 PM that typically runs for about 7 minutes and another backup taken at 7 PM that typically runs for 3 hours.

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20PREVMA%20or%20%22Data%20Source%20Acronym%22%20~%20PREVMA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/cochbl1htgp22bcc3j7tggb56xwidfe4)
- [Connector Handoff](https://arcadia.app.box.com/files/0/f/2592284091/1/f_58550780073)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)
- [DQA](https://arcadia.box.com/s/zq2wtllh2edwzln3033crywjciydkcex)