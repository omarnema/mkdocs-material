Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-26


#ACPCCLF (Arizona Community Physicians Centers for Medicare and Medicaid Services Medicare Shared Savings Prog)

**Client(s)**: [ACP](../ACP.md)  
**Density Area**: Southwest   

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
| Data Source Name| **Arizona Community Physicians Centers for Medicare and Medicaid Services Medicare Shared Savings Prog** |
| Data Source Acronym| **ACPCCLF** |
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
|Name|ACPCCLF_PRESTAGING_PRD|
|User Name|ACPCCLF_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time.*

##Custom Configurations



##Data Source

**Important Notes**  

* This will be a one-time historical load into prestaging. 
* The files for this source are a subset of CCLFs that have already been converted from fixed-width to delimited. 
* This subset does *not* include the demographics files, and as a result, we are receiving Excel files containing a list of members. As this is a one-time load into prestaging, we have agreed to import the Excel files into prestaging manually.  
    * Right now, we have the Q1-3 files. We will be loading th Q4 file as well when that becomes available. Based on comments from If that is the case, we should create a dummy member record for each HIC Number whose demographic info is missing.
    * In the future, we may be able to supplement this with more demographic data will the new ACP CCLF feed. Since this is several months out, we have decided to move forward with the data we have. 
    * We may need to do some MPI configuration to make matches between these dummy records and their clinical records based on HIC Number/payer records, but that is pending further investigation. 



The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0309-PR-ACPCCLF_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|CCLF1_PartA_ClaimHeader||
|-----|-----|
| Table Name | CCLF1_PartA_ClaimHeader|
| File Name Pattern | .CCLF1.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), PRVDR_OSCAR_NUM(6), BENE_HIC_NUM(11), CLM_TYPE_CD(2), CLM_FROM_DT(10), CLM_THRU_DT(10), CLM_BILL_FAC_TYPE_CD(1), CLM_BILL_CLSFCTN_CD(1), PRNCPL_DGNS_CD(7), ADMTG_DGNS_CD(7), CLM_MDCR_NPMT_RSN_CD(2), CLM_PMT_AMT(17), CLM_NCH_PRMRY_PYR_CD(1), PRVDR_FAC_FIPS_ST_CD(2), BENE_PTNT_STUS_CD(2), DGNS_DRG_CD(4), CLM_OP_SRVC_TYPE_CD(1), FAC_PRVDR_NPI_NUM(10), OPRTG_PRVDR_NPI_NUM(10), ATNDG_PRVDR_NPI_NUM(10), OTHR_PRVDR_NPI_NUM(10), CLM_ADJSMT_TYPE_CD(2), CLM_EFCTV_DT(10), CLM_IDR_LD_DT(10), BENE_EQTBL_BIC_HICN_NUM(11), CLM_ADMSN_TYPE_CD(2), CLM_ADMSN_SRC_CD(2), CLM_BILL_FREQ_CD(1), CLM_QUERY_CD(1)  

|CCLF2_PartA_ClaimDetail||
|-----|-----|
| Table Name | CCLF2_PartA_ClaimDetail|
| File Name Pattern | .CCLF2.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), CLM_LINE_NUM(10), BENE_HIC_NUM(11), CLM_TYPE_CD(2), CLM_LINE_FROM_DT(10), CLM_LINE_THRU_DT(10), PROD_REV_CTR_CD(4), CLM_LINE_INSTNL_REV_CTR_DT(10), HCPCS_CD(5), BENE_EQTBL_BIC_HICN_NUM(11), PRVDR_OSCAR_NUM(6), CLM_FROM_DT(10), CLM_THRU_DT(10), CLM_LINE_ALOWD_UNIT_QTY(24), CLM_LINE_CVRD_PD_AMT(17), HCPCS_1_MDFR_CD(2), HCPCS_2_MDFR_CD(2), HCPCS_3_MDFR_CD(2), HCPCS_4_MDFR_CD(2), HCPCS_5_MDFR_CD(2)  

|CCLF3_PartA_ProcedureCode||
|-----|-----|
| Table Name | CCLF3_PartA_ProcedureCode|
| File Name Pattern | .CCLF3.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), BENE_HIC_NUM(11), CLM_TYPE_CD(2), CLM_VAL_SQNC_NUM(2), CLM_PRCDR_CD(7), CLM_PRCDR_PRFRM_DT(10), BENE_EQTBL_BIC_HICN_NUM(11), PRVDR_OSCAR_NUM(6), CLM_FROM_DT(10), CLM_THRU_DT(10)  

|CCLF4_PartA_DiagnosisCode||
|-----|-----|
| Table Name | CCLF4_PartA_DiagnosisCode|
| File Name Pattern | .CCLF4.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), BENE_HIC_NUM(11), CLM_TYPE_CD(2), CLM_PROD_TYPE_CD(1), CLM_VAL_SQNC_NUM(2), CLM_DGNS_CD(7), BENE_EQTBL_BIC_HICN_NUM(11), PRVDR_OSCAR_NUM(6), CLM_FROM_DT(10), CLM_THRU_DT(10), CLM_POA_IND(7)  

