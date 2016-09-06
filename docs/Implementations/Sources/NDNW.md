Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-02-11
ModifyDate: 2016-02-11


#NDNW - New Directions NW

**Client(s)**: [GOBHI](../GOBHI.md)  
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
| Data Source Name| **New Directions NW** |
| Data Source Acronym| **NDNW** |
| Type | **Informatica Extract** |
| Site ID | **{DBID}** |
| Architecture Model | [**{ArchitectureModelName}**](|
| Database hosting | **{hosting}** |





###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

Hosted by GOBHI on same database as [GOBHI Eligibility - GOBHIELG](../~Implementations/~Sources/GOBHIELG/index.html). New Directions sends GOBHI a backup which they restore.

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20CCS%20or%20%22Data%20Source%20Acronym%22%20~%20CCS)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)
