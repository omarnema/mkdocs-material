Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-07-25
ModifyDate: 2016-08-15


#WCHNAMA (Western Connecticut Health Network - Aetna Medicare Advantage)

**Client(s)**: [WCHN](../WCHN.md)  
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
| Data Source Name| **Western Connecticut Health Network - Aetna Medicare Advantage** |
| Data Source Acronym| **WCHNAMA** |
| Type | **Claims** |
| Site ID | **19** |
| Architecture Model |  [**Client DB Extract (Prestaging w/ SFTP Get) with customizations**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging-SFTP-Get.md)
| Database hosting | **Arcadia Hosted** |


Files are pulled from WCHN's SFTP Server:  
**Path:** /EMRClaims/dailies/AetnaMedicareAdvantage  
**Host:** Secure.wchn.org  
**User:** zArcadia  
**Port:** 22  
Password is on LastPass.   


<a href="../../../img/ConnectorArchitecture-Prestaging-with-SFTP-Get.png">![](../../img/ConnectorArchitecture-Prestaging-with-SFTP-Get.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|WCHNAMA_PRESTAGING_PRD|
|User Name|WCHNAMA_PRD_PRESTAGING|  


###Location Hierarchy Configuration

No custom requirements. Should be under a WCHN parent location.

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0661-PR-WCHNAMA_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|CLAIMS||
|-----|-----|
| Table Name | CLAIMS|
| File Name Patterne | _Claims|
| Delimiter | \t|
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CLAIM_ID,CLAIM_LINE_ID,SRV_START_DT,SRV_END_DT,PAID_DT,LOB_CD,
ICD9_DIAG1,ICD_TYPE_CD,ICD9_DIAG2,ICD9_DIAG3,ICD9_DIAG4,PLACE_SVC_CD,
ICD9_PRM_DIAG1,PROC_CD,MOD_CD,UNIT_CNT,CLAIM_LINE_STATUS_CD,REVENUE_CD,
CLAIM_LINE_MSG_CD,CLAIM_DESC,PAID_AMT,SRV_PROV_ID,SRV_EPDB_PROV_ID,
SRV_PROV_NAME,SRV_PROV_SPL_CD,SRV_PROV_SPL_CAT_CD,SRV_PROV_SPL_NAME,
SRV_PROV_TYPE_CD,SRV_PROV_TYPE_DESC,PAID_PROV_ID,PAID_EPDB_PROV_ID,
PAID_PROV_NAME,PROV_TAX_ID,TIN_OWNER_NAME,NPI,PAID_PROV_SPL_CD,
PAID_PROV_SPL_CAT_CD,PAID_PROV_SPL_NAME,PAID_PROV_TYPE_CD,
PAID_PROV_TYPE_DESC,MEDCOST_SUB_CAT_CD,MEDCOST_SUB_CAT_DESC,
MEDCOST_CAT_CD,MEDCOST_CAT_DESC,MEMBER_ID,PCP_PO,PCP_NAME,PCP_TIN,
ICD9_DIAG5,ICD9_DIAG6,ICD9_DIAG7,ICD9_DIAG8,ICD9_DIAG9,ICD9_DIAG10,
ICD9_DIAG11,ICD9_DIAG12,ICD9_DIAG13,ICD9_DIAG14,ICD9_DIAG15,ICD9_DIAG16,
ICD9_DIAG17,ICD9_DIAG18,ICD9_DIAG19,ICD9_DIAG20,ICD9_DIAG21,ICD9_DIAG22,
ICD9_DIAG23,DRG_CD,DRG_VERSION  

|MEMBER||
|-----|-----|
| Table Name | MEMBER|
| File Name Patterne | Members|
| Delimiter | \t|
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MBR_MEMBER_ID,MBR_HIC_NO,PROV_MSCPRV_IND,MBR_PROD_TYPE_CD,
MBR_CONTRACT_NO,MBR_CVRG_EFF_DT,MBR_CVRG_TRM_DT,MBR_LAST_NAME,
MBR_FIRST_NAME,MBR_ADDRLN1,MBR_ADDRLN2,MBR_CITY_NAME,MBR_STATE_CD,
MBR_ZIP_CD,MBR_BIRTH_DT,MBR_GENDER_CD,MBR_TELEPHONE_NO,MBR_PART_D_IND,
MBR_AGE,PROV_NETWORK_NO,PROV_FULL_NAME,B_SCORE_NO,MBR_COUNTY_NAME,
MBR_BUS_LINE_CD,MBR_GRP_NUM,MBR_GRP_CNTL_NAME,PIN  

|PHARMACY||
|-----|-----|
| Table Name | PHARMACY|
| File Name Patterne | _RXClaims|
| Delimiter | \t|
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CLAIM_ID,ADJUDICATED_GPI_CD,DESCRIPTION,GENERIC_CD,CLASS,
DISPENSE_DT,NDC_CD,UNIT_CNT,DAYS_SUPPLY_CNT,BEN_PLAN_PAID_AMT,REFILL_CNT,
PROV_ID,PRESCRIBER_ID,PROV_NAME,TAX_ID,TIN_OWNER_NAME,NPI,MEMBER_ID  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A - Prestaging |
|Is the database production?| N/A - Prestaging  |
|Frequency of Extracts| TBD - Should be appx. monthly  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNAMA%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNAMA)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)