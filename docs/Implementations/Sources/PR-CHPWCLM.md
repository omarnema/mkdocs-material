Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#PR-CHPWCLM (CHPW Claims Extract)

**Client(s)**: PRSEXT - *This is not a true client. It was created as a dummy client to extract data that is ultimately loaded into a prestaging database.*
**Density Area**: Northwest   

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
| Data Source Name| **CHPW Claims Extract** |
| Data Source Acronym| **PR-CHPWCLM** |
| Type | **Claims** |
| Site ID | **1** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|SEAMARTONL01|
|Port|1433|
|Name|QDW_Warehouse_Prd|
|User Name|svc_arcinfoqdw|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from *other/unknown*..

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20PR-CHPWCLM%20or%20%22Data%20Source%20Acronym%22%20~%20PR-CHPWCLM)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)