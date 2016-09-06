Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-04-01
ModifyDate: 2016-04-05


#GEOGAG (George Gagne, MD)

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

This is a Steward "Black Box" connector, meaning we have set up a desktop computer with Informatica installed connected to the practice's network with  to connect to their databases.   

| Overview ||
|-----|-----|
| Data Source Name| **George Gagne, MD** |
| Data Source Acronym| **GEOGAG** |
| Type | **Clinical** |
| Site ID | **112** |
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **External** |

<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MySQL|
|Host|192.168.1.10|
|Port|4928|
|Name|mobiledoc|
|User Name|Arcadia01|  


###Location Hierarchy Configuration

Locations seeds are not required for initial integration.

##Custom Configurations

1. Queries for this connector are to be a direct conversion of existing DRVS queries into syntax that Informatica can use. There should be no updates or additions to these queries beyond what is needed to run the end-to-end ETL and match the content of the existing HDS feed.
2. The criteria for handoff acceptance are as follows:  
- Row counts match counts extracted since most recent historical extract in 3.x; The full table row counts do not need to match exactly, due to data no longer existing in the same state in the eCW DB. 
- Date field completeness -- % completeness of date fields should match those of the 3.x tables within a reasonable error. This is being tested due to the tight constraints placed on date formatting in Informatica.
3. **Seed data should match exactly that of the 3.x instance within the constraints of the new environment. No new seed mapping is required.**
4. `t_immunization` is not used. Immunizations at Steward are pulled into `t_maintenance` with the *maintenance_imm* query. 


**Notes:** This source is NOT subject to the Steward SFTP Get customizations. These query/seed requirements will be updated in the future, but for the intial migration project this is correct.

##Data Source

The data for this connector is pulled from [eCW 9](../../Tech_Delivery/EHR-Documentation/eCW.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None |
|Is the database production?| No  |
|Frequency of Extracts| Nightly |

##Known Issues


* Queries are based off of historical eCW queries, i.e., certain known issues may still apply.  
* Additional Client Literature [Click Here](https://arcadia.app.box.com/files/0/f/3940812891/Per-Site%20Gap%20Analysis)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20GEOGAG%20or%20%22Data%20Source%20Acronym%22%20~%20GEOGAG)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/3pctsu7aqbvxzonk7b020khs0x1zerg9)
- SOW - Many