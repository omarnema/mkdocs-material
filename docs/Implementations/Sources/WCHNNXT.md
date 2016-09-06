Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-23


#WCHNNXT (Western Connecticut Health Network- NextGen)

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

The actual name of this site is **New Milford Medical Group (NMMG)**, so it may be referred to as that. 

| Overview ||
|-----|-----|
| Data Source Name| **Western Connecticut Health Network- NextGen** |
| Data Source Acronym| **WCHNNXT** |
| Type | **Clinical** |
| Site ID | **7** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|172.17.0.31/NJNGTSTSQL1A1EST|
|Port|1433|
|Name|NGProd_NMMG|
|User Name|NMMG_Arcadia|  


###Location Hierarchy Configuration

In VCA environment, so should be placed under a WCHN parent location with other WCHN sites. Otherwise, no specific requirements. 

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a NextGen EHR. 

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None. |
|Is the database production?| No |
|Frequency of Extracts| Nightly  |

##Known Issues

Client will not grant access to EHR Front End for testing, so we are unable to test the connector beyond the DQA and ETL row count tests. 

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNNXT%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNNXT)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/534lp9c40msdjggzaq1298sgf0f77jhp)
- [Handoff Doc](https://arcadia.box.com/s/j2gm8ah6spvektwy3pkcmw50vz3dd6ux)
- SOW (*Unknown. Follow up with the Solution Architect*)