Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-25


#WCHNBLUM (Western Connecticut Health Network - Dr. Blum)

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
| Data Source Name| **Western Connecticut Health Network - Dr. Blum** |
| Data Source Acronym| **WCHNBLUM** |
| Type | **** |
| Site ID | **15** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|BLUMMD\LYTECMD|
|Port|1433|
|Name|mck_PracticePartner|
|User Name|Arcadia|  


###Location Hierarchy Configuration

Nothing custom. Within VCA it should be under the WCHN parent location.

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [McKesson Practice Interface Center 2.2.2.32](../../Tech_Delivery/EHR-Documentation/McKesson-Practice-Interface-Center.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions|**YES: Limited number of Concurrent EHR Front End Logins**|
|Is the database production?| **YES**  |
|Frequency of Extracts| Nightly  |

##Known Issues

* Data is being pulled from two backend databases called ‘Blum’ and ‘mck_PracticePartner’. These two databases do not contain standardized encounter_id fields and lack unique primary keys that explicitly join tables. 
* There are 4 VPN and 2 RDP licenses  available to access this client's backend content. Please *DO NOT INSTALL SOFTWARE* unless you contact the VCA-lead for one of these key. 
* The following licenses are in use as of 1/26/16 .  
	* VPN 1 (RDP 2)
	* VPN 2
	* VPN 3 
	* VPN 4 (RDP 1)
* SFTP Folder Location: 0349-WCHNBLUM



##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNBLUM%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNBLUM)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)