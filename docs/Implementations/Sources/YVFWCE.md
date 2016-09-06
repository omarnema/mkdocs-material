Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-06-11
ModifyDate: 2016-06-11


#YVFWCE (Yakima Valley Farm Workers Clinic - Epic )

**Client(s)**: [CCCN](../CCCN.md), [CHPW](../CHPW.md), [SLVTN](../SLVTN.md), [MODA](../MODA.md)  
**Density Area**: Northwest   

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture

For CCCN and SLVTN is replacing the [deprecated IC-Chart YVFWC](../~Implementations/~Sources/YVFWC/index.html) connector which was deprecated ON Aug 2015  

| Overview ||
|-----|-----|
| Data Source Name| **Yakima Valley Farm Workers Clinic** |
| Data Source Acronym| **YVFWCE** |
| Type | **Clinical** |
| Site ID | **21** |
| Architecture Model | [**Client-DB-Extract-Prestaging**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|Arcadia Prestaging|
|DB|YVFWCE_PRESTAGING_DB|



###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled by YVFWC from [Epic](../../Tech_Delivery/EHR-Documentation/Epic.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Contact the Solution Architect for details.*

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.box.com/s/1mc49mq66emtd17hvlpq2knb5eb7phye)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20YVFWC%20or%20%22Data%20Source%20Acronym%22%20~%20YVFWCE)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)