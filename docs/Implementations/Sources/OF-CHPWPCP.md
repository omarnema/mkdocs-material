Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#OF-CHPWPCP (PCP Data Extract)

**Client(s)**: [CHPW](../CHPW.md)  
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
| Data Source Name| **PCP Data Extract** |
| Data Source Acronym| **OF-CHPWPCP** |
| Type | **Clinical** |
| Site ID | **17** |
| Architecture Model | [**Custom**](../../Tech_Delivery/Standard-Implementations/Custom.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Custom.png">![](../../img/Connector-Custom.png)</a>



###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations
The specifications for the outbound files to be generated from the QDW 4.x production environments (below) are based on our understanding of the deprecated process used in the QDW 2.x environment. 

The source for the Informatica Cloud job for outbound files creation will be a QDW 4.x production warehouse database, with the following tables present. There will be no data filtering from any of these tables/views. In all cases a full extract will be created.

| QDW Source Table    | Destination (CSV Flat File Target)               |
|---------------------|--------------------------------------------------|
| Location_Master     | e.g. 2015_04_29_223400_003_001_Location.csv      |
| Site_Master         | e.g. 2015_04_29_223400_003_001_Site.csv          |
| Provider_Master     | e.g. 2015_04_29_223400_003_001_Provider.csv      |
| v_patient_roster*   | e.g. 2015_04_29_223400_003_001_Patient.csv       |
| v_encounter_roster* | e.g. 2015_04_29_223400_003_001_Encounter.csv     |
| mpi_person_member   | e.g. 2015_04_29_223400_003_001_PersonMember.csv  |
| mpi_person_patient  | e.g. 2015_04_29_223400_003_001_PersonPatient.csv |

*tables/views containing data for only a limited subset of patients required for this extract.

##Target Definition
The target for the Informatica Cloud job for outbound files creation will be encrypted flat files that contain data in the format specified above
  
###Naming Convention
The target output file will adhere to the following naming convention:  

	YYYY_MM_DD_HHMMSS_ClientID_SiteID_ExtractQueryName.csv

	e.g. 2015_04_29_223400_003_001_PersonPatient.csv 
	
###File Sizing
Each target output file will be split into multiple files, each of which will contain a maximum of 500,000 rows of data so that they are within the parameters necessary for encryption through Informatica. Upon split, each file name will be appended with \_# indicating the sequence in which the files were split. For instance, if the above example file name contained 1.3 million rows, the split files would be named as follows: 

	1.	2015\_04\_29\_223400\_003\_001\_PersonPatient\_1.csv (500,000 rows),  
	2.	2015\_04\_29\_223400\_003\_001\_PersonPatient\_2.csv (500,000 rows) and,   
	3.	2015\_04\_29\_223400\_003\_001\_PersonPatient\_3.csv (300,000 rows) 

###Encryption
CHPW will provide PGP public keys for use in the encryption process.

##Data Source
Warehouse



##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A |
|Is the database production?| Yes |
|Frequency of Extracts| Run weekly;9AM EST on Mondays. |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20OF-CHPWPCP%20or%20%22Data%20Source%20Acronym%22%20~%20OF-CHPWPCP)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)