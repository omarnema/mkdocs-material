Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#CHPW (Community Health Plan of Washington)
###(Retired CCCN Connector)

**Client(s)**: [CCCN](../CCCN.md)  
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
| Data Source Name| **Community Health Plan of Washington** |
| Data Source Acronym| **CHPW** |
| Type | **Claims** |
| Site ID | **5** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|CHNWPRODDB01.CHPWQDW.LOCAL|
|Port|1433|
|Name|CHDSTransformDB|
|User Name|CCCN_PRD_Informatica|  

##Current State:
CHPW is a legacy claims connector for CCCN instances of Arcadia Analytics

####CCCN Connector:
Data was pulled from a 2.x CHPW environment Arcadia has retired as of 12/31/15.


##Future State: 
Replicate Source system to Arcadia and have multiple “smart” (i.e. normalization) Connectors from the prestaging database at Arcadia to the Arcadia Analytics destinations.

![CHPW Source Diagram](../img/chpw_source_diagram.jpg)



####Custom CCCN Premium Feeds
In addition, custom premium related feeds will need to exists for the CCCN connector. The details on the exact tables and connector queries are still in development. However, this can happen at another stage as getting the connector for the core tables is the priority right now.



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
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20CHPW%20or%20%22Data%20Source%20Acronym%22%20~%20CHPW)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)