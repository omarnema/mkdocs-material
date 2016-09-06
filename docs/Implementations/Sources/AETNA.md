Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#AETNA (Aetna Inc.)

**Client(s)**: [VCA](../VCA.md)  
**Density Area**: Northeast   

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture

Notes on addition of [eACO](./VAETEACO.md) and JV products into this feed [here](./Aetna-JV-and-eACO-Requirements.md)  


| Overview ||
|-----|-----|
| Data Source Name| **Aetna Inc.** |
| Data Source Acronym| **AETNA** |
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
|Name|AETNA_PRESTAGING_PRD|
|User Name|AETNA_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0100-PR-AETNA_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Claim||
|-----|-----|
| Table Name | Claim|
| File Name Pattern | AET*CLAIM*.txt|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: ps_unique_id, customer_nbr, group_nbr, idn_indicator, subgroup_nbr, account_nbr, file_id, clm_ln_type_cd, non_prfrrd_srv_cd, plsp_prod_cd, product_ln_cd, classification_cd, bnft_pkg_id, plan_id, benefit_tier, fund_ctg_cd, src_subscriber_id, emp_last_nm, emp_first_nm, emp_gender, subscriber_brth_dt, subs_zip_cd, subs_st_postal_cd, coverage_type_cd, ssn_nbr, member_id, member_number, mem_last_nm, mem_first_nm, mem_gender, mbr_rtp_type_cd, birth_dt, src_clm_id, acas_generation_segment_number, prev_clm_seg_id, derived_tcn_nbr, expense_pay_line_number, claim_line_id, ntwk_srv_area_id, paid_prvdr_nsa_id, srv_capacity_cd, pcp_tax_id_format_cd, pcp_tax_id_nbr, pcp_print_nm, srv_prvdr_tax_id_format_cd, srv_prvdr_tax_id_nbr, srv_prvdr_id, srv_prvdr_print_nm, srv_prvdr_address_line_1_txt, srv_prvdr_address_line_2_txt, srv_prvdr_city_nm, srv_prvdr_state_postal_cd, srv_prvdr_zip_cd, srv_prvdr_provider_type_cd, srv_prvdr_specialty_cd, payee_cd, paid_prvdr_par_cd, received_dt, adjn_dt, srv_start_dt, srv_stop_dt, date_processed, filler_one, filler_two, filler_three, mdc_cd, drg_cd, prcdr_cd, prcdr_modifier_cd1, prcdr_type_cd, ICD10_Indicator, MED_COST_SUBCTG_CD, filler_four, type_srv_cd, srv_benefit_cd, tooth_1_nbr, plc_srv_cd, dschrg_status_cd, revenue_cd, hcfa_bill_type_cd, unit_cnt, src_unit_cnt, src_billed_amt, billed_amt, not_covered_amt_1, not_covered_amt_2, not_covered_amt_3, clm_ln_msg_cd_1, clm_ln_msg_cd_2, clm_ln_msg_cd_3, covered_amt, allowed_amt, filler_five, srv_copay_amt, src_srv_copay_amt, deductible_amt, coinsurance_amt, src_coins_amt, bnft_payable_amt, paid_amt, cob_paid_amt, ahf_bfd_amt, ahf_paid_amt, negot_savings_amt, r_c_savings_amt, cob_savings_amt, src_cob_svngs_amt, pri_payer_cvg_cd, cob_type_cd, cob_cd, prcdr_cd_ndc, member_cumbid, clm_ln_status_cd, src_member_id, reversal_cd, admit_cnt, admin_savings_amt, adj_prvdr_dsgnn_cd, aex_plan_dsgntn_cd, benefit_tier_cd, aex_prvdr_spctg_cd, prod_distnctn_cd, billed_eligible_amt, srv_provider_class_cd, poa_cd_1, poa_cd_2, poa_cd_3, filler_six, filler_seven, filler_eight, pricing_mthd_cd, type_class_cd, specialty_ctg_cd, srv_prvdr_npi, ttl_ded_met_ind, ttl_interest_amt, ttl_surcharge_amt, SRV_SPCLTY_CTG_CD, HCFA_PLC_SRV_CD, HCFA_ADMIT_SRC_CD, HCFA_ADMIT_TYPE_CD, SRC_ADMIT_DT, SRC_DISCHARGE_DT, prcdr_modifier_cd2, prcdr_modifier_cd3, poa_cd_4, poa_cd_5, poa_cd_6, poa_cd_7, poa_cd_8, poa_cd_9, poa_cd_10, pri_icd9_dx_cd, icd9_dx_cd_2, icd9_dx_cd_3, icd9_dx_cd_4, icd9_dx_cd_5, icd9_dx_cd_6, icd9_dx_cd_7, icd9_dx_cd_8, icd9_dx_cd_9, icd9_dx_cd_10, icd9_prcdr_cd_1, icd9_prcdr_cd_2, icd9_prcdr_cd_3, icd9_prcdr_cd_4, icd9_prcdr_cd_5, icd9_prcdr_cd_6, ahf_det_order_cd, ahf_mbr_coins_amt, ahf_mbr_copay_amt, ahf_mbr_ded_amt, admission_type, filler_nine, ORG_CD, EOR  

