Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-03-14
ModifyDate: 2016-04-05


#GR-STWMIG (Steward-Hosted Migrated Data Sources)

**Client(s)**: [STW](../STW.md)  
**Density Area**: Northeast   

This is a group of sources that can be connected to from within the Steward network. They were all previously used in 3.x via a DRVS connector. 

Full list of sources is:  

|DBID | Name (Acronym) |  
|-----|-----|  
|2|Hyde Park (HYDEPARK)| MySQL | 
|3| Nissage Cadet (NICAD)| MySQL | 
|4|M. Morey Farizan (FARIZAN)| MySQL | 
|5|Northeast Nephrology & Internal Medicine (NNIM)| MySQL | 
|6|Zuhayr Hemady (HEMADY)| MySQL | 
|7|Thomas Kenney (KENNEY)| MySQL | 
|9|Ambama Clinic (AMBAMA)| MySQL | 
|11|Alonso Medical (ALONSO)| MySQL | 
|12|APG  Brockton (APGBROCK)| MySQL | 
|13|APG Bridgewater (APGBRIDGE)| MySQL | 
|17|Pleasant Valley Internists (PLSVAL)| MySQL | 
|18|William Edwards (WEDWRDS)| MySQL | 
|19|Sharda Kaul (KAUL)| MySQL | 
|20|Michel Lirette (LIRETTE)| MySQL | 
|21|Vascular and Vein Associates (VAVA)| MySQL | 
|22|Merrimack Valley Pulmonary Associates (MVPA)| MySQL | 
|23|Infectious Disease Associates (INFDA)| MySQL | 
|24|Luba Tsypkin & Ashish Gandi (LTAG)| MySQL | 
|25|Pediatric Professional (PEDPROF)| MySQL | 
|26|AASP Allergy and Asthma Speciality (AASP)| MySQL | 
|28|Charles S. Chen (CHEN)| MySQL | 
|29|Dermatology Associates (DERMASSOC)| MySQL | 
|31|Dr.  Stephen Sands (SANDS)| MySQL | 
|32|Associates Internal Medicine (AIM) (AIM)| MySQL | 
|34|Resil (RESIL)| MySQL | 
|35|Timothy Anderson (ANDERSON)| MySQL | 
|36|Derm Specialists (DERMSPEC)| MySQL | 
|39|Alan Kurland (KURLAND)| MySQL | 
|40|Neponset Valley Surgical (NEPVAL)| MySQL | 
|41|Robert Patz & Mebel (PATZ)| MySQL | 
|42|Steven Ross (ROSS)| MySQL | 
|43|Paul Burns (BURNS)| MySQL | 
|45|Manish Tandon (TANDON)| MySQL | 
|46|Nicole McDonald (MCDON)| MySQL | 
|47|Tural Pediatrics (TURALPED)| MySQL | 
|49|Michael Romanowsky (RMNWSKY)| MySQL | 
|50|Stephen Kovacs (KOVACS)| MySQL | 
|51|Bijan Sadrnoori (SADRNRI)| MySQL | 
|52|Leonid Kotkin (KOTKIN)| MySQL | 
|53|Brian Hinnebusch (HNNBSCH)| MySQL | 
|54|John T Frasca (FRASCA)| MySQL | 
|55|St Annes Pain Management (SAPM)| MySQL | 
|56|Millview Medical Joncas (MILLVW)| MySQL | 
|57|Carney Pulmonary (CARNEY)| MySQL | 
|58|CPN1 (CPN1)| MySQL | 
|59|CPN 2 (CPN2)| MySQL | 
|61|Good Sam Production (GSAM)| MySQL | 
|62|New England Medical Group (NEMG)| MySQL | 
|63|Andrade Medical Associates (ANDRADE)| MySQL | 
|64|Kevin McCarthy (KMCCRTHY)| MySQL | 
|65|Methuen Medical Group (METHUENMG)| MySQL | 
|70|APG Easton (APGEASTON)| MySQL | 
|71|Joseph Emma (EMMA)| MySQL | 
|72|We Care (WECARE)| MySQL | 
|73|Sharma (SHARMA)| MySQL | 
|74|Sawyer (SAWYER)| MySQL | 
|75|Raouf Sayegh (SAYEGH)| MySQL | 
|76|Whittier-Merrimack Valley (WHITMERVAL)| MySQL | 
|78|Whittier-Haverhill Family (WHITHAVRHL)| MySQL | 
|81|Simon Ho (SMHO)| MySQL | 
|82|Dr. Michael Kutka (KUTKA)| MySQL | 
|83|Dr. Sidiqqi (SIDIQQI)| MySQL | 
|84|Dr. Chapman (CHPMN)| MySQL | 
|85|Dr. Maureen Norman (NRMN)| MySQL | 
|88|Quincy Internal Med - Dr. Gales (QIMGALES)| MySQL | 
|92|Prima CARE (PRIMACARE)| SQL Server | 
|93|Associates in Nephrology, PC (ANEPHPC)| SQL Server | 
|94|Yuliya Mandel, MD, PC (MANDEL)| SQL Server | 
|95|Eric Cohen (ECOHEN)| SQL Server | 
|96|Brigida Tironese-Call (TIRON)| SQL Server | 
|97|Lydia Zuser (ZUSER)| SQL Server | 
|98|Taunton Medical (TAUNTON)| SQL Server | 
|99|Mill River Pediatrics (MILLRIV)| SQL Server | 
|104|[Loew Family Practice (LOEWFAM)| SQL Server | 


Connectivity details can be found on [Box](https://arcadia.box.com/s/pgejoftb0mvzbfzmz263owqcbi3brg8x)  


## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture 

### Implementation Round 1: Migration  
[PRIMACARE](./PRIMACARE.md) and [CPN1](./CPN1.md) were chosen as the two pilot practices for the migration of the Steward AA instance from 3.6 (Steward hosted) to 4.x (Arcadia hosted). 

Identical configurations (i.e. queries) will be used for all other Steward eCW MySQL (CPN1) and MSSQL (Prima CARE) connectors for this migration.  

### Implementation Round 2: HCC/Risk Navigator  

Second implementation round to update these queries for HCC Navigator. The scope of this changes is less than the changes required for front end. 

Required query changes for this implementation round are:

1.  **New query** will be written and implemented to populated the **progress note table**  
2.  Updated **assessment** query that fixes the **primary key** issue identified during the migration project  
3.  Update **provider** query to set **provider active indicator** in accordance with Steward’s requirements
4.  Confirm that it is possible given existing encounter/charge records to switch from using encounter types to CPT codes for the **medical encounter** definition. This is considered our standard and preferred approach, so as long as we have the appropriate linkages to make this work, it’s probably best to switch. Given this is eCW and we’ve taken this approach with pretty much all other eCW connectors, I don’t anticipate any issues with this.   
5.  Update **patient** query to map **SSN** according to logic in current 4.x eCW patient query.  All other mappings should not change.   

For this implementation round, PRIMACARE (SQL Server) and ANDRADE (MySQL) are being used as pilots. 

<a href="../../../img/Connector-Client-DB-Extract-CDC.png">![](../../img/Connector-Client-DB-Extract-CDC.png)</a>

###Database Connection Information  

[See connectivity document on Box](https://arcadia.box.com/s/pgejoftb0mvzbfzmz263owqcbi3brg8x)  


###Location Hierarchy Configuration

Locations seeds are not required at this time. Will be required in the future, but not until a second round. 

##Custom Configurations

### Implementation Round 1: Migration  

1. Queries for this connector are to be a direct conversion of existing DRVS queries into syntax that Informatica can use. There should be no updates or additions to these queries beyond what is needed to run the end-to-end ETL and match the content of the existing HDS feed. 
2. The criteria for handoff acceptance are as follows:   
- Row counts match counts extracted since most recent historical extract in 3.x; The full table row counts do not need to match exactly, due to data no longer existing in the same state in the eCW DB.  
- Date field completeness -- % completeness of date fields should match those of the 3.x tables within a reasonable error. This is being tested due to the tight constraints placed on date formatting in Informatica.
3. **Seed data should match exactly that of the 3.x instance within the constraints of the new environment. No new seed mapping is required.**
4. `t_immunization` is not used. Immunizations at Steward are pulled into `t_maintenance` with the *maintenance_imm* query. 


### Implementation Round 2: HCC/Risk Navigator  

Updates to the above list: 

1. This is no longer completely true. See [Overview](#overview-and-architecture) for more details. 
2. Requirement for handoff is that the requirements listed above have been completed and validated to QA Team's satisfaction. 
3. This is still valid with the exception of medical encounter definition, which should be switch to CPT codes if possible. 
4. This is still valid. This change will be implemented in Implementation Round 3. 

###SFTP Customization for Steward Sources  

See [**Steward Custom SFTP Workflow**](.\STW-Custom-SFTP-Workflow.md). 

##Data Source

The data for this connector is pulled from [eCW 9](../../Tech_Delivery/EHR-Documentation/eCW.md).

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None |
|Is the database production?| No  |
|Frequency of Extracts| Nightly |

##Known Issues  

* Queries are based off of historical eCW queries, i.e., certain known issues may still apply.  
* Updates will be applied in a future implementation round. More details to come. 
* Additional Client Literature [Click Here](https://arcadia.app.box.com/files/0/f/3940812891/Per-Site%20Gap%20Analysis)

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20GR-STWMIG%20or%20%22Data%20Source%20Acronym%22%20~%20GR-STWMIG)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/3pctsu7aqbvxzonk7b020khs0x1zerg9)
- SOW (*Unknown. Follow up with the Solution Architect*)