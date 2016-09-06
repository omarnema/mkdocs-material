Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-02-25
ModifyDate: 2016-02-25


#LARMC (LHCQF Riverland Medical Center)

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
| Data Source Name| **LHCQF Riverland Medical Center** |
| Data Source Acronym| **LARMC** |
| Type | **Clinical (ED)** |
| Site ID | **125** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|LARMC_PRESTAGING_PRD|
|User Name|LARMC_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

See [onboarding process for LHCQF ED Registry connectors](./LHCQF-ED-Registry-Onboarding.md).

Should be a "copy and paste" of other ED Registry connectors. This connector *is* subject to any LHCQF unencrypted file customizations (more documentation needed).

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0391-PR-LARMC_SFTP_PRD**.  
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

**Columns**: facilityname,universalid,messagedatetime,PatientID,PatientDateofBirth,Gender,MaritalStatus,StreetAddress,City,State,ZipCode,FirstName,MiddleName,LastName,SSN,PrimaryPhoneNumber,PrimaryInsuranceCompanyName,PrimaryInsuranceGroupNumber,PrimaryInsurancePolicyNumber,SecondaryInsuranceCompanyName,SecondaryInsuranceGroupNumber,SecondaryInsurancePolicyNumber,TertiaryInsuranceCompanyName,TertiaryInsuranceGroupNumber,TertiaryInsurancePolicyNumber,ChiefComplaint,VisitNumber,AdmitDateTime,AttendingPhysicianName,ReferringPhysicianName,AdmittingPhysicianName,DischargeDateTime,DiagnosisCode,DiagnosisText,DiagnosisCodingSystem,EmergencySecerityLevel,HL7Type  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20LARMC%20or%20%22Data%20Source%20Acronym%22%20~%20LARMC)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)