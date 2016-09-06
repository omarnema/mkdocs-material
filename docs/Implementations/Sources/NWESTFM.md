Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#NWESTFM (Northwest Family Medicine)

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
| Data Source Name| **Northwest Family Medicine** |
| Data Source Acronym| **NWESTFM** |
| Type | **Clinical** |
| Site ID | **7** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |

<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

####Contacts
| Name           | Position             | Reports To | Email                  | Notes                                                                                                                                         |
|----------------|----------------------|------------|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Sarah Peters   | Practicing Physician | ---        | sarahp@nwfm.mvipa.org  | MUST COMMUNICATE BY CALLING OFFICE AND GOING THROUGH MA (JERRICA MACK).  Key decision maker for practice.  WVCH is paying for implementation. |
| Timothy Peters | Practicing Physician | ---        | tpeters@nwfm.mvipa.org | Dr. Sarah's husband; purchases technical items for practice and handles things like network, Microsoft Office, etc.                           |
| Shasta Stocker | Medical Assistant    | Dr. Sarah  | sstocker19@gmail.com   | MA; has external commitments and may not be continuously employed by practice.                                                                |
| Jerrica Mack   | Medical Assistant    | Dr. Sarah  | jmack@nwfm.mvipa.org   | Coordinator for Dr. Sarah Peters.                                                                                                             |
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

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20NWESTFM%20or%20%22Data%20Source%20Acronym%22%20~%20NWESTFM)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)