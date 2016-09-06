Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-25


#WCHNAFP (Western Connecticut Health Network - Associated Family Physicians)

**Client(s)**: [WCHN](../WCHN.md)  
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
| Data Source Name| **Western Connecticut Health Network - Associated Family Physicians** |
| Data Source Acronym| **WCHNAFP** |
| Type | **Clinical** |
| Site ID | **18** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|jupiter-2008r2\LYTECMD|
|Port|1433|
|Name|Associated Family Physicians|
|User Name|SA|  


###Location Hierarchy Configuration

Nothing custom. Within VCA it should be under the WCHN parent location.

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [McKesson Practice Interface Center 2.2.2.32](../../Tech_Delivery/EHR-Documentation/McKesson-Practice-Interface-Center.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| EHR Front End Access limited to: Tues after 1 PM. Wed All day. Th after 3:30 PM, Fri All Day|
|Is the database production?| **Yes** |
|Frequency of Extracts| Daily  |

##Known Issues

*Not documented at this time.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNAFP%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNAFP)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)