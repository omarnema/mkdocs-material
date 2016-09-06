Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-05-16
ModifyDate: 2016-05-18


#STWCLM (Steward Consolidated Claims Feed)

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
| Data Source Name| **Steward Consolidated Claims Feed** |
| Data Source Acronym| **STWCLM** |
| Type | **** |
| Site ID | **126** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|STWCLM_PRESTAGING_PRD|
|User Name|STWCLM_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

For the 6/30/2016 deadline to get HCC Navigator live for Steward, we do NOT need to operationalize the data loads for this.  We just need to load the historical files into prestaging and transform the data from there.

However, we WILL need to do this eventually. Before this can happen, we may need further conversations regarding source file formatting (zipped/encrypted), file naming conventions, and delivery method.


##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  See [**Documentation of the extract specifications**](https://arcadia.box.com/s/rl96xfrvyvqkusiyum35lqcrhq0utdb1) for more details.  

This is a set of unified claims data that comes from Athena.  The plans whose data are included in this extract are :  

* BCBS 
* TMP (Tufts Medicare Preferred)
* THP (Tufts Health Plan - Commercial)
* HPHC (Harvard Pilgrim)


These files should be loaded from the folder **\\qdwsftp01\0610-PR-STWCLM_SFTP_PRD**.  



##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| No, prestaging|
|Is the database production?| No, prestaging |
|Frequency of Extracts| One time historical for 6/30 deadline.  Incrementals TBD.  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20STWCLM%20or%20%22Data%20Source%20Acronym%22%20~%20STWCLM)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)