Status: Internal-Only
Author: Amrit Sridhar
CreateDate: 06-15-2016
ModifyDate: 06-15-2016


#LAORION (LHCQF LaHIE feed)

**Client(s)**: [LHCQF] (../LHCQF.md)
**Density Area**: Southeast

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
| Data Source Name| **LHCQF LaHIE feed** |
| Data Source Acronym| **LAORION** |
| Type | **Clinical** |
| Site ID | **001** |
| Architecture Model | [**{ArchitectureModelName}**](../../Tech_Delivery/Standard-Implementations/{ArchitectureModelHypens}.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/LHCQF_LAORION.png">![](../../img/Connector-{ArchitectureModelHypens}.png)</a>


###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|LHCQFSQLPRD02, QDWSQLQA02, QDWSQLDEV02|
|Port|1433|
|Name|LHCQF_PRESTAGING_PRD02, LHCQF_PRESTAGING_UAT, LHCQF_PRESTAGING_DEV|
|User Name|LHCQF_PRD02_INFORMATICA, LHCQF_UAT_INFORMATICA, LHCQF_DEV_INFORMATICA|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

This data feed is entirely a custom feed as a result of the migration of an SSIS package from the 3.X platform to the 4.X platform. It is imperitive that files are loaded in sequential order. If they are not, a restore must happen and re-processing of the files in sequential order will then occur. Additionally the files are processed in a set of 26 As a result, there are several constraints in processing the data.

The feed in question has two working mechanisms

1. Prestaging Load
2. CDC Connector

Prestaging for this data feed is located on the same environment that the warehouse due to the nature of the custom SSIS package. Only LHCQF PRD02 has current LaHIE data in it.

Files are dropped by Orion into \\QDWSFTP01\LHCCQF_SFTP_PRD
These files are processed by the LHCQF_EXTRACT_PRD02 nightly job on LHCQFSQLPRD02.
This nightly job processes the files into the prestaging database, and then generates a CDC extract that pulls from these tables to be loaded into the warehouse database.

In more details, the custom LHCQF_EXTRACT_PRD02 job contains the below steps
1. Validate Extract Status
  --This step references that the last extract was successfully generated. It is a requirement to proceed with further file processing.
2. Move Files to Local SFTP
  --This moves the Orion source files to the local LHCQFSQLPRD02 server for processing through the legacy ssis package
3. Run SSIS
  --This is the 3.X ssis package that processes the source ORION files into the prestaging database. The data is loaded into a legacy schema, and then executes a stored procedure dbo.truncateloadstructured to load this data into a "structured" schema. This data gets truncated on a nightly basis. Additionally, this triggers an insert of "0" into the dbo.extractactivity table that will be followed by a "1" from a successful extract
4. Run Informatica Extract
  --This triggers an informatica CDC extract to run off of the data held in the structured schema. An additional task found in the LAORION taskflow runs to validate that there is an expected number of output files. This logs a record = '1' in the dbo.extractactivity table in order to ensure that the files were appropriately processed. This data is dropped into the "Extracted_Data" subfolder for 0227-LAORION_SFTP_PRD02, to be moved into the parent folder by the QDW nightly job.

In the regular QDW Nightly job, there is a custom step in the nightly job "Move Extracted Files" prior to the informatica load that moves the set of extracted files into the parent folder to be picked up by the informatica load taskflow. This is to ensure that only one set of files is loaded in sequence into warehouse as per the initial requirement

##Points of Failure

With these custom steps in the nightly job, there are a few breakpoints that are not part of standard troubleshooting. As a rule of thumb, if the prestaging load fails you *must* restage the set of 26 files of the day processed from LHCQFSQLPRD02//D:Clients/LHCQFPRD02/ARCHIVE to QDWSFTP01//LHCQF_SFTP_PRD

1. Validate Extract Status fail
a. Ensure that extracted_data subfolder is empty. If not empty, load in the data and manually insert data into lhcqf_prestaging_prd02.dbo.extractactivity ('1',getdate(),'<Error Message Remediation')
b. Check to see if the most recent record in dbo.extractactivity has a status = '1'. If not, then you may need to regenerate the extract or figure out why it did not log to the table. 
2. Move Files Fail
a. Ensure that there are a set of 26 files, or multiple of 26 files in QDWSFTP01//LHCQF_SFTP_PRD

**If we fall behind one day on extracts, do the following workflow**
1. Send out a change request to decrease Nightly Job Cutoff to "00:01"
2. Run the extract Job
3. Load data into warehouse by starting nightly job 
4. Repeat steps 2 & 3 as needed 
5. Send out a change request to increase nightly job cutoff to "04:00"

##Data Source

The source of this data is found in the prestaging database on the same server. These load the data into a "structured" schema that mimics the staging environment. A CDC connector pulls a 1:1 mapping to load into warehouse.

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *NONE* |
|Is the database production?| *NO* |
|Frequency of Extracts| *Scheduled to start processing at 3 PM*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20{acronym}%20or%20%22Data%20Source%20Acronym%22%20~%20{acronym})%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)
