Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#FHCNRES (Family Health Center Results)

**Client(s)**: [FHN](../FHN.md)  
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
| Data Source Name| **Family Health Center Results** |
| Data Source Acronym| **FHCNRES** |
| Type | **Clinical** |
| Site ID | **1** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|Reporting01|
|Port|1433|
|Name|Mobiledoc|
|User Name|ArcadiaInformatica|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [eCW 10](../../Tech_Delivery/EHR-Documentation/eCW.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20FHCNRES%20or%20%22Data%20Source%20Acronym%22%20~%20FHCNRES)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)