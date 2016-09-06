Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#FMOLOL (Franciscian Missionaries of Our Lady Health System, QDW 4.X)

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
| Data Source Name| **Franciscian Missionaries of Our Lady Health System, QDW 4.X** |
| Data Source Acronym| **FMOLOL** |
| Type | **Clinical** |
| Site ID | **19** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|FMOLOL_PRESTAGING_PRD|
|User Name|FMOLOL_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0279-PR-FMOLOL_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Assessment||
|-----|-----|
| Table Name | Assessment|
| File Name Pattern | Assessment|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, assessment_assessment_id, encounter_id, patient_id, assessment_icd9_code, assessment_primary_diagnosis_ind, assessment_create_timestamp, assessment_modify_timestamp, assessment_delete_ind  

|Charge||
|-----|-----|
| Table Name | Charge|
| File Name Pattern | Charge|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, charge_charge_id, encounter_id, patient_id, charge_cpt_code, charge_create_timestamp, charge_modify_timestamp, charge_delete_ind  

|Encounter||
|-----|-----|
| Table Name | Encounter|
| File Name Pattern | Encounter|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, encounter_id, patient_id, provider_id, encounter_location, encounter_type, encounter_encounter_date, encounter_create_timestamp, encounter_modify_timestamp, encounter_delete_ind  

|Patient||
|-----|-----|
| Table Name | Patient|
| File Name Pattern | Patient|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, patient_id, patient_MRN, patient_first_name, patient_last_name, patient_sex, patient_race, patient_ethnicity, patient_language, patient_address1, patient_city, patient_state, patient_zip, patient_birth_date, patient_create_timestamp, patient_modify_timestamp, patient_delete_ind, patient_ssn, patient_opt_in_ind  

|Payer||
|-----|-----|
| Table Name | Payer|
| File Name Pattern | Payer|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, payer_payer_id, patient_id, payer_name, payer_create_timestamp, payer_modify_timestamp, payer_delete_ind, payer_payer_order, payer_policy_start, payer_policy_end  

|Provider||
|-----|-----|
| Table Name | Provider|
| File Name Pattern | Provider|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, provider_id, provider_first_name, provider_last_name, provider_national_provider_id, provider_create_timestamp, provider_modify_timestamp, provider_delete_ind  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20FMOLOL%20or%20%22Data%20Source%20Acronym%22%20~%20FMOLOL)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)