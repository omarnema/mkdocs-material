Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-25


#GR-LAED (Group Louisiana Emergency Departments)

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

| Overview ||
|-----|-----|
| Data Source Name| **Group Louisiana Emergency Departments** |
| Data Source Acronym| **GR-LAED** |
| Type | **Clinical** |
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
|Name|GR-LAED_PRESTAGING_PRD|
|User Name|GR-LAED_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0259-GR-LAED_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Utilization||
|-----|-----|
| Table Name | Utilization|
| File Name Pattern | .|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: FacilityName, UniversalId, MessageDateTime, PatientId, PatientDOB, PatientGender, PatientMaritalStatus, PatientStreetAddress, PatientCity, PatientState, PatientZipCode, PatientFirstName, PatientMiddleName, PatientLastName, PatientSSN, PatientPrimaryPhone, PrimaryInsuranceCompanyName, PrimaryInsuranceGroupNumber, PrimaryInsurancePolicyNumber, SecondaryInsuranceCompanyName, SecondaryInsuranceGroupNumber, SecondaryInsurancePolicyNumber, TertiaryInsuranceCompanyName, TertiaryInsuranceGroupNumber, TertiaryInsurancePolicyNumber, ChiefComplaint, VisitNumber, AdmitDateTime, AttendingPhysicianName, ReferringingPhysicianName, AdmittingingPhysicianName, DischargeDateTime, DiagnosisCode, DiagnosisText, DiagnosisCodingSystem, EmergencySeverityLevel  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None |
|Is the database production?| No. Prestaging |
|Frequency of Extracts| Nightly  |

##Known Issues

*Contact the Solution Architect for details.*

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.app.box.com/files/0/f/1888547619/4._Client_Specific_Material)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20GR-LAED%20or%20%22Data%20Source%20Acronym%22%20~%20GR-LAED)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)