Status: Internal-Only
Author: {SA}
CreateDate: {now}
ModifyDate: {now}


#{acronym} ({name})

**Client(s)**: {Clients}  
**Density Area**: {density}   

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
| Data Source Name| **{name}** |
| Data Source Acronym| **{acronym}** |
| Type | **{type}** |
| Site ID | **{DBID}** |
| Architecture Model | [**{ArchitectureModelName}**](../../Tech_Delivery/Standard-Implementations/{ArchitectureModelHypens}.md)|
| Database hosting | **{hosting}** |


<a href="../../../img/Connector-{ArchitectureModelHypens}.png">![](../../img/Connector-{ArchitectureModelHypens}.png)</a>

{connectivity}

###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

{dataSource}

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20{acronym}%20or%20%22Data%20Source%20Acronym%22%20~%20{acronym})%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)
