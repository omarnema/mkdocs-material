Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#MAHHROGAR (Mahoney, Hrohoe & Garneau)

**Client(s)**: [AHP](../AHP.md), [XCLS](../XCLS.md)  
**Density Area**: New York   

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
| Data Source Name| **Mahoney, Hrohoe & Garneau** |
| Data Source Acronym| **MAHHROGAR** |
| Type | **Clinical** |
| Site ID | **49** |
| Architecture Model | [**Direct Feed (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Direct-Feed.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Direct-Feed.png">![](../../img/Connector-Direct-Feed.png)</a>



###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

Source of data is a flat file provided by the client that meets the Arcadia specifications and is loaded directly into staging.

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20MAHHROGAR%20or%20%22Data%20Source%20Acronym%22%20~%20MAHHROGAR)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)