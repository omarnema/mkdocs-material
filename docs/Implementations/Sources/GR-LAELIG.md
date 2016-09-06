Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-17


#GR-LAELIG (Group Louisiana Eligibility)

**Client(s)**: [LHCQF](../LHCQF.md)  
**Density Area**: Southeast   

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture

**Note** This connector was replaced by the [LAMOELG](./LAMOELG.md) connector when LHCQF decided they wanted to replace the data provider for their eligibility feed. 


| Overview ||
|-----|-----|
| Data Source Name| **Group Louisiana Eligibility** |
| Data Source Acronym| **GR-LAELIG** |
| Type | **Claims** |
| Site ID | **5** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|GR-LAELIG_PRESTAGING_PRD|
|User Name|GR-LAELIG_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0260-GR-LAELIG_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|EDRegistry_Subscriber||
|-----|-----|
| Table Name | EDRegistry_Subscriber|
| File Name Pattern | EDRegistry_Subscriber|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Member_Num, Group_ID, Mem_Num_Suffix, Start_Date, End_Date, Med_Part_A_Ind, Med_Part_B_Ind, First_Name, Middle_Name, Last_Name, Gender, Home_Phone, DOB, Death_Date, SSN, Race, Addr_Line_1, Addr_Line_2, City, State, Zip, County_Code, Medicaid_ID  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None (prestaging)|
|Is the database production?| N/A (prestaging)  |
|Frequency of Extracts| Nightly. |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20GR-LAELIG%20or%20%22Data%20Source%20Acronym%22%20~%20GR-LAELIG)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)