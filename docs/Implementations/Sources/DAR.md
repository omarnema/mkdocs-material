Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-07-20
ModifyDate: 2016-07-26


#DAR (Dar Medical Associates)

**Client(s)**: [AHP](../AHP.md), [XCLS](../XCLS.md)  
**Density Area**: New York   

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
| Data Source Name| **Dar Medical Associates** |
| Data Source Acronym| **DAR** |
| Type | **Clinical** |
| Site ID | **74** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|DAR_PRESTAGING_PRD|
|User Name|DAR_PRD_PRESTAGING|  


###Location Hierarchy Configuration

* AHP
    * AHP Community
		* Dar Medical Associates
     		* Dar Medical Associates
     		* Dar Medical Associates - Unknown Location
     	
##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0397-PR-DAR_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|allergies||
|-----|-----|
| Table Name | allergies|
| File Name Pattern | allergies|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE, ALLERGY, REACTION, TYPE, SEVERITY, STATUS, COMMENTS  

|demographic||
|-----|-----|
| Table Name | demographic|
| File Name Pattern | demographic|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE_OF_BIRTH, FIRST_NAME, MI, LAST_NAME, SEX, SSNUM, ACCOUNT_ID, ADDRESS_1, ADDRESS_2, CITY, STATE, ZIP, PHONE_1, PHONE_2, RACE, MARITAL_STATUS, DECEASED, DATE_OF_DEATH, LAST_DOV, PHYSICIAN_NAME, PHYSICIAN_NPI, ETHNICITY, LANGUAGE, PRIMARY_INSURANCE, PINSID, PID, SECONDARY_INSURANCE, SINSID, SID, PCP_Name, PCP_NPI, STATUS, DATE_OF_STATUS  

|encounters||
|-----|-----|
| Table Name | encounters|
| File Name Pattern | encounters|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, TYPE, DATE, LOCATION, PRACTITIONER, NPI, CODE, COMMENTS, PRIMARY_INSURANCE, PINSID, PID  

|futureappts||
|-----|-----|
| Table Name | futureappts|
| File Name Pattern | futureappts|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, TYPE, DATE, LOCATION, PRACTITIONER, NPI, COMMENTS  

|history||
|-----|-----|
| Table Name | history|
| File Name Pattern | history|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, HX_DATE, HX_DESCRIPTION, HX_STATUS, COMMENTS  

|meds||
|-----|-----|
| Table Name | meds|
| File Name Pattern | meds|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE_PRESCRIBED, DATE_DISCONTINUED, MED_NAME, MED_STRENGTH, MED_STRENGTH_UNIT, MED_FORM, MED_SIG, COMMENTS, NDC, REORDERED_DATE  

|problems||
|-----|-----|
| Table Name | problems|
| File Name Pattern | problems|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE_DIAGNOSIS, CODE, DIAGNOSIS, DATE_RESOLVED, DATE_INACTIVE, COMMENTS  

|procedures||
|-----|-----|
| Table Name | procedures|
| File Name Pattern | procedures|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE_OF_PROCEDURE, CODE, PROC_NAME, PROCEDURE_RESULT, COMMENTS  

|results||
|-----|-----|
| Table Name | results|
| File Name Pattern | results|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, TYPE, DATE_OF_TEST, NAME, RESULT, UNIT, LOINC, COMMENTS  

|shots||
|-----|-----|
| Table Name | shots|
| File Name Pattern | shots|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE, STATUS, VACCINE, REACTION, MANUFACTURER, LOT, CODE, CVX, NDC, COMMENTS  

|vitals||
|-----|-----|
| Table Name | vitals|
| File Name Pattern | vitals|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PKEY, PTID, DATE_OF_VISIT, VITALS_NAME, VITALS_RESULT, VITALS_UNIT, COMMENTS  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| Not applicable as the client provides the files |
|Is the database production?| Yes  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20DAR%20or%20%22Data%20Source%20Acronym%22%20~%20DAR)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/jjj9gc5sqinprno3749cr2fk9bnsyaf0)
- [SOW](https://arcadia.box.com/s/81vmvio34xf2brxqw8u7)
- [DQA](https://arcadia.box.com/s/64ptk9c6dbnk94t8tuu3ye4nm7m4q7yf)

