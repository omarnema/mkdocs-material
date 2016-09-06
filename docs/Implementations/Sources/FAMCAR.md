Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-06-11
ModifyDate: 2016-06-11


#FAMCAR (Family Care)

**Client(s)**: [CCCN](../CCCN.md)  
**Density Area**: Northwest   

**Note:** FAMCAR is an internal Arcadia acronym and is not used by Coordinated Care.

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture


Family Care



| Overview ||
|-----|-----|
| Data Source Name| **Family Care** |
| Data Source Acronym| **FAMCAR** |
| Type | **Claims** |
| Site ID | **6** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |



<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|FAMCAR_PRESTAGING_PRD|
|User Name|FAMCAR_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*N/A*

##Custom Configurations




##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

No claim ammounts

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\????-FAMCAR_SFTP_PRD**.  



##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20FAMCAR%20or%20%22Data%20Source%20Acronym%22%20~%20FAMCAR)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)