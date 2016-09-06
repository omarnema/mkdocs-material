Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-01-11
ModifyDate: 2016-02-12


#OF-WCHNGPRO (Western Connecticut Health Network - GPRO)

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
| Data Source Name| **Western Connecticut Health Network - GPRO** |
| Data Source Acronym| **OF-WCHNGPRO** |
| Type | **** |
| Site ID | **24** |
| Architecture Model | [**Outbound Feed**](../../Tech_Delivery/Standard-Implementations/Outbound-Feed.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Outbound-Feed.png">![](../../img/Connector-Outbound-Feed.png)</a>

###Outbound Feed Structure and Requirements

**Table Definitions:** 

1. `rpt.GPRO_Extract` – The source of the final extract that we will be sending to ACO Solutions. 
2. `lookup.GPRO_Patients` – Full list of members for GPRO. IncludeInExtract = 1 indicates that they have the TIN for WCMG (I can update it later on once we’ve added more sites). 
3. `lookup.GPRO_CodeMap` – Mapping from Arcadia concepts to codes used in the extract. 

Note: we are only pulling patients from AllScripts or Cerner and members with the `orig_source_id` of ‘008’ (CCLF) or ‘GPROLIST’ (a supplemental connector containing those members not included in CCLF). 

*Update:* For a second round of submission, this was updated to send only members from NMMG (WCHNNXT). These files were sent without any front end testing of WCHNNXT, only DQA results. 

**Additional Mappings:**
In addition to lookup.GPRO_CodeMap, there is some additional logic in the procedure itself documented below: 

**Dx Codes for BMI Percentile:**  

If age between 3 and 17, then  
If BMI Percentile < .05 then 'V85.51'  
Else if BMI Percentile < .85 then 'V85.52'  
Else if BMI Percentile < .95 then 'V85.53'  
Else if BMI Percentile >= .95 then 'V85.54'  

**Dx Codes for BMI.** 

If age between 18  and 74, then   
if BMI <= 18.9 then 'V85.0'  
else if BMI between 19 and 24.9 then 'V85.1'  
else if BMI between 25 and 25.9 then 'V85.21'  
else if BMI between 26 and 26.9 then 'V85.22'  
else if BMI between 27 and 27.9 then 'V85.23'  
else if BMI between 28 and 28.9 then 'V85.24'  
else if BMI between 29 and 29.9 then 'V85.25'  
else if BMI between 30 and 30.9 then 'V85.30'  
else if BMI between 31 and 31.9 then 'V85.31'  
else if BMI between 32 and 32.9 then 'V85.32'  
else if BMI between 33 and 33.9 then 'V85.33'  
else if BMI between 34 and 34.9 then 'V85.34'  
else if BMI between 35 and 35.9 then 'V85.35'  
else if BMI between 36 and 36.9 then 'V85.36'  
else if BMI between 37 and 37.9 then 'V85.37'  
else if BMI between 38 and 38.9 then 'V85.38'  
else if BMI between 39 and 39.9 then 'V85.39'  
else if BMI between 40 and 44.9 then 'V85.41'  
else if BMI between 45 and 49.9 then 'V85.42'  
else if BMI between 50 and 59.9 then 'V85.43'  
else if BMI between 60 and 69.9 then 'V85.44'  
else if BMI > 70 then 'V85.45'  

Loinc codes for vitals: 

* 8302-2 -> vitals_height
* 3141-9  -> vitals_weight
* 39156-5  ->  vitals_BMI
* 8480-6  ->  vitals_systolic
* 8462-4  ->  vitals_diastolic

Maintenance Result SNOMED codes:  

* Smoking/Tobacco Status:   
    * Positive: 449868002                               
    * Negative: 266919005
    * Unknown Status: 489483015
* PHQ-9/Depression Screen  
    * Positive Depression Screening: SNOMED 428181000124104
    * Negative Depression Screening: SNOMED 428171000124102
    * Unknown Status: LOINC 73832-8
    * PHQ-9 with Result: LOINC 44249-1


####Code on GitHub
* Tables
    - [GPRO Code Mapping](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Schema%20Objects/Schemas/Lookup/Tables/GPRO_CodeMap.sql)
    - [GPRO Patient List](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Schema%20Objects/Schemas/Lookup/Tables/GPRO_Patients.sql)
    - [Included Site/Source IDs](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Schema%20Objects/Schemas/Lookup/Tables/GPRO_SitesAndSources.sql)
    - [Result table (`rpt.GPRO_Extract`)](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Schema%20Objects/Schemas/rpt/Tables/GPRO_Extract.sql)
* Extract Procedure [`rpt.uspWCHNGpro`](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Schema%20Objects/Schemas/rpt/Programmability/Stored%20Procedures/uspWCHNGPRO.sql)
* Post Deploy:
    - [Configuration codemapping and data sources to include](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Scripts/SeedData/GPRO_Config.sql)
    - [List of patients to send](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Scripts/SeedData/GPRO_Patients.sql)



##Custom Configurations

The extract pulls all data from the table `rpt.GPRO_Extract`, which is populated by running `rpt.uspWCHNGpro`.

Because it is only intented to be run a few times, the running of this procedure was not included in the Informatica extract, so it needs to be done manaully.

##Data Source

This is an outbound feed connector that pulls data from the Arcadia Analytics Warehouse DB's for WCHN's GPRO Submission Process.  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| None. |
|Is the database production?| N/A - QDW Warehouse|
|Frequency of Extracts| On demand as needed for GPRO submission  |

##Known Issues


##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20OF-WCHNGPRO%20or%20%22Data%20Source%20Acronym%22%20~%20OF-WCHNGPRO)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- [Build Request](https://arcadia.box.com/s/6pit6pagte3l7bqg4g1fw1m2hymztf6c)
