Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-07-25
ModifyDate: 2016-07-25


#BITUFTS (BIDCO Tufts Commercial Claims)

**Client(s)**: [BIDCO](../BIDCO.md)  
**Density Area**: Northeast   

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
| Data Source Name| **BIDCO Tufts Commercial Claims** |
| Data Source Acronym| **BITUFTS** |
| Type | **Claims** |
| Site ID | **80** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|BITUFTS_PRESTAGING_PRD|
|User Name|BITUFTS_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

No regular process has been established for file delivery, and the client has not yet agreed to send the files through the standard mechanism (unzipped, PGP-encrypted files sent through SFTP).   We received an initial set of files that were packages into multi-level self-extracting executables. 

Ongoing conversations need to happen to address the following concerns: 

* Self-extracting executables. No standard process for extracting them, and could potentially be a security risk to run unknown executables. Tufts' documentation says they can be delivered in ZIPs, which is more workable. 
* Non-unique naming conventions: there can be overlappping file names once the exe's are unpacked. To get around this, the strategy has been to prepend the date stamp in the executable name to the file name. 

These have been escalated but not resolved. 

Some files also contain trailer records, and some file name matching requires regex.

**NOTE**: This file feed contains data for both commercial (BITUFTS) and Medicare Advantage ([BITMPMA](./BITMPMA.md)) feeds, so the prestaging load covers both connecors. However the connector query development and connector testing are being tracked separately in Jira. 

##Data Source

