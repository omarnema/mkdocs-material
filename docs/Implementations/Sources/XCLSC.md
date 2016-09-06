Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#XCLSC (Excellus Claims)

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
| Data Source Name| **Excellus Claims** |
| Data Source Acronym| **XCLSC** |
| Type | **Claims** |
| Site ID | **2** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|XCLSC_PRESTAGING_PRD|
|User Name|XCLSC_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0030-XCLSC_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|ClaimDetail||
|-----|-----|
| Table Name | ClaimDetail|
| File Name Pattern | ClaimDetail|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_detail_id, claim_header_id, member_id, adjudicated_location_id, rendering_provider_id, code_type, code_value, units, pos, adjustment_code, service_from_date, service_thru_date, claim_status, selfpay_ind, netpayment_amount, billed_amount, deductible_amount, allowed_amount, member_responsibility_amount, copay_amount, coinsurance_amount, invoice_date, Mod1, mod2, mod3, mod4, line_no, revenue_code, not_covered_amount, paid_amount, interest_amount, check_amount, fee_for_service_equivalent_amt, patient_liab_cost_share_amount, final_processing_status, create_timestamp, modify_timestamp  

|ClaimDiagnosis||
|-----|-----|
| Table Name | ClaimDiagnosis|
| File Name Pattern | ClaimDiagnosis|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_diagnosis_id, claim_header_id, diagnosis_code, diagnosis_code_type, poa_ind, line_no, seq_no, admitting_diag_ind, discharge_diag_ind, emergency_diag_ind, create_timestamp, modify_timestamp  

|ClaimHeader||
|-----|-----|
| Table Name | ClaimHeader|
| File Name Pattern | ClaimHeader|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_header_id, member_id, member_elig_id, admitting_provider_id, attending_provider_id, billing_provider_id, member_payment_amount, member_payment_date, submitted_date, service_from_date, service_thru_date, pos, admission_date, discharge_date, drg, drg_type, patient_status, claim_frequency, claim_type, form_type, bill_type, claim_no, claim_status, account_no, admission_hour, admission_source, admission_type, admitting_diagnosis, allowed_amount, check_amount, claim_submission_method, fee_for_service_equivalent_amt, final_claim_ind, first_claim_no, medical_record_no, not_covered_amount, paid_amount, patient_control_no, patient_liab_cost_share_amount, received_date, total_billed_amount, create_timestamp, modify_timestamp  

|ClaimRx||
|-----|-----|
| Table Name | ClaimRx|
| File Name Pattern | ClaimRx|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: claim_rx_id, member_id, nabp_no, rx_no, fill_date, pbm_audit_no, adjustment_status, adjudication_date, refill_no, drug_strength, drug_units, quantity, days_supply, ndc, drug_name, drug_generic_code, drug_product_type_code, generic_ind, dosage_form_code, federal_drug_class_code, formulary_ind, compound_ind, daw_code, paid_date, paid_amount, billed_amount, not_covered_amount, deductible_amount, coinsurance_amount, copay_amount, billing_copay_amount, passed_copay_amount, ancillary_amount, pbm_processing_fee_amount, tax_amount, uc_ind, uc_amount, mac_amount, reimbursement_code, pharmacy_npi, pharmacy_city, pharmacy_state, pharmacy_zip, payee_name, payee_type, submit_type_code, create_timestamp, modify_timestamp  

|Lob||
|-----|-----|
| Table Name | Lob|
| File Name Pattern | Lob|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: lob_id, lob_desc, lob_type, create_timestamp, modify_timestamp  

|Member||
|-----|-----|
| Table Name | Member|
| File Name Pattern | Member.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: member_id, first_name, middle_name, last_name, contract_title, sex, home_phone, business_phone, cell_phone, birth_date, death_date, pregnancy_date, language, risk, ssn, relationship, race, ethnicity, attention, address_type, address_line1, address_line2, city, state, zip, county, country, medicaid_id, medicare_id, historical_indicator, create_timestamp, modify_timestamp  

|MemberElig||
|-----|-----|
| Table Name | MemberElig|
| File Name Pattern | MemberElig|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: member_elig_id, member_id, group_id, product_id, mbr_no, mbr_no_suffix, start_date, end_date, term_code, medicare_a_ind, medicare_b_ind, seq_no, other_coverage_int_ind, other_coverage_ext_ind, premium_amount, pregnancy_ind, subscriber_only_ind, pcp_copay_amt, deductible_amt, drug_coverage_ind, create_timestamp, modify_timestamp  

|MemberID||
|-----|-----|
| Table Name | MemberID|
| File Name Pattern | MemberID|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: SUBR_ID, DEP_NBR, SYST_IND, UNIQ_ID_NEW, UNIQ_ID_OLD, INSERT_DATE, CRTE_RUN_CYCL_EXEC_SK, LAST_UPDT_RUN_CYCL_EXEC_SK, XFER_DATE  

|planGroup||
|-----|-----|
| Table Name | planGroup|
| File Name Pattern | planGroup|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: group_id, group_desc, create_timestamp, modify_timestamp  

|Product||
|-----|-----|
| Table Name | Product|
| File Name Pattern | Product|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: product_id, product_desc, lob_id, create_timestamp, modify_timestamp  

|Provider||
|-----|-----|
| Table Name | Provider|
| File Name Pattern | Provider|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: provider_id, business_phone, fax, first_name, middle_initial, last_name, sex, dob, npi, attention, address_type, address_line1, address_line2, city, state, zip, county, country, dea, primary_specialty, license_no, medicaid_id, provider_type, tax_id, taxonomy, language, create_timestamp, modify_timestamp  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20XCLSC%20or%20%22Data%20Source%20Acronym%22%20~%20XCLSC)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)