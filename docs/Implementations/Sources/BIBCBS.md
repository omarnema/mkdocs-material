Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-07-25
ModifyDate: 2016-07-25


#BIBCBS (BIDCO BCBS Commerical Claims)

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
| Data Source Name| **BIDCO BCBS Commerical Claims** |
| Data Source Acronym| **BIBCBS** |
| Type | **Claims** |
| Site ID | **83** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|BIBCBS_PRESTAGING_PRD|
|User Name|BIBCBS_PRD_PRESTAGING|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

No regular process has been established for file delivery, and the client has not yet agreed to send the files through the standard mechanism (unzipped, PGP-encrypted files sent through SFTP).   We received an initial set of files that were packages into password-protected zip files. 

Also, BIDCO has told us that BCBS regularly changes the passwords for the ZIP folders. 

##Data Source  

Documentation of flat file feed [here](https://arcadia.box.com/s/4jer5u0qn9ar18xfpq8vv2snkf7yght9).

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0540-PR-BIBCBS_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Medical||
|-----|-----|
| Table Name | Medical|
| File Name Patterne | _MED.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: INT_CLM_NUM,CLM_LINE_NUM,PDDATE,TYPE_SRV_CD,SVCDT,PROVID,SPRV_SPEC_CD,SPRV_TYPE_CD,RPRV_NUM,CURSUBID,MEM_FIRST_NAME,MEM_LAST_NAME,PATDOB,SEXCD,MEM_REL_CD,PCP_NUM,CPT_PROC_CD,CPT_PMOD1_CD,ICD_DIAG1_CD,DW_SRV_UNITS,CHARGE_AMT,PAID,netpay,PLACE_SRV_CD,WITHAMT,TOS_CAT1_CD,TOS_CAT2_CD,DRG_CD,REVENUE_CD,COPAY_AMT,DEDUCT_AMT,COBAMT,PT_PENALTY_AMT,CAP_IND,REFCIRC,ATPDATE,NETWK_PROD_CD,BCMBRNBR,ADMITDT,DISCHDT,DISCH_STAT_CD,SRC_IND,RATE_STRUCT_CD,HCFA_DRG_CD,REF_AUTH_NUM,UCP_AMT,DW_NETWK_IND,PCPTEAM,SUBPROD_IND,BPRVNUM,CLMCLASS,CLM_OPRV_NUM,CLM_OPRV_NPI,APR_DRG_CD,APR_SOI,APR_ROM,SPROVNPI,BPROVNPI,PCP_NPI,ICD_DIAG2_CD,ICD_DIAG3_CD,ICD_DIAG4_CD,ICD_DIAG5_CD,ICD_DIAG6_CD,ICD_DIAG7_CD,ICD_DIAG8_CD,ICD_DIAG9_CD,ICD_DIAG10_CD,ICD_DIAG11_CD,ICD_DIAG12_CD,ICD_DIAG13_CD,ICD_DIAG14_CD,ICD_DIAG15_CD,ICD_DIAG16_CD,ICD_DIAG17_CD,ICD_DIAG18_CD,ICD_DIAG19_CD,ICD_DIAG20_CD,ICD_DIAG21_CD,ICD_DIAG22_CD,ICD_DIAG23_CD,ICD_DIAG24_CD,ICD_PROC1_CD,ICD_PROC2_CD,ICD_PROC3_CD,ICD_PROC4_CD,ICD_PROC5_CD,ICD_PROC6_CD,ICD_PROC7_CD,ICD_PROC8_CD,ICD_PROC9_CD,ICD_PROC10_CD,ICD_PROC11_CD,ICD_PROC12_CD,ICD_PROC13_CD,ICD_PROC14_CD,ICD_PROC15_CD,ICD_PROC16_CD,ICD_PROC17_CD,ICD_PROC18_CD,ICD_PROC19_CD,ICD_PROC20_CD,POA_ICD_DIAG1_IND,POA_ICD_DIAG2_IND,POA_ICD_DIAG3_IND,POA_ICD_DIAG4_IND,POA_ICD_DIAG5_IND,POA_ICD_DIAG6_IND,POA_ICD_DIAG7_IND,POA_ICD_DIAG8_IND,POA_ICD_DIAG9_IND,POA_ICD_DIAG10_IND,POA_ICD_DIAG11_IND,POA_ICD_DIAG12_IND,POA_ICD_DIAG13_IND,POA_ICD_DIAG14_IND,POA_ICD_DIAG15_IND,POA_ICD_DIAG16_IND,POA_ICD_DIAG17_IND,POA_ICD_DIAG18_IND,POA_ICD_DIAG19_IND,POA_ICD_DIAG20_IND,POA_ICD_DIAG21_IND,POA_ICD_DIAG22_IND,POA_ICD_DIAG23_IND,POA_ICD_DIAG24_IND,HCPCS_PROC_CD,COINS_AMT,CURR_CLM_IND,LINE_STAT_CD,DW_CLM_LINE_STAT,ADMKEY,ATP_CURR_CLM_IND,ADMITDT2,DISCHDT2,TOS_CAT3_CD,ICD_SUBM_IND,ICD_DIAG25_CD,ICD_PROC21_CD,ICD_PROC22_CD,ICD_PROC23_CD,ICD_PROC24_CD,ICD_PROC25_CD,POA_ICD_DIAG25_IND,MEMB_LIAB_OTHER,DW_MEM_LIAB_AMT  

|Members||
|-----|-----|
| Table Name | Members|
| File Name Patterne | _MEM.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CURSUBID,BCMBRNBR,MTH_DT_YR_MTH,MEM_MTH_CNT,MEM_REL_CD,MEM_LAST_NAME,MEM_FIRST_NAME,MEM_STREET,MEM_STREET2,MEM_CITY,MEM_STATE,MEM_ZIP_CD,MEM_BIRTH_DT,MEM_GENDER,NETWK_PROD_CD,PCP_RCIRC_CD,PCP_PCT_NUM,ACCT_NUM,GRP_NUM,MEM_COV_CTYPE_CD,CLASS_RISK_CD,PCP_NUM,MEM_PCP_ST_DT,MEM_PROF_ST_DT,MEM_PROF_END_DT,PHARM_BEN_IND,RATE_STRUCT_CD,AGEGRP,GRP_ALPHA_PREFIX,MEM_PHONE_NUM,PCP_NPI,SUBPROD_IND,BH_BEN_IND,ID_CARD_NUM,MEM_MTH_ST_DT,MEM_MTH_END_DT  

|Pharmacy||
|-----|-----|
| Table Name | Pharmacy|
| File Name Patterne | _PHA.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: INT_CLM_NUM,PDDATE,TYPE_SRV_CD,SVCDT,PROVID,CURSUBID,MEM_FIRST_NAME,MEM_LAST_NAME,PATDOB,SEXCD,MEM_REL_CD,PCP_NUM,CHARGE_AMT,PAID,NETPAY,HEADCODE,SERVCODE,COPAY_AMT,DEDUCT_AMT,CAP_IND,REFCIRC,NETWK_PROD_CD,DISPENSE_CD,FORMULARY,DW_MDDB_MULTSRC_IND,CLM_NDC,MDDB_TC_CLASS_CD,MDDB_TC_GRP_CD,METRIC_QUANTITY,DEA_NUM,DEA_CLASS,NUM_REFILLS,DAYS_SUPPLY,BCMBRNBR,SRC_IND,PROD_DESC_ABBR,CLM_STRENGTH,RATE_STRUCT_CD,PCPTEAM,SUBPROD_IND,CLM_PDEA_NPI,CLMCLASS,RX_ORIGIN_CD,MAIL_RETAIL_IND,SCRIPT_COUNT,PCP_NPI,PHARM_NPI,COINS_AMT,BRAND_NAME  

|Provider||
|-----|-----|
| Table Name | Provider|
| File Name Patterne | _PRV.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PRV_NUM,PRV_FIRST_NAME,PRV_LAST_NAME,PRV_LIC_NUM,PRV_STREET,PRV_CITY,PRV_ZIP_CD,PRV_STATE,PRV_DEA_NUM,PRV_NPI  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A - Prestaging |
|Is the database production?| N/A - Prestaging  |
|Frequency of Extracts| Unknown. File delivery TBD. |

##Known Issues

File delivery TBD.

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20BIBCBS%20or%20%22Data%20Source%20Acronym%22%20~%20BIBCBS)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)