Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-02-10
ModifyDate: 2016-02-17


#VGRIFFIN (VCA Anthem Griffin)

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

Due to an oversight on the part of the IL at the time, this was communicated as being an Athena feed rather than Anthem, so the name is slightly misleading.  


| Overview ||
|-----|-----|
| Data Source Name| **VCA Athena Griffin** |
| Data Source Acronym| **VGRIFFIN** |
| Type | **** |
| Site ID | **35** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|VGRIFFIN_PRESTAGING_PRD|
|User Name|VGRIFFIN_PRD_PRESTAGING|  


###Location Hierarchy Configuration

N/A 

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files from Anthem loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0416-PR-VGRIFFIN_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Medical||
|-----|-----|
| Table Name | Medical|
| File Name Patterne | Medical|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: SBSCRBR_ID,MBR_SQNC_NBR,MBR_BRTH_DT,MBR_GNDR_CD,EMP_BRTH_DT,EMP_GNCR_CD,MBR_REL_CD,CLM_TYPE_CD,REC_TYPE,CLM_NBR,CLM_LINE_NBR,ADJ_TYP_CD,ACCT_NBR,SUBGRP_NBR,DIAG_1_CD,DIAG_2_CD,PLACE_SRVC_CD,SRVC_STRT_DT,SRVC_END_DT,SRVC_CNT,RVNU_CD,PRIM_PROC_TYPE_CD,SEC_PROC_TYP_CD,PRIN_PROC_CD,OTHR_ICD_PROC_1_CD,PROC_MDFR_1_CD,ADMT_DT,BILL_TYPE_CD,DSCHRG_STTS_CD,BILL_PROV_TAX_ID,BILL_PROV_ZIP_CD,DEPT_NBR,BILL_PROV_SPEC,EMP_CNTRCT_TYPE,PROD_ID,CPAY_AMT,DDCTBL_AMT,COINSRN_AMT,COB_SVNGS_AMT,PAID_AMT,PAID_DT,CDHP_AMT,MDCR_IND,PKG_NBR,NTWK_IND,PCP_IND,APP_DENY_CD,BILL_PROV_CITY,BILL_PROV_ADRS_LINE_1,BILL_PROV_ADRS_LINE_2,BILL_PROV_ST,BILL_PROV_NM,DSCHRG_DT,FIRM_NM,MBR_FIRST_NM,MBR_LAST_NM,PAID_DAYS_CNT,PCP_NM,PCP_TAX_ID,PROC_MDFR_2_CD,MBR_SSN,ICD_VRSN_CD,BILL_PROV_NPI,RNDR_PROV_NPI,INP_DRG  

|Members||
|-----|-----|
| Table Name | Members|
| File Name Patterne | Members|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: SBSCRBR_ID,MBR_SQNC_NBR,MBR_BRTH_DT,MBR_GNDR_CD,MBR_REL_CD,EMP_ZIP_CD,MBR_EFCTV_DT,MBR_TERM_DT,PROD_ID,ACCT_NBR,SUBGRP_NBR,DEPT_NBR,HLTH_CLASS_COV_CD,PKG_NBR,EMP_CNTRCT_TYPE,MBR_FIRST_NM,MBR_LAST_NM,MBR_SSN  

|Rx||
|-----|-----|
| Table Name | Rx|
| File Name Patterne | Rx|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: SBSCRBR_ID,MBR_SQNC_NBR,MBR_BRTH_DT,MBR_GNDR_CD,MBR_REL_CD,CLM_TYPE_CD,CLM_NBR,ADJ_TYP_CD,ACCT_NBR,SUBGRP_NBR,DEPT_NBR,PROD_ID,PAID_DT,PAID_AMT,CPAY_AMT,DDCTBL_AMT,COINSRN_AMT,MCDR_IND,PKG_NBR,PRSC_PROV_DEA_NO,BILL_PROV_ZIP_CD,PERSON_ID,EMP_ZIP_CD,PHARM_NBR,RX_FILL_DT,DAYS_SPLY_NBR,NDC_CD,MAIL_ORDR_CD,BRND_GNRC_CD,DAW_CD,REFIL_CD,INGRED_COST_AMT,DSPNSG_FEE_AMT,SALES_TAX_AMT,FRMLRY_CD,SCRIPT_NO,QTY_DISP,DRUG_NM,GNRC_AVAIL_IND,CDHP_AMT,MBR_FIRST_NM,MBR_LAST_NM,NABP,PCP_NM,PHARM_NM,PRSC_PROV_NM,PRSC_PROV_SPEC,PRSC_PROV_TAX_ID,THERA_CLASS_1_NM,THERA_CLASS_GRP  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20VGRIFFIN%20or%20%22Data%20Source%20Acronym%22%20~%20VGRIFFIN)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Handoff Document](https://arcadia.box.com/s/ukvbbhom4ne87jvr56f9sdw8wuonhqcu)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)