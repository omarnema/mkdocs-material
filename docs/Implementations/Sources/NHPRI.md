Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-08-03
ModifyDate: 2016-08-03


#NHPRI (Neighborhood Health Plan of Rhode Island)

**Client(s)**: [BVCHC](../BVCHC.md)  
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
| Data Source Name| **Neighborhood Health Plan of Rhode Island** |
| Data Source Acronym| **NHPRI** |
| Type | **Claims** |
| Site ID | **1** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|NHPRI_PRESTAGING_PRD|
|User Name|NHPRI_PRD_PRESTAGING|  


###Location Hierarchy Configuration

TBD. 

##Custom Configurations

##Data Source  

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0426-PR-NHPRI_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A - Prestaging |
|Is the database production?| N/A - Prestaging  |
|Frequency of Extracts| Unknown. File delivery TBD. |

##Known Issues

Initial set of historical files are unencrypted/zipped. We will be working to get them encrypted on an ongoing basis. 

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20NHPRI%20or%20%22Data%20Source%20Acronym%22%20~%20NHPRI)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
* [SOW](https://arcadia.box.com/s/i1batfuya2lo1bd3b6pyvelubwnel29m)