|Enrollment||
|-----|-----|
| Table Name | Enrollment|
| File Name Pattern | AET*COE*.txt|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: member_id, effective_month, MSK_PREFIX_NM, member_last_nm, member_first_nm, member_SUFFIX_NM, member_mbr_gender_cd, member_birth_dt, member_ADDRESS_LINE_1_TXT, member_ADDRESS_LINE_2_TXT, member_CITY_NM, member_STATE_POSTAL_CD, member_COUNTY_CD, member_ZIP_CD, member_phone, member_SRC_MEMBER_ID, member_MBR_RTP_TYPE_CD, member_SSN_NBR, ps_unique_id, customer_nbr, group_nbr, subgroup_nbr, account_nbr, employee_last_nm, employee_first_nm, employee_gender_cd, employee_subscriber_brth_dt, employee_subs_zip_cd, employee_subs_st_postal_cd, employee_COUNTY_CD, employee_SSN_NBR, file_id, plsp_prod_cd, product_ln_cd, fund_ctg_cd, COVERAGE_TYPE_CD, NTWK_SRV_AREA_ID, CUST_SUBSEG_CD, MEDICAL_IND, DRUG_IND, SBSTNC_ABUSE_IND, MENTAL_HEALTH_IND, ORIG_COVG_EFF_DT, pcp_tax_id_nbr, pcp_prvdr_id, pcp_print_nm, pcp_address_line_1_txt, pcp_address_line_2_txt, pcp_city_nm, pcp_state_postal_cd, pcp_zip_cd, pcp_npi_nbr, pcp_SPECIALTY_CTG_CD, pcp_ORG_ID, FIRST_VST_DT, LAST_VST_DT, VISIT_NBR, attr_prvd_tax_id_nbr, attr_prvdr_id, attr_prvd_print_nm, attr_prvd_address_line_1_txt, attr_prvd_address_line_2_txt, attr_prvd_city_nm, attr_prvd_state_postal_cd, attr_prvd_zip_cd, attr_prvd_npi_nbr, attr_prvd_SPECIALTY_CTG_CD, STATUS_IND, eff_dt, cncl_dt, member_SRC_CUMB_ID, employee_SRC_CUMB_ID, middle_nm, individual_id, pulse_fsi_score, ERG_Prospective_Score, ERG_Retro_Score, business_ln_cd, Aetna_card_id, grp_cntl_name, current_record_ind, cumb_id_seq_no, ORG_ID, EOR  

|Lab||
|-----|-----|
| Table Name | Lab|
| File Name Pattern | AET*LABD*.txt|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: ps_unique_id, customer_nbr, group_nbr, filler, subgroup_nbr, account_nbr, product_ln_cd, plan_id, fund_ctg_cd, ee_id, ee_last_name, ee_first_name, subs_zip_cd, ssn_nbr, member_id, src_member_id, last_name, first_name, src_mbr_gender_cd, MBR_RTP_TYPE_CD, src_mbr_birth_dt, loinc_cd, loinc_description, procedure_cd, lab_test_nm, lab_result_txt, lab_abn_text, lab_low_range, lab_high_range, lab_nrml_rslt_rng, collection_dt, fasting_ind, srv_start_dt, lab_units_txt, lab_prvdr_id, lab_prvdr_tax_id_nbr, lab_prvdr_npi_nbr, lab_prvdr_print_nm, lab_prvdr_address_line_1_txt, lab_prvdr_address_line_2_txt, lab_prvdr_city_nm, lab_prvdr_state_postal_cd, lab_prvdr_zip_cd, Ordering_prvdr_ID, ordering_prvdr_tax_id_nbr, ordering_prvdr_npi_nbr, ordering_prvdr_print_nm, ordering_prvdr_address_line_1_txt, ordering_prvdr_address_line_2_txt, ordering_prvdr_city_nm, ordering_prvdr_state_postal_cd, ordering_prvdr_zip_cd, ORG_CD, EOR  

|Rx||
|-----|-----|
| Table Name | Rx|
| File Name Pattern | AET*DRUG*.txt|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: ps_unique_id, customer_nbr, group_nbr, file_source, subgroup_nbr, account_nbr, product_ln_cd, rx_product_cd, plan_id, fund_ctg_cd, option_cd, rx_intgrtn_opt_cd, ee_id, ee_last_name, ee_first_name, subs_zip_cd, ssn_nbr, member_id, src_rx_member_id, last_name, first_name, src_mbr_gender_cd, mbr_rtp_type_cd, src_mbr_birth_dt, filler_one, filler_two, clm_status, dir_mbr_reim_ind, ee_ntwk_srv_area_id, office_id, sort_name, prescriber_id, spclty_ctg_cd, address_line_1, address_line_2, nabp_nbr, phm_zip_cd, process_dt, disp_dt, ndc_cd, label_nm, formulary_cd, generic_cd, source_type_cd, retail_mod_cd, new_refill_cnt, daw_cd, unts_dispensed_qty, days_supply_cnt, sub_ing_cost_amt, prof_fee_amt, awp_amt, sales_tax_amt, app_to_per_ded_amt, srv_copay_amt, paid_amt, ahf_paid_amt, ahf_bfd_amt, GPI_1st_10_bytes, phi_acas_bypass_cd, price_type_cd, calc_ing_cost_amt, prescbr_id_qlfy_cd, prod_distnctn_cd, rx_claim_id, compound_cd, maint_drug_cd, prescription_nbr, nabp_provider_name, prescribing_provider_name, record_status, ORG_CD, EOR  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20AETNA%20or%20%22Data%20Source%20Acronym%22%20~%20AETNA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)