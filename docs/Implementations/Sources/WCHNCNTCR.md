Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-05-03
ModifyDate: 2016-05-03


#WCHNCNTCR (WCHN Connecticare Claims)

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
| Data Source Name| **WCHN Connecticare Claims** |
| Data Source Acronym| **WCHNCNTCR** |
| Type | **Claims** |
| Site ID | **36** |
| Architecture Model | [**Client DB Extract (Prestaging w/ SFTP Get) with customizations**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging-SFTP-Get.md)|
| Database hosting | **Arcadia Hosted** |

Files are pulled from WCHN's SFTP Server:  
**Path:** /EMRClaims/dailies/Connecticare 
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
|Name|WCHNCNTCR_PRESTAGING_PRD|
|User Name|WCHNCNTCR_PRD_PRESTAGING|  


###Location Hierarchy Configuration

Nothing custom. 

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0514-PR-WCHNCNTCR_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|CodeDetails||
|-----|-----|
| Table Name | CodeDetails|
| File Name Patterne | CodeDetails.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CodeSet,Code,CodeDescription  

|CodeDetails_med||
|-----|-----|
| Table Name | CodeDetails_med|
| File Name Patterne | CodeDetails_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CodeSet,Code,CodeDescription  

|ControlTotals||
|-----|-----|
| Table Name | ControlTotals|
| File Name Patterne | ControlTotals.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,LOB,RunDate,TableName,Recs,AmtAllow  

|ControlTotals_med||
|-----|-----|
| Table Name | ControlTotals_med|
| File Name Patterne | ControlTotals_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,LOB,RunDate,TableName,Recs,AmtAllow  

|Medical||
|-----|-----|
| Table Name | Medical|
| File Name Patterne | Medical.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,NMI,NMI_Sub,LOB1,LOB2,Age,Gender,GrpNum,
DivNum,COCLevel1,COCLevel2,ClmNum,ClmServNum,ClaimType,PCP_Num,PCP_AffNum,
PCP_NPI,PCP_TIN,ServProvNum,ServProvAffNum,ServProvNPI,ServProvTIN,
ServProvSpec1,ServProvClass,ServProvCat,RefProvNum,RefProvAffNum,RefProvNPI,
RefProvTIN,DateEff,DateEnd,DateAdmit,DateDischarge,DatePaid,Proc1,
Proc1Type,Location,Modifer1,Modifier2,DRG,MDC,AdmitType,DischargeStatus,
PaymentStatus_NetworkInOut,ERAvoid_Flag,InptFac_Acute_SubAcute,Qty,Days,
AmtCharge,AmtAllow,AmtPay  

|Medical_med||
|-----|-----|
| Table Name | Medical_med|
| File Name Patterne | Medical_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,NMI,NMI_Sub,LOB1,LOB2,Age,Gender,GrpNum,
DivNum,COCLevel1,COCLevel2,ClmNum,ClmServNum,ClaimType,PCP_Num,PCP_AffNum,
PCP_NPI,PCP_TIN,ServProvNum,ServProvAffNum,ServProvNPI,ServProvTIN,
ServProvSpec1,ServProvClass,ServProvCat,RefProvNum,RefProvAffNum,RefProvNPI,
RefProvTIN,DateEff,DateEnd,DateAdmit,DateDischarge,DatePaid,Proc1,
Proc1Type,Location,Modifer1,Modifier2,DRG,MDC,AdmitType,DischargeStatus,
PaymentStatus_NetworkInOut,ERAvoid_Flag,InptFac_Acute_SubAcute,Qty,Days,
AmtCharge,AmtAllow,AmtPay  

|MedicalDiagnosis_med||
|-----|-----|
| Table Name | MedicalDiagnosis_med|
| File Name Patterne | MedicalDiagnosis_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ClmNum,DiagCategory,DiagCd,ICD_Indicator  

|MedicalDiagnsos||
|-----|-----|
| Table Name | MedicalDiagnsos|
| File Name Patterne | MedicalDiagnsos.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ClmNum,DiagCategory,DiagCd,ICD_Indicator  

|Member||
|-----|-----|
| Table Name | Member|
| File Name Patterne | Member.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ApplyMo,LOB1,LOB2,NMI,NMI_Sub,First_Name,
Last_Name,Gender,DateBirth,Age,PCP_Num,PCP_AffNum,PCP_NPI,PCP_TIN,
ContractClass,GrpNum,DivNum,Address1,Address2,City,County,State,Zip,Phone1  

|Member_med||
|-----|-----|
| Table Name | Member_med|
| File Name Patterne | Member_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ApplyMo,LOB1,LOB2,NMI,NMI_Sub,First_Name,
Last_Name,Gender,DateBirth,Age,PCP_Num,PCP_AffNum,PCP_NPI,PCP_TIN,
ContractClass,GrpNum,DivNum,Address1,Address2,City,County,State,Zip,Phone1  

|Pharmacy||
|-----|-----|
| Table Name | Pharmacy|
| File Name Patterne | Pharmacy.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,NMI,NMI_Sub,LOB1,LOB2,Age,Gender,GrpNum,DivNum,ClmNum,RxNum,AdjudNum,PCP_Num,
PCP_AffNum,PCP_NPI,PCP_TIN,PrescribProvNum,PrescribProvNPI,PrescribProvTIN,
PrescribDEANum,PrescribPharmacyNum,PrescribPharmacyNPI,
PrescribPharmacyName,DateFill,DateBilled,DateTrans,RefillNum,NDC,DrugName,GPI,
GCN,GBrand_Flag,GBSourceCd,TheraClassCd,Formulary_Flag,
SpecialtyDrug_Flag,Tier,Retail_MailOrder_Flag,DAWCd,DaysSupply,PaidQty,
ScriptCount1,ScriptCount2,AmtAWP,AmtGross,AmtPaid  

|Pharmacy_med||
|-----|-----|
| Table Name | Pharmacy_med|
| File Name Patterne | Pharmacy_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,NMI,NMI_Sub,LOB1,LOB2,Age,Gender,GrpNum,DivNum,ClmNum,RxNum,AdjudNum,PCP_Num,PCP_AffNum,PCP_NPI,PCP_TIN,PrescribProvNum,PrescribProvNPI,PrescribProvTIN,
PrescribDEANum,PrescribPharmacyNum,PrescribPharmacyNPI,PrescribPharmacyName,
DateFill,DateBilled,DateTrans,RefillNum,NDC,DrugName,GPI,GCN,
GBrand_Flag,TheraClassCd,Formulary_Flag,SpecialtyDrug_Flag,Tier,
Retail_MailOrder_Flag,DAWCd,DaysSupply,PaidQty,ScriptCount1,
ScriptCount2,AmtAWP,AmtGross,AmtPaid  

|ProvLookup||
|-----|-----|
| Table Name | ProvLookup|
| File Name Patterne | ProvLookup.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ProvNum,ProvNPI,ProvFirstName,ProvLastName  

|ProvLookup_med||
|-----|-----|
| Table Name | ProvLookup_med|
| File Name Patterne | ProvLookup_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ProvNum,ProvNPI,ProvFirstName,ProvLastName  

|TINLookup||
|-----|-----|
| Table Name | TINLookup|
| File Name Patterne | TINLookup.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ProvTIN,ProvTINName  

|TINLookup_med||
|-----|-----|
| Table Name | TINLookup_med|
| File Name Patterne | TINLookup_med.|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: Partnership_Current,ProvTIN,ProvTINName  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A - Prestaging |
|Is the database production?| No - Prestaging |
|Frequency of Extracts| Run prestaging load daily. |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNCNTCR%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNCNTCR)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)