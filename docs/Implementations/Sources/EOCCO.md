Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-02-11
ModifyDate: 2016-02-11


#EOCCO - Eastern Oregon CCO

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
| Data Source Name| **Eastern Oregon CCO** |
| Data Source Acronym| **EOCCO** |
| Type | **Claims** |
| Site ID | **004** |
| Architecture Model | [**Backup+Restore to Prestaging**]|
| Database hosting | **Arcadia Prestaging** |




###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

The data will is sent as a DB backup from PHTech. PHtech also uses this model for a the Silverton WVCH data model [WVP](../~Implementations/~Sources/WVP/index.html)

The backups is historical and gets restored to prestaging on a weekly basis. The previous data gets truncated.

An SSIS job on the prestaging server will handle the backup + restore weekly, and a weekly connector will extract the data from prestaging on a weekly basis.

##Data Source

PH Tech for EOCCO. Same vendor as  [WVP](../~Implementations/~Sources/WVP/index.html)

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions|  *None* |
|Is the database production?| *None*  |
|Frequency of Extracts| The backup is sent weekly and will be sent at 5PM Eastern in the SFTP Folder.  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20{acronym}%20or%20%22Data%20Source%20Acronym%22%20~%20{acronym})%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)
