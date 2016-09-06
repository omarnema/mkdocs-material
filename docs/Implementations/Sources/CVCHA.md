Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#CVCHA (Columbia Valley CHC)

**Client(s)**: [CCCN](../CCCN.md)  
**Density Area**: Northwest   

*This is the second CCCN connector to CVCH. The first connector used Nextgen before it was depreciated and CVCH converted to Athena. The Nextgen source is listed as* **CVCH**, *this page is about the new Athena,* **CHVCHA**.

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
| Data Source Name| **Columbia Valley CHC** |
| Data Source Acronym| **CVCHA** |
| Type | **Clinical** |
| Site ID | **7** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|CVCHDW01|
|Port|1433|
|Name|ATHENA|
|User Name|arcadia|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations


##Data Source

The data for this connector is pulled from [Athena 0](../../Tech_Delivery/EHR-Documentation/Athena.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| **After 5PM PST (preferable between 6-8 PST)** |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues


Issues with linking Problems and diagnosis. Currently no problems have valid diagnosis codes (ICD9/10). 

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.app.box.com/files/0/f/1888547619/4._Client_Specific_Material)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20CVCHA%20or%20%22Data%20Source%20Acronym%22%20~%20CVCHA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)