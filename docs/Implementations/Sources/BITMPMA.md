Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-07-25
ModifyDate: 2016-07-25


#BITMPMA (Medicare Advantage from TMP)

**Client(s)**: [BIDCOUI](../BIDCOUI.md)  
**Density Area**: Northeast   

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
| Data Source Name| **Medicare Advantage from TMP** |
| Data Source Acronym| **BITMPMA** |
| Type | **Claims** |
| Site ID | **85** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|BITUFTS_PRESTAGING_PRD|
|User Name|BITUFTS_PRD_PRESTAGING|  


###Location Hierarchy Configuration

Nothing custom required here. 

##Custom Configurations

There are some customizations and additional information about the file feed that are documented under [BITUFTS](./BITUFTS.md). These two connectors come from a single feed of flat files but are treated separately because the file specs are different for Medicare Preferred vs Commercial and because they represent different claims from different business entities within Tufts. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0609-PR-BITMPMA_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| No, prestaging. |
|Is the database production?| No, prestaging.  |
|Frequency of Extracts| TBD.  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20BITMPMA%20or%20%22Data%20Source%20Acronym%22%20~%20BITMPMA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)