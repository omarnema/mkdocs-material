Status: Internal-Only
Author: Nick Daniel
CreateDate: 2016-01-11
ModifyDate: 2016-03-14


#MVP (MVP Claims Data)

**Client(s)**: [AHP](../AHP.md)  
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
| Data Source Name| **MVP Claims Data** |
| Data Source Acronym| **MVP** |
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
|Name|MVP_PRESTAGING_PRD|
|User Name|MVP_PRD_PRESTAGING|  


###Location Hierarchy Configuration

Not applicable, as this is a claims feed.

##Custom Configurations

All plan data is sourced from 3 different client files as follows:

**Med** - plan_billing_provider, plan_claim_diagnosis, plan_claim_header, plan_claim_line, plan_group, plan_lob, plan_group, plan_provider  
**Rx** - plan_claim_rx  
**Elig** - plan_member, plan_member_address, plan_member_assignment, plan_member_elig, plan_member_month, plan_product, plan_site  

The only exceptions are plan_payor and plan_source, which are populated by queries run from Information_Schema.Columns, and plan_product, which is populated by all 3 client files.

##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0292-PR-MVP_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


|Elig||
|-----|-----|
| Table Name | Elig|
| File Name Pattern | Elig|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: MEMID, ENRID, RELFLAG, MEMFIRSTNAME, MEMLASTNAME, GENDER, DOB, ADDR1, ADDR2, CITY, STATE, ZIP, HOMEPHONE, WORKPHONE, COVTYPEID, COVTYPEDESC, EFFDATE, TERMDATE, CMSTATUS, PCPID, PCPNAME, PCP_NPI, PCP_TIN, STATUS, PLANTYPE, PLANNAME, GUID  

|Med||
|-----|-----|
| Table Name | Med|
| File Name Pattern | Med|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CLMNUM, CLAIMLINENUMBER, CLMTYPE, CLMTYPEDESC, MEMID, ENRID, RELFLAG, MEMFIRSTNAME, MEMLASTNAME, GENDER, DOB, ADDR1, ADDR2, CITY, STATE, ZIP, HOMEPHONE, WORKPHONE, FROMDATE, TODATE, RCVDATE, PAIDDATE, BILLTYPE, POSCODE, SPECCODE, SPECDESC, FIRSTDIAGCODE, SECONDDIAGCODE, THIRDDIAGCODE, FOURTHDIAGCODE, FIFTHDIAGCODE, SIXTHDIAGCODE, SEVENTHDIAGCODE, EIGHTHDIAGCODE, NINTHDIAGCODE, TENTHDIAGCODE, MODIFIERCODE, CPT4_1, CPT4_2, CPT4_3, HCPCS, CPTII, MODIFIERCODE2, REVCODE1, REVCODE2, REVCODE3, REVCODE4, REVCODE5, ICD9PROCCODE1, ICD9PROCCODE2, ICD9PROCCODE3, ICD9PROCCODE4, ICD9PROCCODE5, ICD9PROCCODE6, DRGTYPE, DRGCODE, DISCHSTATUS, TYPEOFBILL, ADJCODE, PROVID, PROVNAME, PROVIDERFIRSTNAME, PROVIDERLASTNAME, PROVNPI, PROVZIPCODE, PROVTYPECODE, PROVTYPEDESC, NWKID, NWKNAME, INNWK, SERVICEUNITS, PAIDAMT, BILLEDAMT, ALLOWEDAMT, PPOSAVINGAMT, ENRPAIDAMT, COINSAMT, COPAYAMT, DEDUCTAMT, NOTALLOWEDAMT, COBAMT, PLANEXCLAMT, ICD10PROCEDURECODEINDICATOR1, ICD10PROCEDURECODEINDICATOR2, ICD10PROCEDURECODEINDICATOR3, ICD10PROCEDURECODEINDICATOR4, ICD10PROCEDURECODEINDICATOR5, ICD10PROCEDURECODEINDICATOR6, ICD10DXINDICATORDX1, ICD10DXINDICATORDX2, ICD10DXINDICATORDX3, ICD10DXINDICATORDX4, ICD10DXINDICATORDX5, ICD10DXINDICATORDX6, ICD10DXINDICATORDX7, ICD10DXINDICATORDX8, ICD10DXINDICATORDX9, ICD10DXINDICATORDX10, LOBCODE  

|Rx||
|-----|-----|
| Table Name | Rx|
| File Name Pattern | Rx|
| Delimiter | ||
| Text Qualifier | none|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: TRANSNUM, SEQNO, MEMID, ENRID, RELFLAG, MEMFIRSTNAME, MEMLASTNAME, GENDER, DOB, ADDR1, ADDR2, CITY, STATE, ZIP, HOMEPHONE, WORKPHONE, FILLDATE, PAIDDATE, METRICQUANTITY, DAYSSUPPLY, DRUGCODE, DRUGSTRENGTH, FORMULARY_YN, MOI, PRESCRIBERID, PRESCRIBERNAME, PHARMID, PHARMNAME, PHARMZIPCODE, PAIDAMT, BILLEDAMT, INGREDCOST, DISPENSINGCOST, SALESTAX, ALLOWEDAMT, ENRPAIDAMT, COINSAMT, COPAYAMT, DEDUCTAMT, NOTALLOWEDAMT, ADMFEES, AWP, COBAMT, ADJCODE, DISCOUNTAMT, PRESCOUNT, LOBCODE  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| N/A, files are generated by the client. |
|Is the database production?| N/A, files are generated by the client.  |
|Frequency of Extracts| Monthly  |

##Known Issues

We are currently receiving full historical extracts from the client each month as opposed to incremental files.

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20MVP%20or%20%22Data%20Source%20Acronym%22%20~%20MVP)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/un1amgyabo3x2842hlumcaakbkbe1zda)
- [Connector Handoff](https://arcadia.box.com/s/ixyws0rehvqhbq9outr7q5vaxfskel6w)
- [SOW](https://arcadia.box.com/s/q1r4ok4ysxa2mj2rm8ort4474tk5z1jj)