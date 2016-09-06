Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-06-11


#CCW (Coordinate Care Claims)

**Client(s)**: [CCCN](../CCCN.md)  
**Density Area**: Northwest   

**Note:** CCW is an internal Arcadia acronym and is not used by Coordinated Care.

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture


Coordinated Care is a managed care organization and a subsidiary of Centene. 


A pending CR to improve to work with Coordinated Care to build a new connector that is per spec.



| Overview ||
|-----|-----|
| Data Source Name| **Coordinate Care Claims** |
| Data Source Acronym| **CCW** |
| Type | **Claims** |
| Site ID | **6** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |



<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|CCW_PRESTAGING_PRD|
|User Name|CCW_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*N/A*

##Custom Configurations

In addition to the standard core data elements needed for Arcadia Analytics, CCW is not sending Arcadia


##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |


##New Connector

Due to some of the previous limitation this connector is being completely rebuilt from new data. The DB will keep the same acronym and prestaging database

[Issue Tracking Log for New CCW Connectpr](https://arcadia.box.com/s/5fnu7t4x7eqe99tzxplvkjjr2bsr0dd0)

##Known Issues


**Future Requirement**: must map fee_for_service_equivalent in next connector

Discrepancies were identified in the CCCN custom reconciliation reports that were traced back to gaps in CCW’s provided eligibility and assignments data. Historic records that have since been removed/deleted/inactivated were not getting updated in incremental extracts. To address this, Arcadia requested CCW to switch to monthly historical extracts. However, the issue still persisted as the historical extract did not always include updates to the old records that have since been invalidated.

Custom procedures exist to load in eligibility and assignment as a work around for the fact that historic eligibility and assignments that are not included in feeds and previous active assignments/enrollments are not marked with an end date. See [CCCN](../CCCN.md) Custom Procedures

Missing or inconsistent delete indicators and update timestamps

| Medical Claims | Delete Indicator | Source Updated Timestamp                 |
|----------------|------------------|------------------------------------------|
| Product        | No               | No update or insert date – Run date only |
| Provider       | No               | Yes                                      |
| RX Claims      | Yes              | Yes                                      |
| Claims         | Yes              | Yes                                      |
| Membership     | Yes              | Yes*                                     |

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0001-CCW_SFTP_PRD**.  


Coordinate Care sends Arcadia monthly data extracts.

* Provider\_yyyymmdd.txt
* Product\_yyyymmdd.txt
* Medical\_claims\_Enhancement_yyyymmdd.txt
* Medical\_claims_yyyymmdd.txt
* Premium\_Payments_yyyymmdd.txt
* Rx_Claims\_yyyymmdd.txt
* PCP\_Capitation_yyyymmdd.txt
* Member\_yyyymmdd.txt

 

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20CCW%20or%20%22Data%20Source%20Acronym%22%20~%20CCW)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)