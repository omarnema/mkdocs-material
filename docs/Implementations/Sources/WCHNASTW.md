Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-10


#WCHNASTW (Western Connecticut Health Network - Allscripts Touchworks)

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
| Data Source Name| **Western Connecticut Health Network - Allscripts Touchworks** |
| Data Source Acronym| **WCHNASTW** |
| Type | **Clinical** |
| Site ID | **3** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLDEV01|
|Port|1433|
|Name|WCHNASTW_PRESTAGING_DEV|
|User Name|WCHNASTW_DEV_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is an AllScripts database that was restored on prestgsqldev01. Even though it is hosted on the prestaging server, it is not a true "prestaging" connector since the source of the data is not a set of flat files that we load into prestaging. 

There is no well-defined plan for future refreshes of this data, as restoring it is a long, manual process. We currently have a full set of data for 2015, which was needed for GPRO submission. 


##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None |
|Is the database production?| No  |
|Frequency of Extracts| Only needed when new database is restored.  |

##Known Issues

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.app.box.com/files/0/f/1888547619/4._Client_Specific_Material)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNASTW%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNASTW)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)