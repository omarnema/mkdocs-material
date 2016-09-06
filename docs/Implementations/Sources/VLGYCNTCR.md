Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-04-29
ModifyDate: 2016-05-09


#VLGYCNTCR (VCA - ConnectiCare_Legacy)

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

| Overview ||
|-----|-----|
| Data Source Name| **VCA - ConnectiCare_Legacy** |
| Data Source Acronym| **VLGYCNTCR** |
| Type | **** |
| Site ID | **32** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

This feed contains historical data only, prestaging can be a truncate/load.  No new or recent data is expected.  


###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|VLGYCNTCR_PRESTAGING_PRD|
|User Name|VLGYCNTCR_PRD_PRESTAGING|  


###Location Hierarchy Configuration

Nothing custom required.

##Custom Configurations

None documented at this time. 

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0508-PR-VLGYCNTCR_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|BH||
|-----|-----|
| Table Name | BH|
| File Name Patterne | BH|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CCI_MBR,AGE,riskpop,GROUP_,DIVISION,business_unit,Prog,
pcp_prov,pcp_aff,pcp_sub_prog,pcp_area,serv_prov,serv_aff,serv_sub_prog,
serv_provcat,serv_provclass,serv_spec1,claim,serv,claim_type,location,drg,
modifier,YMDEFF,ymdend,ymdadmit,ymddischarge,ymdpaid,ymdrcvd,ymdentered,
proc1,proc2,proc3,diag,diag2,diag3,diag4,diag5,explain1,explain2,
serv_status,fund,feesched,count_field,days,mintues,amtcharge,amtallow,
amtpay,amtrisk,amtcopay,amtdeduct,amtcoins,amtdiscount,amtffs,paid,
NMI,DomesticClmAmt,ICDIndicator  

|Med||
|-----|-----|
| Table Name | Med|
| File Name Patterne | Med|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: member,age,riskpop,group_,division,business_unit,prog,
pcp_prov,pcp_aff,pcp_sub_prog,pcp_area,serv_prov,serv_aff,serv_sub_prog,
serv_provcat,serv_provclass,serv_spec1,claim,serv,claim_type,location,
coverage_class_code,DRG,modifier,ymdeff,ymdend,ymdadmit,ymddischarge,
ymdpaid,ymdrcvd,ymdentered,proc1,proc2,proc3,diag,diag2,diag3,diag4,diag5,
explain1,explain2,serv_status,fund,feesched,count_field,days,minutes,
amtcharge,amtallow,amtpay,amtrisk,amtcopay,amtdeduct,amtcoins,amtdiscount,
amtffs,paid,NMI,DomesticClmAmt,ICDIndicator  

|Member||
|-----|-----|
| Table Name | Member|
| File Name Patterne | Member|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MEMBER,Subscriber,NMI,FIRST_NAME,LAST_NAME,
BUSINESS_UNIT,PROG,RISKPOP,YMDBIRTH,SEX,PHONE_ONE,ADDRESS_ONE,
ADDRESS_TWO,CITY,county,STATE,ZIP,PROV,AFF,YMDEFF,YMDEND,CLASS,
CORP,GROUP_,DIVISION,DrugBenefit_Flag,contractype  

|Provider||
|-----|-----|
| Table Name | Provider|
| File Name Patterne | Provider|
| Delimiter | ||
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: serv_prov,serv_aff,ymdeff,ymdend,firstname,lastname,HAT_Code,Prov_Cat,spec1,spec2,sub_prog,IRS,license,status,phone1,phone2,address1,address2,area,city,state,zip,NPI  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| No, Prestaging|
|Is the database production?| No, Prestaging |
|Frequency of Extracts| Never - legacy one-time feed.  |

##Known Issues  
  
1.  Data feed does not contain any location data. 
2.  Original set of files did not contain a full set of PCP data, i.e. ~25% of the plan_member_assignment records refer to a nonexistent provider. These additional ID-provider mappings are being requested from the client. 

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20VLGYCNTCR%20or%20%22Data%20Source%20Acronym%22%20~%20VLGYCNTCR)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)