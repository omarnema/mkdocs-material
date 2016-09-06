Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#URMC (University Rochester Medical Center)

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
| Data Source Name| **University Rochester Medical Center** |
| Data Source Acronym| **URMC** |
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
|Name|URMCID_PRESTAGING_PRD|
|User Name|URMCID_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0069-URMC_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Allergy||
|-----|-----|
| Table Name | Allergy|
| File Name Pattern | allergy|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, allergy_id, patient_id, encounter_id, type, description, reaction, ndc_code, onset_date, resolved_date, create_timestamp, delete_ind, modify_timestamp, loaded_from_file, severity  

|Appointment||
|-----|-----|
| Table Name | Appointment|
| File Name Pattern | Appointment|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, appointment_id, patient_id, encounter_id, provider_id, appointment_date, create_timestamp, modify_timestamp, delete_ind, kept, canceled, rescheduled, loaded_from_file, appt_reason, billed_ind, location  

|Assessment||
|-----|-----|
| Table Name | Assessment|
| File Name Pattern | Assessment|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, assessment_id, problem_id, encounter_id, provider_id, patient_id, assessment_severity, assessment_description, assessment_notes, icd9_code, assessment_date, primary_diagnosis_ind, create_timestamp, modify_timestamp, created_by, modified_by, delete_ind, loaded_from_file, icd10_code  

|Encounter||
|-----|-----|
| Table Name | Encounter|
| File Name Pattern | encounter|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, encounter_id, patient_id, provider_id, location, type, encounter_date, create_timestamp, delete_ind, modify_timestamp, loaded_from_file, locked_ind, locked_timestamp, signed_ind, signed_timestamp, no_known_allergy_ind, no_known_medication_ind, no_known_problem_ind, type_description, dept_description, orig_dept_id, appointment_id, reason, dental_ind, optometry_ind, behavioral_ind, enabling_ind, discharge_timestamp, progress_note_ind, opt_out_ind  

|Exclusion||
|-----|-----|
| Table Name | Exclusion|
| File Name Pattern | exclusion|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Center_ID, ExclusionID, Patient_ID, Line, NPI, Measure, Exclusion_Type, Exclusion_Reason, Exclusion_Start_Date, Exclusion_End_Date, Deleted_Ind, Created_Time, Modified_Time  

|Immunization||
|-----|-----|
| Table Name | Immunization|
| File Name Pattern | Immunization|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, immunization_id, patient_id, encounter_id, type, completed_date, cpt_code, cvx_code, dose, units, lot_number, manufacturer, route, site, delete_ind, create_timestamp, modify_timestamp, loaded_from_file, hx_data_ind  

|Location||
|-----|-----|
| Table Name | Location|
| File Name Pattern | Location|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, location_id, location_name, location_address, location_city, location_state, location_zip, loaded_from_file  

|Medication||
|-----|-----|
| Table Name | Medication|
| File Name Pattern | medication|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: medicationlist_id, center_id, patient_id, originating_enc_id, updated_enc_id, ndc_code, prescribed_elsewhere_ind, start_date, stop_date, date_last_refilled, medication_dictionary, cpoe_ind, delete_ind, create_timestamp, modify_timestamp, loaded_from_file, medication_name, medication_generic_name, order_ind, order_date, created_by, modified_by, location_id, provider_id, dose, route, instructions, status  

|Observation||
|-----|-----|
| Table Name | Observation|
| File Name Pattern | maintenance|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, maintenance_id, patient_id, encounter_id, provider_id, type, description, result, units, ordered_date, completed_date, create_timestamp, delete_ind, result_numeric, modify_timestamp, completed_by, completed_by_provider_id, loaded_from_file, cpt_code, icd9_code, loinc_code, category  

|Orders||
|-----|-----|
| Table Name | Orders|
| File Name Pattern | Order|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, order_id, patient_id, encounter_id, ordering_provider_id, ordered_date, from_location_id, to_location_id, order_name, order_notes, order_priority, order_status, order_type, order_specialty_unscrubbed, cpt_code, icd9_code, icd10_code, sequence_number, result_received_date, reviewing_provider_id, result_reviewed_date, delete_ind, create_timestamp, modify_timestamp, loaded_from_file, created_by, modified_by, cpoe_ind, linked_image_ind  

|Patient||
|-----|-----|
| Table Name | Patient|
| File Name Pattern | patient|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, patient_id, provider_id, first_name, middle_name, last_name, race, ethnicity, language, email, address1, address2, city, county, state, zip, phone, birth_date, death_date, patient_status, create_timestamp, delete_ind, sex, modify_timestamp, MRN, loaded_from_file, guarantor_self_ind, guarantor_id, homelessness_status, migrant_status, veteran_status, ssn, income, family_size, alias, guarantor_relationship, phone2, advance_directive, billing_account__id, usual_location, opt_in_ind, mail_address1, mail_address2, mail_city, mail_state, mail_zip, medicaid_id  

|patient_merge||
|-----|-----|
| Table Name | patient_merge|
| File Name Pattern | patient_merge|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Center_ID, Patient_ID, NPI, Patient_ID_Source, Deleted_Ind, Created_Time, Modified_Time  

|Problem||
|-----|-----|
| Table Name | Problem|
| File Name Pattern | problem|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, problem_id, originating_encounter_id, updated_encounter_id, provider_id, patient_id, problem_status, problem_severity, problem_description, problem_notes, icd9_code, onset_date, resolved_date, create_timestamp, modify_timestamp, created_by, modified_by, delete_ind, loaded_from_file, icd10_code  

|Provider||
|-----|-----|
| Table Name | Provider|
| File Name Pattern | provider|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, provider_id, first_name, last_name, email, address1, address2, city, state, zip, phone, type, national_provider_id, taxonomy_code, create_timestamp, delete_ind, specialty, modify_timestamp, loaded_from_file, middle_name, usual_location, prov_active_ind  

|Result||
|-----|-----|
| Table Name | Result|
| File Name Pattern | result|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, result_id, patient_id, encounter_id, provider_id, parent_result_id, order_id, lab_facility_name, lab_name, lab_description, collection_date, received_date, sign_off_date, sign_off_provider_id, result_type, result_value, result_units, result_min, result_max, result_out_of_range, result_status, result_notes, delete_ind, create_timestamp, modify_timestamp, loaded_from_file, result_from_interface_ind, created_by, modified_by, loinc_code  

|Vitals||
|-----|-----|
| Table Name | Vitals|
| File Name Pattern | Vitals|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: center_id, vitals_id, patient_id, encounter_id, provider_id, vitals_date, create_timestamp, delete_ind, height, weight, bmi, bp_systolic, bp_diastolic, height_units, weight_units, modify_timestamp, loaded_from_file, temperature, temperature_units, temperature_site, heart_rate, spo2, bp_position, bmi_percentile  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Contact the Solution Architect for details.*

* Known Issues and Unvalidated Data Spreadsheet [Click Here](https://arcadia.app.box.com/files/0/f/1888547619/4._Client_Specific_Material)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20URMC%20or%20%22Data%20Source%20Acronym%22%20~%20URMC)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)