|CCLF5_PartB_Physicians||
|-----|-----|
| Table Name | CCLF5_PartB_Physicians|
| File Name Pattern | .CCLF5.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), CLM_LINE_NUM(10), BENE_HIC_NUM(11), CLM_TYPE_CD(2), CLM_FROM_DT(10), CLM_THRU_DT(10), RNDRG_PRVDR_TYPE_CD(3), RNDRG_PRVDR_FIPS_ST_CD(2), CLM_PRVDR_SPCLTY_CD(2), CLM_FED_TYPE_SRVC_CD(1), CLM_POS_CD(2), CLM_LINE_FROM_DT(10), CLM_LINE_THRU_DT(10), CLM_LINE_HCPCS_CD(5), CLM_LINE_CVRD_PD_AMT(15), CLM_PRMRY_PYR_CD(1), CLM_LINE_DGNS_CD(7), CLM_PRVDR_TAX_NUM(10), RNDRG_PRVDR_NPI_NUM(10), CLM_CARR_PMT_DNL_CD(2), CLM_PRCSG_IND_CD(2), CLM_ADJSMT_TYPE_CD(2), CLM_EFCTV_DT(10), CLM_IDR_LD_DT(10), CLM_CNTL_NUM(40), BENE_EQTBL_BIC_HICN_NUM(11), CLM_LINE_ALOWD_CHRG_AMT(17), CLM_LINE_ALOWD_UNIT_QTY(24), HCPCS_1_MDFR_CD(2), HCPCS_2_MDFR_CD(2), HCPCS_3_MDFR_CD(2), HCPCS_4_MDFR_CD(2), HCPCS_5_MDFR_CD(2), CLM_DISP_CD(2), CLM_DGNS_1_CD(7), CLM_DGNS_2_CD(7), CLM_DGNS_3_CD(7), CLM_DGNS_4_CD(7), CLM_DGNS_5_CD(7), CLM_DGNS_6_CD(7), CLM_DGNS_7_CD(7), CLM_DGNS_8_CD(7)  

|CCLF6_PartB_DME||
|-----|-----|
| Table Name | CCLF6_PartB_DME|
| File Name Pattern | .CCLF6.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), CLM_LINE_NUM(10), BENE_HIC_NUM(11), CLM_TYPE_CD(2), CLM_FROM_DT(10), CLM_THRU_DT(10), CLM_FED_TYPE_SRVC_CD(1), CLM_POS_CD(2), CLM_LINE_FROM_DT(10), CLM_LINE_THRU_DT(10), CLM_LINE_HCPCS_CD(5), CLM_LINE_CVRD_PD_AMT(15), CLM_PRMRY_PYR_CD(1), PAYTO_PRVDR_NPI_NUM(10), ORDRG_PRVDR_NPI_NUM(10), CLM_CARR_PMT_DNL_CD(2), CLM_PRCSG_IND_CD(2), CLM_ADJSMT_TYPE_CD(2), CLM_EFCTV_DT(10), CLM_IDR_LD_DT(10), CLM_CNTL_NUM(40), BENE_EQTBL_BIC_HICN_NUM(11), CLM_LINE_ALOWD_CHRG_AMT(17), CLM_DISP_CD(2)  

|CCLF7_PartD_RxClaims||
|-----|-----|
| Table Name | CCLF7_PartD_RxClaims|
| File Name Pattern | .CCLF7.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CUR_CLM_UNIQ_ID(13), BENE_HIC_NUM(11), CLM_LINE_NDC_CD(11), CLM_TYPE_CD(2), CLM_LINE_FROM_DT(10), PRVDR_SRVC_ID_QLFYR_CD(2), CLM_SRVC_PRVDR_GNRC_ID_NUM(20), CLM_DSPNSNG_STUS_CD(1), CLM_DAW_PROD_SLCTN_CD(1), CLM_LINE_SRVC_UNIT_QTY(24), CLM_LINE_DAYS_SUPLY_QTY(9), PRVDR_PRSBNG_ID_QLFYR_CD(2), CLM_PRSBNG_PRVDR_GNRC_ID_NUM(20), CLM_LINE_BENE_PMT_AMT(13), CLM_ADJSMT_TYPE_CD(2), CLM_EFCTV_DT(10), CLM_IDR_LD_DT(10), CLM_LINE_RX_SRVC_RFRNC_NUM(12), CLM_LINE_RX_FILL_NUM(9)  

|CCLF8_BENE_Demographics||
|-----|-----|
| Table Name | CCLF8_BENE_Demographics|
| File Name Pattern | .CCLF8.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: BENE_HIC_NUM(11), BENE_FIPS_STATE_CD(2), BENE_FIPS_CNTY_CD(3), BENE_ZIP_CD(5), BENE_DOB(10), BENE_SEX_CD(1), BENE_RACE_CD(1), BENE_AGE(3), BENE_MDCR_STUS_CD(2), BENE_DUAL_STUS_CD(2), BENE_DEATH_DT(10), BENE_RNG_BGN_DT(10), BENE_RNG_END_DT(10), BENE_1ST_NAME(30), BENE_MIDL_NAME(15), BENE_LAST_NAME(40), BENE_ORGNL_ENTLMT_RSN_CD(1), BENE_ENTLMT_BUYIN_IND(1)  

|CCLF9_BENE_XREF||
|-----|-----|
| Table Name | CCLF9_BENE_XREF|
| File Name Pattern | .CCLF9.|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | True|
| Has Header? | False|
| Add Row Number? | False|  

**Columns**: CRNT_HIC_NUM(11), PRVS_HIC_NUM(11), PRVS_HICN_EFCTV_DT(10), PRVS_HICN_OBSLT_DT(10), BENE_RRB_NUM(12)  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20ACPCCLF%20or%20%22Data%20Source%20Acronym%22%20~%20ACPCCLF)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)