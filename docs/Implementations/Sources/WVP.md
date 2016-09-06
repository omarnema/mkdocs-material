Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-01-11
ModifyDate: 2016-01-11


#WVP (Willamette Valley Community Health)

**Client(s)**: [SLVTN](../SLVTN.md); [CCCN](../CCCN.md)  
**Density Area**: Northwest   

**NOTE:** There is some ambiguity with the acronym used for this source and the prestaging database.  This connector is for **Willamette Valley Community Health**, one of Oregon’s Coordinated Care Organizations (CCO) functions as a health plan. The usual acronym for this organization is **WVCH**.  Arcadia a business relationship with **WVCH**, where they send us data for the CCO members that are part of Silverton Health Partners (SHP). 

A separate organization, **Willamette Valley Physicians** is often abbreviated as **WVP** and is is a large network of providers whose leadership also oversees the CCO, WVCH.  **Willamette Valley Physicians is a separate organization and is NOT part of this Willamette Valley Community Health connector**. We do not currently have a business relationship with WVP, but we do have a business relationship with some of the participating practices who are also part of SHP.  Since we’d really like to have a business relationship with WVP down the road, it might be good to avoid using “WVP” in connector names.

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
| Data Source Name| **Willamette Valley Claims** |
| Data Source Acronym| **WVP** |
| Type | **Claims** |
| Site ID | **3** (Silverton)|
| Architecture Model | [**Client DB Extract (CDC)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-CDC.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Contacts
| Name             | Position               | Email                     | Notes                                                                                                                                                                            |
|------------------|------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Bill Guest       | CEO                    | bguest@wvchealth.org      | WVCH paid for additional Hope, Northwest, and Family connectors to be added to the Silveton analytics platform, so his approval is required for all travel billed for that work. |
| Nancy Rickenbach | Director of Operations | nrickenbach@wvchealth.org | WVCH main contact for Silverton Health; oversees plan operations.                                                                                                                |
| Lori Ashbaugh    | Compliance Officer     | lashbaugh@wvchealth.org   | Executed BAA with Arcadia.                                                                                                                                                       |

PHtech is the vendor which handles the data integration with Arcaida on behalf of WVCH.


###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|QDWSQLPROD03|
|Port|1433|
|Name|WVPSilvertonExtract|
|User Name|SLVTN_PRD_Informatica|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations
Unlike most pre-staging databases which are housed on a dedicated pre-staging server, the pre-staging database WVPSilvertonExtract is housed on the QDW Prod Server: QDWSQLPROD03.  It is not currently known why the initial set-up was done like this but is likely due to it pre-dating the typical configuration of the pre-staging server.

The data includes medical in addition to behavioral and dental plan data.

###Silverton
The data in the database should be for members assigned to Silverton sites (*see known issues below*) and all of the data should be loaded into the Silverton implementation.

###CCCN
The extract should be limited to only members assigned to YVFWC sites and for data only within the assignment period per the logic below:  

```sql
SELECT A.*  
FROM [EXAMPLE\_TABLE] A --SHOULD BE APPLIED TO ANY MEMBER TABLE THAT HAS AN EVENT DATE (EX. Claim)  
JOIN [member\_pcp] PCP  
ON A.DATE\_FIELD >= PCP.eff\_date  
AND (A.DATE\_FIELD <= PCP.term\_date  
OR  PCP.term\_date IS NULL)  
AND provider\_category='PCP'  
WHERE practice\_office_nm IN (--ONLY VALID YVFWC SITES:  
 'Pacific Pediatrics'  
,'Lancaster Family Health Center'  
,'Salud Medical Center' ) 
```


##Data Source

The source of data for this connector is a flat file or set of flat files loaded into prestaging and then transformed during extract.  
These files should be loaded from the folder **\\qdwsftp01\0017-WVP_SFTP_PRD**.  
Files loaded into prestaging for this source are:  


##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues
As of February 2016, there is a known issue with the vendor sending Arcadia additional member data. Only members with valid assignments should be included, per the logic below.

```sql
SELECT A.*  
FROM [EXAMPLE\_TABLE] A --SHOULD BE APPLIED TO ANY MEMBER TABLE THAT HAS AN EVENT DATE (EX. Claim)  
JOIN [member\_pcp] PCP  
ON A.DATE\_FIELD >= PCP.eff\_date  
AND (A.DATE\_FIELD <= PCP.term\_date  
OR  PCP.term\_date IS NULL)  
AND provider\_category='PCP'  
WHERE practice\_office_nm IN (--ONLY VALID SILVERTON SITES, ex:  
'Keizer Health Center'  
,'Hope Family Medicine Inc'  
,'Silverton Family Physicians'  
,'Yakima Valley Farm Workers'  
,'Woodburn Internal Medicine'  
,'Salud Medical Center'  
,'Lancaster Family Health Center'  
,'Woodburn Family Medicine'  
,'Mt Angel Family Medicine'  
,'Rodney E Orr MD PC'  
,'NW Family Medicine' )
```

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WVP%20or%20%22Data%20Source%20Acronym%22%20~%20WVP)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (**SLVTN**: *N/A*; **CCCN**: [CD-10687](https://jira.arcadiasolutions.com/browse/CD-10687) )
- SOW (*Unknown. Follow up with the Solution Architect*)