Flat file feed [specifications](https://arcadia.box.com/s/7dsyx1eqrrcwcmjuzokzqw4jy1qofypp).

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0538-PR-BITUFTS_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Acturial||
|-----|-----|
| Table Name | Acturial|
| File Name Patterne | _erda0013|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: ACTUARIAL_CODE(4),ACTUARIAL_DESC(30)  

|DIAGNOSIS||
|-----|-----|
| Table Name | DIAGNOSIS|
| File Name Patterne | _erda0015|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: DIAG_CODE(8),DIAG_DESC(60),ICD_VERSION(1)  

|DRG_CODES||
|-----|-----|
| Table Name | DRG_CODES|
| File Name Patterne | _erda00(31|33)|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: BUSINESS_LINE_KEY(4),PROVIDER_UNIT(2),DRG_CODE(6),TOS_CODE(3),PROVIDER_IPA(2),PROVIDER_ID(6),PCP_ID(6),AGE_GENDER_GROUP(3),MEMBER_ID(14),DATE_OF_SERVICE(8),ADMISSION_DATE(8),DISCHARGE_DATE(8),DAYS(5),DISCHARGE_STATUS(2),DIAG1_DESC(60),DIAG1_CODE(8),DIAG2_CODE(8),DIAG3_CODE(8),DIAG4_CODE(8),DIAG5_CODE(8),DIAG6_CODE(8),DIAG7_CODE(8),ICD_PROC1_CODE(8),ICD_PROC2_CODE(8),ICD_PROC3_CODE(8),ICD_PROC4_CODE(8),ICD_PROC5_CODE(8),FUND_CODE(4),HOSP_PROV_ID_NPI(10),PCP_ID_NPI(10),CLAIM_NUMBER(8),CLAIM_LINE(2),TYPE_OF_BILL(4),Prim_POA(2),Scnd_POA(2),Form_Type(2),PROC_MOD1(2),PROC_MOD2(2),PROC_MOD3(2),PROC_MOD4(2),REVENUE_CODE(4),DIAG_POINTER1(5),DIAG_POINTER2(5),DIAG_POINTER3(5),DIAG_POINTER4(5),RAW_POS_CODE(2),DIAG8_CODE(8),DIAG9_CODE(8),DIAG10_CODE(8),DIAG11_CODE(8),DIAG12_CODE(8),DIAG13_CODE(8),DIAG14_CODE(8),DIAG15_CODE(8),DIAG16_CODE(8),DIAG17_CODE(8),DIAG18_CODE(8),DIAG19_CODE(8),DIAG20_CODE(8),DIAG21_CODE(8),DIAG22_CODE(8),DIAG23_CODE(8),DIAG24_CODE(8),PRIN_PROC_CODE(8),OTHER_PROC1_CODE(8),OTHER_PROC2_CODE(8),OTHER_PROC3_CODE(8),OTHER_PROC4_CODE(8),OTHER_PROC5_CODE(8),OTHER_PROC6_CODE(8),OTHER_PROC7_CODE(8),OTHER_PROC8_CODE(8),OTHER_PROC9_CODE(8),OTHER_PROC10_CODE(8),OTHER_PROC11_CODE(8),OTHER_PROC12_CODE(8),OTHER_PROC13_CODE(8),OTHER_PROC14_CODE(8),OTHER_PROC15_CODE(8),OTHER_PROC16_CODE(8),OTHER_PROC17_CODE(8),OTHER_PROC18_CODE(8),OTHER_PROC19_CODE(8),OTHER_PROC20_CODE(8),OTHER_PROC21_CODE(8),OTHER_PROC22_CODE(8),OTHER_PROC23_CODE(8),RISK_OF_MORTALITY(2),DRG_GROUPER(2),DRG_GROUPER_VERSION_NUMBER(2),ICD_VERSION(1)  

|DRG_REFERENCE||
|-----|-----|
| Table Name | DRG_REFERENCE|
| File Name Patterne | _DRGreference|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: DRG_GROUPER(2),DRG_VERSION_NUMBER(2),DRG_CODE(6),DRG_DESCRIPTION(40)  

|ELIGIBILITY||
|-----|-----|
| Table Name | ELIGIBILITY|
| File Name Patterne | _erda00(22|53)|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MISC1(9),RELATIONSHIP_CODE(2),MISC2(1),FIRST_NAME(13),MIDDLE_INITIAL(1),LAST_NAME(20),DOB(8),AGE(3),GENDER_CODE(1),MISC3(1),STATUS(1),EFFECTIVE_DATE(8),PRODUCT(6),GROUP_NUMBER(8),PLAN_CODE(10),IPA(2),MISC4(1),PCP_NAME(30),MEMBER_ADDRESS_1(30),CITY(30),STATE(2),ZIP_CODE(10),PHONE(10),END_DATE(8),MISC5(28),TAPE_DATE(8),PCP_ID(6),MEMBER_ID(14),MEMBER_ADDRESS_2(30),BUSINESS_LINE_KEY(4),PCP_ID_NPI(10),MISC6(1)  

|Medical||
|-----|-----|
| Table Name | Medical|
| File Name Patterne | _erda0011|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: ACTUAL_COST(11),ACTUARIAL_CODE(4),ADJ_CODE(2),ADM_REF_ID(6),ADMISSION_DATE(8),AMT_ALLOWED(11),AMT_ALLOWED2(11),AMT_COPAY2(11),AMT_PAID(11),AMT_COPAY(11),AMT_DEDUCTIBLE(11),AMT_COINSURANCE(11),CLAIM_TYPE(2),TAX_ID(12),BUSINESS_LINE_KEY(4),CLAIM_NUMBER(8),DISCHARGE_DATE(8),DATE_OF_SERVICE(8),FUND_CODE(4),PROVIDER_ID(6),PROVIDER_UNIT(2),PROVIDER_IPA(2),IPA_SUBSIDIARY(6),DOB(8),GENDER(2),MEMBER_ID(14),PAID_DATE(8),PAYEE_ID(6),PCP_ID(6),POS_CODE(2),PRIMARY_DIAGNOSIS(8),PROCEDURE_CODE(8),PRODUCT(6),PROVIDER_CATEGORY(2),REFERRAL_NUMBER(8),SECOND_DIAGNOSIS(8),TOS_CODE(4),UNITS_NOT_DENIED(6),PROCEDURE_MODIFIER(2),CAPITATION_FLAG(2),SERVICE_PROVIDER(3),AMOUNT_BILLED(11),MESSAGE_CODE(2),PAID_IP_FLAG(2),PATIENT_ACCT(12),SECOND_DIAGNOSIS_2(8),SECOND_DIAGNOSIS_3(8),SECOND_DIAGNOSIS_4(8),SECOND_DIAGNOSIS_5(8),SECOND_DIAGNOSIS_6(8),SECOND_DIAGNOSIS_7(8),PRIMARY_PROV_IPA(2),CLAIM_SUF_LINE(4),LAST_VERSION(2),ADM_REF_ID_NPI(10),HOSP_PROV_ID_NPI(10),PAYEE_ID_NPI(10),PCP_ID_NPI(10),AMT_RETENTION(11),TYPE_OF_BILL(4),FORM_TYPE(2),PROC_MOD1(2),PROC_MOD2(2),PROC_MOD3(2),PROC_MOD4(2),REVENUE_CODE(4),DIAG_POINTER1(5),DIAG_POINTER2(5),DIAG_POINTER3(5),DIAG_POINTER4(5),RAW_POS_CODE(2),SECOND_DIAGNOSIS_8(8),SECOND_DIAGNOSIS_9(8),SECOND_DIAGNOSIS_10(8),SECOND_DIAGNOSIS_11(8),SECOND_DIAGNOSIS_12(8),SECOND_DIAGNOSIS_13(8),SECOND_DIAGNOSIS_14(8),SECOND_DIAGNOSIS_15(8),SECOND_DIAGNOSIS_16(8),SECOND_DIAGNOSIS_17(8),SECOND_DIAGNOSIS_18(8),SECOND_DIAGNOSIS_19(8),SECOND_DIAGNOSIS_20(8),SECOND_DIAGNOSIS_21(8),SECOND_DIAGNOSIS_22(8),SECOND_DIAGNOSIS_23(8),SECOND_DIAGNOSIS_24(8),ICD_VERSION(2),MISC1(1),MISC2(8)  

|MEDICAL_CLAIMS||
|-----|-----|
| Table Name | MEDICAL_CLAIMS|
| File Name Patterne | _erda0011|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: ACTUAL_COST(11),ACTUARIAL_CODE(4),ADJ_CODE(2),ADM_REF_ID(6),ADMISSION_DATE(8),AMT_ALLOWED(11),AMT_ALLOWED2(11),AMT_COPAY2(11),AMT_PAID(11),AMT_COPAY(11),AMT_DEDUCTIBLE(11),AMT_COINSURANCE(11),CLAIM_TYPE(2),TAX_ID(12),BUSINESS_LINE_KEY(4),CLAIM_NUMBER(8),DISCHARGE_DATE(8),DATE_OF_SERVICE(8),FUND_CODE(4),PROVIDER_ID(6),PROVIDER_UNIT(2),PROVIDER_IPA(2),IPA_SUBSIDIARY(6),DOB(8),GENDER(2),MEMBER_ID(14),PAID_DATE(8),PAYEE_ID(6),PCP_ID(6),POS_CODE(2),PRIMARY_DIAGNOSIS(8),PROCEDURE_CODE(8),PRODUCT(6),PROVIDER_CATEGORY(2),REFERRAL_NUMBER(8),SECOND_DIAGNOSIS(8),TOS_CODE(4),UNITS_NOT_DENIED(6),PROCEDURE_MODIFIER(2),CAPITATION_FLAG(2),SERVICE_PROVIDER(3),AMOUNT_BILLED(11),MESSAGE_CODE(2),PAID_IP_FLAG(2),PATIENT_ACCT(12),SECOND_DIAGNOSIS_2(8),SECOND_DIAGNOSIS_3(8),SECOND_DIAGNOSIS_4(8),SECOND_DIAGNOSIS_5(8),SECOND_DIAGNOSIS_6(8),SECOND_DIAGNOSIS_7(8),PRIMARY_PROV_IPA(2),CLAIM_SUF_LINE(4),LAST_VERSION(2),ADM_REF_ID_NPI(10),HOSP_PROV_ID_NPI(10),PAYEE_ID_NPI(10),PCP_ID_NPI(10),AMT_RETENTION(11),TYPE_OF_BILL(4),FORM_TYPE(2),PROC_MOD1(2),PROC_MOD2(2),PROC_MOD3(2),PROC_MOD4(2),REVENUE_CODE(4),DIAG_POINTER1(5),DIAG_POINTER2(5),DIAG_POINTER3(5),DIAG_POINTER4(5),RAW_POS_CODE(2),SECOND_DIAGNOSIS_8(8),SECOND_DIAGNOSIS_9(8),SECOND_DIAGNOSIS_10(8),SECOND_DIAGNOSIS_11(8),SECOND_DIAGNOSIS_12(8),SECOND_DIAGNOSIS_13(8),SECOND_DIAGNOSIS_14(8),SECOND_DIAGNOSIS_15(8),SECOND_DIAGNOSIS_16(8),SECOND_DIAGNOSIS_17(8),SECOND_DIAGNOSIS_18(8),SECOND_DIAGNOSIS_19(8),SECOND_DIAGNOSIS_20(8),SECOND_DIAGNOSIS_21(8),SECOND_DIAGNOSIS_22(8),SECOND_DIAGNOSIS_23(8),SECOND_DIAGNOSIS_24(8),ICD_VERSION(2),MISC1(1),MISC2(8)  

|MEDICARE_CLAIMS||
|-----|-----|
| Table Name | MEDICARE_CLAIMS|
| File Name Patterne | _shcl|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: SUBSCRIBER_NUMBER(9),PERSON_NUMBER(2),MEDICAL_GROUP(3),PCP_ID(6),PROVIDER_ID(6),VENDOR_ID(10),ADMIT_REF_ID(6),PLACE_OF_SERVICE(5),DIAGNOSIS_CODE_1(8),CLAIM_DATE(8),CLAIM_NUMBER(12),CLAIM_LINE_NUMBER(3),SUB_LINE_NUMBER(1),CLAIM_STATUS(1),MEDICAL_DEF_CODE(4),SERVICE_DATE(8),QUANTITY(6),PROCEDURE_CODE(8),MODIFIER(2),NET_AMOUNT(11),RISK_TYPE(2),REFERRAL_NUMBER(8),POST_DATE(8),UNITS_SUBCAP(6),UNITS_CAP(6),ACTUAL_COST_FFS(11),NET_AMOUNT_CAP(11),NET_AMOUNT_SUBCAP(11),DRG_CODE(3),PCP_PROVIDER_FLAG(1),UNITS_FFS(6),AMOUNT_BILLED(11),DIAGNOSIS_CODE_2(8),DIAGNOSIS_CODE_3(8),DIAGNOSIS_CODE_4(8),DIAGNOSIS_CODE_5(8),AMOUNT_ALLOWED(11),AMOUNT_COPAY(11),AMOUNT_WITHHELD(11),ADMIT_DATE(8),DISCHARGE_DATE(8),PROV_MED_GROUP(3),MESSAGE_CODE(5),PAT_ACCT(20),PROC_1(8),PROC_1_DESC(60),PROC_2(8),PROC_3(8),PROC_4(8),PROC_5(8),Provider_Par_Flag(1),AMOUNT_DEDUCTIBLE(11),AMOUNT_OTHER_CARRIER(11),OTHER_CARRIER_REASON(5),DIAGNOSIS_CODE_6(8),DIAGNOSIS_CODE_7(8),DIAGNOSIS_CODE_8(8),DIAGNOSIS_CODE_9(8),PRESENT_ON_ADMISSION_1(1),PRESENT_ON_ADMISSION_2(1),PRESENT_ON_ADMISSION_3(1),PRESENT_ON_ADMISSION_4(1),PRESENT_ON_ADMISSION_5(1),PRESENT_ON_ADMISSION_6(1),PRESENT_ON_ADMISSION_7(1),PRESENT_ON_ADMISSION_8(1),PRESENT_ON_ADMISSION_9(1),MODIFIER_2(2),MODIFIER_3(2),DISPOSITION_CODE(2),NOT_COVERED_AMOUNT(11),FILLER(1),DIAGNOSIS_CODE_10(8),DIAGNOSIS_CODE_11(8),DIAGNOSIS_CODE_12(8),DIAGNOSIS_CODE_13(8),DIAGNOSIS_CODE_14(8),DIAGNOSIS_CODE_15(8),DIAGNOSIS_CODE_16(8),DIAGNOSIS_CODE_17(8),DIAGNOSIS_CODE_18(8),DIAGNOSIS_CODE_19(8),DIAGNOSIS_CODE_20(8),DIAGNOSIS_CODE_21(8),DIAGNOSIS_CODE_22(8),DIAGNOSIS_CODE_23(8),DIAGNOSIS_CODE_24(8),DIAGNOSIS_CODE_25(8),PRESENT_ON_ADMISSION_10(1),PRESENT_ON_ADMISSION_11(1),PRESENT_ON_ADMISSION_12(1),PRESENT_ON_ADMISSION_13(1),PRESENT_ON_ADMISSION_14(1),PRESENT_ON_ADMISSION_15(1),PRESENT_ON_ADMISSION_16(1),PRESENT_ON_ADMISSION_17(1),PRESENT_ON_ADMISSION_18(1),PRESENT_ON_ADMISSION_19(1),PRESENT_ON_ADMISSION_20(1),PRESENT_ON_ADMISSION_21(1),PRESENT_ON_ADMISSION_22(1),PRESENT_ON_ADMISSION_23(1),PRESENT_ON_ADMISSION_24(1),PRESENT_ON_ADMISSION_25(1),ICD_VERSION(1)  

|MEDICARE_DEF||
|-----|-----|
| Table Name | MEDICARE_DEF|
| File Name Patterne | _meddef|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: MED_DEF_CODE  

|MEDICARE_DIAGNOSIS||
|-----|-----|
| Table Name | MEDICARE_DIAGNOSIS|
| File Name Patterne | _diag|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: DIAG_CODE(8),DIAG_DESC(60),ICD_VERSION(1)  

|MEDICARE_ELIGIBILITY||
|-----|-----|
| Table Name | MEDICARE_ELIGIBILITY|
| File Name Patterne | _shel|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: SUBSCRIBER_NUMBER(9),PERSON_NUMBER(2),CURRENT_PATIENT_INDICATOR(1),FIRST_NAME(12),MIDDLE_INITIAL(1),LAST_NAME(20),DATE_OF_BIRTH(8),AGE(3),SEX(1),SPECIAL_STATUS(1),STATUS(1),EFFECTIVE_DATE(8),LINE_OF_BUSINESS(3),GROUP(8),PLAN_CODE(10),MEDICAL_GROUP(3),PCP_NAME(30),MEMBER_STREET_ADDRESS(30),MEMBER_CITY(30),MEMBER_STATE(2),MEMBER_ZIP_CODE(10),MEMBER_HOME_PHONE(10),TERMINATION_DATE(8),TERMINATION_REASON(35),AS_OF_DATE(8),WORKING_AGED_FLAG(1),PCP_ID(6),RIDER(6),PBP_CODE(3),SEGMENT_ID(3),PCP_NPI(10),GROUP_NAME(27)  

|MEDICARE_MEMBER_MONTH||
|-----|-----|
| Table Name | MEDICARE_MEMBER_MONTH|
| File Name Patterne | _shmm|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MEDICAL_GROUP(3),YEAR_MONTH(6),PCP_ID(6),SUBSCRIBER_NUMBER(9),AGE_GENDER_GROUP(3),COUNTY_CODE(5),MEM_GROUP_NUMBER(8),PLAN(10),MEMBER_MONTH(2),RIDER(6),PBP_CODE(3),SEGMENT_ID(3),PCP_NPI(10)  

|MEDICARE_MODIFIER||
|-----|-----|
| Table Name | MEDICARE_MODIFIER|
| File Name Patterne | _modif|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: MOD_NO_DESC  

|MEDICARE_PHARMACY||
|-----|-----|
| Table Name | MEDICARE_PHARMACY|
| File Name Patterne | _shrx|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: DATE_OF_FILL(8),PAID_DATE(8),PROVIDER_UNIT(3),PCP_ID(6),SUBSCRIBER_ID(14),AGE_GENDER_GROUP(3),DRUG_USC_CODE(6),DOCUMENT_NUMBER(16),DEA_NUMBER(10),ADMIN_FEE_CHARGED(11),AMOUNT_PAID(11),NDC(12),DRUG_NAME(28),DRUG_STRENGTH(6),PRESCRIPTION_QNTY(6),PRESCR_DAYS_SUPPLY(4),FORMULARY_CODE(1),DAW_IND(1),GENERIC_BRAND_IND(1),MS_SOURCE_IND(1),DRUG_DOSAGE_FORM(2),NEW_REFILL_IND(2),PHARMACY_NUMBER(6),MEMBER_EXPENDITURE(11),CLAIM_TYPE_IND(2),STANDARD_COPAY(11),BUSINESS_LINE_KEY(4),PCP_NPI(10),PHARMACY_NPI(10),PRESCRIBER_NPI(10),FUND_CODE(2),MEDICARE_MANDATED_FLAG(2),MISC1(10),GENERIC_PRODUCT_INDICATOR(14),DOCUMENT_SEQ_NO(3),RECORD_STATUS_CODE(1),AMT_ALLOWED(11),ACTUAL_COST(11),THER_CLASS(4),THER_CLASS_DESC(40),E_PRESCRIB_IND(4)  

|MEDICARE_PROCEDURE_CODE||
|-----|-----|
| Table Name | MEDICARE_PROCEDURE_CODE|
| File Name Patterne | _proc|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: PROC_CD_DESC  

|MEDICARE_PROVIDER||
|-----|-----|
| Table Name | MEDICARE_PROVIDER|
| File Name Patterne | _shpro|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: PROVIDER_ID(6),PROVIDER_NAME(30),PROVIDER_TYPE(4),PROVIDER_TYPE_DESC(60),SPECIALTY_CODE_1(4),SPECIALTY_DESC_1(60),SPECIALTY_CODE_2(4),SPECIALTY_DESC_2(60),NPI_NUMBER(10)  

|MEDICARE_SUBSCRIBER||
|-----|-----|
| Table Name | MEDICARE_SUBSCRIBER|
| File Name Patterne | _shmem|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: SUBSCRIBER_NUMBER(9),RELATIONSHIP_CODE(2),LAST_NAME(20),FIRST_NAME(12),MIDDLE_INITIAL(1),ZIP_CODE(10),DOB(8),GENDER(1)  

|MEDICARE_VENDOR||
|-----|-----|
| Table Name | MEDICARE_VENDOR|
| File Name Patterne | _shven|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: VENDOR_DESC  

|MEMBER_MONTH||
|-----|-----|
| Table Name | MEMBER_MONTH|
| File Name Patterne | _erda(0032|2232)|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MM_DATE(6),BUSINESS_LINE_KEY(4),IPA(2),PROVIDER_ID(6),MEMBER_ID(14),RX_RIDER(1),AGE_GENDER_GROUP(3),MEM_COUNT(1),PROV_NPI(10),FILLER(25)  

|MEMBER_MONTH_SUPPORT||
|-----|-----|
| Table Name | MEMBER_MONTH_SUPPORT|
| File Name Patterne | _erda(0034|2233)|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MEMBER_ID(14),MEM_FIRST_NAME(14),MEM_LAST_NAME(20),ZIP_CODE(10),DOB(8),IPA(2)  

|MEMBER_SUPPORT||
|-----|-----|
| Table Name | MEMBER_SUPPORT|
| File Name Patterne | _erda0020|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MEM_ID(14),MEM_FIRST_NAME(14),MEM_LAST_NAME(20),ADDR_ZIP(10),DOB(8),IPA(2)  

|PHARMACY||
|-----|-----|
| Table Name | PHARMACY|
| File Name Patterne | _rxda0111|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: DATE_OF_FILL(8),PAID_DATE(8),IPA(2),PCP_ID(6),MEMBER_ID(14),AGE_GENDER_GROUP(3),DRUG_USC_CODE(6),DOCUMENT_NUMBER(16),DEA_NUMBER(10),ADMIN_FEE_CHARGED(11),AMOUNT_PAID(11),NDC(12),DRUG_NAME(28),DRUG_STRENGTH(6),PRESCRIPTION_QNTY(6),PRESCR_DAYS_SUPPLY(4),FORMULARY_CODE(1),DAW_IND(1),GENERIC_BRAND_IND(1),MS_SOURCE_IND(1),DRUG_DOSAGE_FORM(2),NEW_REFILL_IND(2),PHARMACY_NUMBER(6),MEMBER_EXPENDITURE(11),CLAIM_TYPE_IND(2),STANDARD_COPAY(11),BUSINESS_LINE_KEY(4),GROSS_RECOVERY(16),PCP_NPI(10),PHARMACY_NPI(10),PRESCRIBER_NPI(10),MISC1(14),Generic_Product_Identifier(14),Document_Seq_No(3),Record_Status_CD(1),Fund_Code(3),Ther_Class(20),Ther_Class_Desc(40),Amt_Allowed(11),Actual_Cost(11),MISC2(8),E_PRESCRIB_IND(4)  

|PLACE_OF_SVC||
|-----|-----|
| Table Name | PLACE_OF_SVC|
| File Name Patterne | _erda0014|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: POS_CODE(2),POS_DESC(60)  

|PROCEDURE_CODE||
|-----|-----|
| Table Name | PROCEDURE_CODE|
| File Name Patterne | _erda0016|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PROCEDURE_CODE(8),PROCEDURE_DESC(30)  

|Provider||
|-----|-----|
| Table Name | Provider|
| File Name Patterne | _erda0012|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PROVIDER_ID(6),PROVIDER_NAME(30),PROVIDER_TYPE_DESC(40),SPECIALTY_CODE(4),SUB_SPEC_CODE(4),SPECIALTY_CODE_DESC(40),PROVIDER_TYPE_CODE(2),NPI(10)  

|PROVIDER_CATEGORY||
|-----|-----|
| Table Name | PROVIDER_CATEGORY|
| File Name Patterne | _erda0017|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PROVIDER_CATEGORY(2),PROVIDER_CAT_DESC(40)  

|TYPE_OF_SVC||
|-----|-----|
| Table Name | TYPE_OF_SVC|
| File Name Patterne | _erda0019|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: TOS_CODE(4),TOS_DESC(30)  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A - Prestaging |
|Is the database production?| N/A - Prestaging  |
|Frequency of Extracts| Unknown. File delivery TBD. |

##Known Issues

File delivery TBD.

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20BITUFTS%20or%20%22Data%20Source%20Acronym%22%20~%20BITUFTS)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)