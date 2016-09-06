Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#ABHMOI (Alexian Brothers Health Maintenance Organization of Illinois)

**Client(s)**: [AXBRO](../AXBRO.md)  
**Density Area**: Chicago   

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
| Data Source Name| **Alexian Brothers Health Maintenance Organization of Illinois** |
| Data Source Acronym| **ABHMOI** |
| Type | **Claims** |
| Site ID | **1** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|ABHMOI_PRESTAGING_PRD|
|User Name|ABHMOI_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0278-PR-ABHMOI_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|planClaimDetail||
|-----|-----|
| Table Name | planClaimDetail|
| File Name Pattern | planClaimDetail.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_detail_id, claim_header_id, member_id, adjudicated_location_id, Rendering_provider_id, code_type, code_value, Units, pos, adjustment_code, service_from_date, service_thru_date, claim_status, selfpay_ind, netpayment_amount, billed_amount, deductible_amount, allowed_amount, member_responsibility_amount, copay_amount, coinsurance_amount, invoice_date, mod1, mod2, mod3, mod4, line_no, revenue_code, not_covered_amount, paid_amount, interest_amount, check_amount, fee_for_service_equivalent_amt, patient_liab_cost_share_amount, final_processing_status, create_timestamp, modify_timestamp, source_id  

|planClaimDiagnosis||
|-----|-----|
| Table Name | planClaimDiagnosis|
| File Name Pattern | planClaimDiagnosis.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_diagnosis_id, claim_header_id, diagnosis_code, diagnosis_code_type, poa_ind, line_no, seq_no, admitting_diag_ind, discharge_diag_ind, emergency_diag_ind, create_timestamp, modify_timestamp, source_id  

|planClaimHeader||
|-----|-----|
| Table Name | planClaimHeader|
| File Name Pattern | planClaimHeader.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_header_id, member_id, member_elig_id, admitting_provider_id, attending_provider_id, billing_provider_id, member_payment_amount, member_payment_date, submitted_date, service_from_date, service_thru_date, pos, admission_date, discharge_date, drg, drg_type, patient_status, claim_frequency, claim_type, form_type, bill_type, claim_no, claim_status, account_no, admission_hour, admission_source, admission_type, admitting_diagnosis, allowed_amount, check_amount, claim_submission_method, fee_for_service_equivalent_amt, final_claim_ind, first_claim_no, medical_record_no, not_covered_amount, paid_amount, patient_control_no, patient_liab_cost_share_amount, received_date, total_billed_amount, create_timestamp, modify_timestamp, source_id  

|planClaimRX||
|-----|-----|
| Table Name | planClaimRX|
| File Name Pattern | planClaimRX.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_rx_id, member_id, nabp_no, rx_no, fill_date, pbm_audit_no, adjustment_status, adjudication_date, refill_no, drug_strength, drug_units, quantity, days_supply, ndc, drug_name, drug_generic_code, drug_product_type_code, generic_ind, dosage_form_code, federal_drug_class_code, formulary_ind, compound_ind, daw_code, paid_date, paid_amount, billed_amount, not_covered_amount, deductible_amount, coinsurance_amount, copay_amount, billing_copay_amount, passed_copay_amount, ancillary_amount, pbm_processing_fee_amount, tax_amount, uc_ind, uc_amount, mac_amount, reimbursement_code, pharmacy_npi, pharmacy_city, pharmacy_state, pharmacy_zip, payee_name, payee_type, submit_type_code, create_timestamp, moditfy_timestamp, source_id  

|planGroup||
|-----|-----|
| Table Name | planGroup|
| File Name Pattern | planGroup.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: group_id, group_desc, create_timestamp, modify_timestamp, source_id  

|planLOB||
|-----|-----|
| Table Name | planLOB|
| File Name Pattern | planLOB.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: lob_id, lob_desc, lob_type, create_timestamp, modify_timestamp, source_id  

|planLocation||
|-----|-----|
| Table Name | planLocation|
| File Name Pattern | planLocation.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: location_id, location_desc, location_type, start_date, end_date, created_by, modified_by, address_attention, address_type, address_line1, address_line2, city, state, zip, county, country, delete_ind, create_timestamp, modify_timestamp, source_id  

|planMember||
|-----|-----|
| Table Name | planMember|
| File Name Pattern | planMember.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: member_id, first_name, middle_name, last_name, contact_title, Sex, home_phone, business_phone, cell_phone, birth_date, death_date, pregnancy_date, language, Risk, Ssn, Relationship, Race, Ethnicity, Attention, address_type, address_line1, address_line2, City, state, zip, county, country, medicaid_id, medicare_id, historical_indicator, create_timestamp, modify_timestamp, source_id  

|planMemberAssign||
|-----|-----|
| Table Name | planMemberAssign|
| File Name Pattern | planMemberAssign.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: member_assignment_id, member_id, provider_id, location_id, site_id, start_date, end_date, assignment_type, Cap_amount, created_by, modified_by, create_timestamp, modify_timestamp, source_id  

|planMemberElig||
|-----|-----|
| Table Name | planMemberElig|
| File Name Pattern | planMemberElig.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: member_elig_id, member_id, group_id, product_id, mbr_no, mbr_no_suffix, start_date, end_date, term_code, medicare_a_ind, medicare_b_ind, seq_no, other_coverage_int_ind, other_coverage_ext_ind, premium_amount, pregnancy_ind, subscriber_only_ind, pcp_copay_amount, deductible_amount, drug_coverage_ind, create_timestamp, modify_timestamp, source_id  

|planProduct||
|-----|-----|
| Table Name | planProduct|
| File Name Pattern | planProduct.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: product_id, product_desc, lob_id, create_timestamp, modify_timestamp, source_id  

|planProvider||
|-----|-----|
| Table Name | planProvider|
| File Name Pattern | planProvider.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: provider_id, business_phone, fax, full_name, first_name, middle_initial, last_name, sex, dob, npi, attention, address_type, address_line1, address_line2, city, state, zip, county, country, dea, primary_specialty, license_no, medicaid_id, provider_type, tax_id, taxonomy, language, create_timestamp, modify_timestamp, source_id  

|planSite||
|-----|-----|
| Table Name | planSite|
| File Name Pattern | planSite.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: site_id, site_desc, site_type, start_date, end_date, create_timestamp, modify_timestamp, created_by, modified_by, address_attention, address_type, address_line1, address_line2, city, state, zip, county, country, delete_ind, source_id  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20ABHMOI%20or%20%22Data%20Source%20Acronym%22%20~%20ABHMOI)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)