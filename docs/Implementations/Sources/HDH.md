Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-06-06
ModifyDate: 2016-06-06


#HDH (Harney District Hospital)

**Client(s)**: [MODA](../MODA.md)  
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
| Data Source Name| **Harney District Hospital** |
| Data Source Acronym| **HDH** |
| Type | **Clinical** |
| Site ID | TBD |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|TBD|
|Host|TBD|
|Port|TBD|
|Name|TBD|
|User Name|TBD|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

###Clinic Details
8 providers  
9,500 active patients  

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [Centricity](../../Tech_Delivery/EHR-Documentation/Centricity.md).



##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20CARE%20or%20%22Data%20Source%20Acronym%22%20~%20HDH)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)