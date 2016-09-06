Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-26


#ACPCLN (Arizona Community Physicians Clinical Data)

**Client(s)**: [ACP](../ACP.md)  
**Density Area**: Southwest   

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
| Data Source Name| **Arizona Community Physicians Clinical Data** |
| Data Source Acronym| **ACPCLN** |
| Type | **Clinical** |
| Site ID | **1** |
| Architecture Model | [**Client DB Extract**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract.md)|
| Database hosting | **External** |


<a href="../../../img/Connector-Client-DB-Extract.png">![](../../img/Connector-Client-DB-Extract.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|TWSQL|
|Port|1433|
|Name|Works|
|User Name|arcadia|  


###Location Hierarchy Configuration

Nothing custom required. All locations can roll up to the single data source parent. 

##Custom Configurations

ACPCLN does not contain charge data. The configuration of the workflow at ACP is to use AllScripts for clinical entries, and IDX for billing/scheduling. As a result, measure calculation was very low for ACPCLN on its own, and a second connector, [ACPIDX](./ACPIDX.md), was built to capture this billing data, and the two should be brough together through the MPI. 

ACPCLN also does not contain all clinical data - there is a separate repository QIS that contains some additional information that has to be mapped separately.

This data source is **extremely large** and as a result we have take a few measures for implementing bug fixes:  
* Stood up a second, lightweight environment for bug fixes (ACP2) on  a very small subset of patients.
* The AllScripts queries have been updated to include a `TestPatientSwitchBit` and `TestPatientIDList` parameter that can be used to quickly iterate bug fixes before testing on the full data set. 
* Extracts have been limited for most tables to 2013 to present, with certain queries going back 5 years and others being full historical (e.g. patient, provider)
* For maintenance and result queries, we are deliberately excluding specific unscrubbed types that are not being used for anything and were previously giving us >35 million records each. We also have the go ahead to only pull patients who have had an encounter after 2011. For details on these changes, see this [JIRA Ticket](https://jira.arcadiasolutions.com/browse/AAI-22253).

the second light weight environment is called ACP2

###ACP2 Environment

the database is found on 
*server:QDWSQLDEV05
*names: ACP2_Warehouse_DEV and ACP2_staging_DEV

there is no separate ACP2 connector set up - run the ACP DEV connector then copy the data from the DEV folder ( \\qdwsftp01\0302-ACPCLN_SFTP_DEV ) to the ACP2 DEV folder ( \\qdwsftp01\0424-ACPCLNTOO_SFTP_DEV ). once the data is there you can kick of the nightly job run in ACP2. As a DEV environment there is no front end on ACP2. The intention is to only load test patients into ACP2 to keep job run times to an absolute minimum, i.e. full run completed in 30 mins.

###Test Patient Filter

Test patient loads are conducted by modifying the extract tasks in DEV the two key parameters are:
1. testpatientswitchbit : this is set to 1 or 0. 1 turns the filter on, 0 turns it off
2. testpatientclientidlist ; this is a list of ids for patients whose data you wish to pull - this should be all test patients. Ideally this is set up as part of the integration, less ideally it will be the patient_original_ids for each patient in every open ticket.

to use the filter set the above in each query in the connector studio tasks pane. Set each query switchbit to 1 and include your list 'id one', 'id two',... 'id n' in every testpatientclientidlist field.  Then push the tasks to the cloud, run the DEV extract, move the files from the ACP DEV sFTP folder to the ACP2 DEV sFTP folder and kick off the job in ACP2. All these stesp should be very fast since the volume of data is massively curtailed. This should allow you to iterate on all fixes rapidly - even more so if you maintain a script you an execute on the ACP2_WAREHOUSE_DEV database that checks for the state indicating that all the bugs are fixed. 

##Data Source

The data for this connector is pulled from [AllScripts Enterprise 11.2](../../Tech_Delivery/EHR-Documentation/AllScripts-Enterprise.md).

Additional info for **Round 2 - QIS and Deceased Patients Updates**:  
* Deceased patient logic was already implemented as a support ticket, so only scope is capturing screenings entered during QIS
* Basic premise of the QIS workflow is that the providers enter screenings (e.g. fall risk screenings) thought a QIS module, and that action triggers the creation of a structured result. A very useful resource is this [recording of the Dr. Adler demonstrating the workflow](https://arcadia.box.com/s/jvsj9u1dkga81uwfq07j34zevt52n6gx). 
* Requirement is to capture all relevant screenings for the product as described in that video and pull them into maintenance. Seeds should go through clinical review (may be easiest to load just this data into staging then run the seeding procedure to limit the data being pulled into the seed extract). 

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Extract after business hours |
|Is the database production?| **Yes** |
|Frequency of Extracts| Nightly |

##Known Issues

Documented in [handoff document](https://arcadia.box.com/s/4ipisx794ojhodz2j2jtgiehcsdbcu8s)

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.app.box.com/files/0/f/1888547619/4._Client_Specific_Material)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20ACPCLN%20or%20%22Data%20Source%20Acronym%22%20~%20ACPCLN)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/78co4837cxmdi4fnqi4lyv8u59x0bosr)
- SOW - See [ACP](../ACP.md) Page
