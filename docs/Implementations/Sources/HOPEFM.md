Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#HOPEFM (Hope Family Medicine)

**Client(s)**: [SLVTN](../SLVTN.md)  
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
| Data Source Name| **Hope Family Medicine** |
| Data Source Acronym| **HOPEFM** |
| Type | **Clinical** |
| Site ID | **8** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |

<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Contacts
| First Name | Last Name | Position             | Reports To | Email                  | Phone | Notes                                                                                                                                                                                                                                                                                            |
|------------|-----------|----------------------|------------|------------------------|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Eric       | North     | Practicing Physician | ---        | eric.m.north@gmail.com |       | Owns practice with his wife.  Decided to be his own system super user rather than delegating to an MA, so is very knowledgeable about his data.  Mission-driven practice, lovely space, lovely people.  Dr. North used to work for Drs. Peters at Northwest.  WVCH is paying for implementation. |

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|EHR-DBR|
|Port|1433|
|Name|NGReport|
|User Name|ext.arcadia|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The data for this connector is pulled from [NextGen 5.8](../../Tech_Delivery/EHR-Documentation/NextGen.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Contact the Solution Architect for details.*

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.app.box.com/files/0/f/1888547619/4._Client_Specific_Material)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20HOPEFM%20or%20%22Data%20Source%20Acronym%22%20~%20HOPEFM)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)