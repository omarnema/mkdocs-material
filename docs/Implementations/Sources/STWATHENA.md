Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-07-25
ModifyDate: 2016-07-25


#STWATHENA (Steward Athena Data Warehouse Feed)

**Client(s)**: [STW](../STW.md)  
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
| Data Source Name| **Steward Athena Data Warehouse Feed** |
| Data Source Acronym| **STWATHENA** |
| Type | **Clinical** |
| Site ID | **127** |
| Architecture Model | **CDC/Custom**|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>



###Location Hierarchy Configuration

TBD based on data that comes in. Should start with single-level hierarchy, but may need to be adjusted given that the data are coming from a combined warehouse so we might need to break down further. 

##Custom Configurations

###SFTP Customization for Steward Sources  

See [**Steward Custom SFTP Workflow**](.\STW-Custom-SFTP-Workflow.md). 

##Data Source

This data is from a warehouse set up by Steward which contains a consolidation of a large number of Athena Data Warehouse feeds. 

The data for this connector is pulled from [Athena 0](../../Tech_Delivery/EHR-Documentation/Athena.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| The warehouse is refreshed every morning, so we should pull after business hours.  Also, to work around their loads, we should add nolock hints to all of our queries.  |
|Is the database production?| No  |
|Frequency of Extracts| Nightly  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20STWATHENA%20or%20%22Data%20Source%20Acronym%22%20~%20STWATHENA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)