Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-02-25
ModifyDate: 2016-02-25


#LASMHED (Slidell Memorial Hospital)

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
| Data Source Name| **Slidell Memorial Hospital** |
| Data Source Acronym| **LASMHED** |
| Type | **Clinical (ED)** |
| Site ID | **89** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|LASMHED_PRESTAGING_PRD|
|User Name|LASMHED_PRD_PRESTAGING|  


###Location Hierarchy Configuration

Nothing custom unless number of locations is very large. 

##Custom Configurations

See [onboarding process for LHCQF ED Registry connectors](./LHCQF-ED-Registry-Onboarding.md).

Should be a "copy and paste" of other ED Registry connectors. This connector is *not* subject to any LHCQF unencrypted file customizations.


##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\\\qdwsftp01\0427-PR-LASMHED_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Utilization||
|-----|-----|
| Table Name | Utilization|
| File Name Patterne | .|
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

*Not documented at this time.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20LASMHED%20or%20%22Data%20Source%20Acronym%22%20~%20LASMHED)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)