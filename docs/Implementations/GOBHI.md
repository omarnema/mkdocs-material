Status: Internal-Only
Author: Author;
CreateDate: 2015-2-5
ModifyDate: 2015-2-5

# Greater Oregon Behavioral Health

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [Specifications](#specifications)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Greater Oregon Behavioral Health

####Client Density Area
Northwest

####Client Acronym
GOBHI

####Client Contract IDs
Software Subscription & Services Agreement:1066

##Overview
**In Scope**:  
Building a clinically integrated network  
&nbsp;&nbsp;&nbsp;&nbsp;Implement Arcadia Analytics platform and stand up the web-based portal: 

- Set up 12 behavioral health EHR data connectors
- Set up 3 claims connectors
- Set up 10 physical health EHR data connectors



###Description
Behavioral health client
###Location
The Dalles, OR 97058

###Other Details
N/A
###Front-end URLs
[QA Front-End](https://gobhiwebtst01.arcadiahosted.local/)


###Contacts  
**BEN** **EXSTROM**  
IT Director  
206-491-0095  
ben.exstrom@gobhi.net

**NATALIE** **ELSTON**  
360-931-7398  
natalie.elston@gobhi.net



#Inbound Data Sources

###Claims
- [GOBHI Eligibility - GOBHIELG](../~Implementations/~Sources/GOBHIELG/index.html)
- [Eastern Oregon CCO - EOCCO](../~Implementations/~Sources/EOCCO/index.html)
- Columbia Pacific CCO
- Umpqua Health Alliance CCO

###Behavioral Health
- [Wallowa Valley Center for Wellness - WALLOWA](../~Implementations/~Sources/WALLOWA/index.html)
- [Clatsop Behavioral Health - CLTSPB](../~Implementations/~Sources/CLTSPB/index.html)
- [Community Counseling Solutions - CCS](../~Implementations/~Sources/CCS/index.html)
- [Center for Human Development - CFHD](../~Implementations/~Sources/CFHD/index.html)
- Mid-Columbia Center for Living - MCCFL
- [Tillamook Family Counseling - TILLA](../Implementations/Sources/TILLA/index.html)
- Symmetry Care - SYMCAR
- Lifeways - LIFEWY
- Lake County Mental Health - LCMH
- [New Directions NW - NDNW](../Implementations/Sources/NDNW/index.html)
- Columbia Community Mental Health - CCMH
- Community Health Alliance - CHA

###Physical Health
- Good Shepherd Healthcare System
- Grande Ronde Hospital
- Harney District Hospital
- Blue Mountain Hospital
- Morrow County Health District
- St. Alphonsus Medical Group
- Columbia River Community Health Services
- Treasure Valley Pediatric Clinic, P.C.
- Valley Family Healthcare
- Yakima Family Farm Workers Clinic


##Outbound Data Sources
###Report Name
* Details

##Specifications

###Sources
| Source Type           | Data Source             | Participant                              |
|-----------------------|-------------------------|------------------------------------------|
| Behavioral Health EHR | Credible                | Community Counseling Solutions           |
| Behavioral Health EHR | Credible                | Lake County Mental Health                |
| Behavioral Health EHR | Credible                | Lifeways                                 |
| Behavioral Health EHR | Credible                | Symmetry Care                            |
| Behavioral Health EHR | Unicare (Profiler)      | Columbia Community Mental Health         |
| Behavioral Health EHR | Unicare (Profiler)      | Community Health Alliance                |
| Behavioral Health EHR | Anasazi                 | Mid-Columbia Center for Living           |
| Behavioral Health EHR | ECHO                    | Center for Human Development             |
| Behavioral Health EHR | Streamline              | New Directions NW                        |
| Behavioral Health EHR | Care Logic (Qualifacts) | Clatsop Behavioral Health                |
| Behavioral Health EHR | Care Logic (Qualifacts) | Tillamook Family Counseling              |
| Behavioral Health EHR | OWITS                   | Wallowa Valley Center for Wellness       |
| Claims                | Claims Extract          | Columbia Pacific CCO                     |
| Claims                | Claims Extract          | Umpqua Health Alliance CCO               |
| Shared EOCCO          | Claims Extract          | Eastern Oregon CCO                       |
| Shared EOCCO          | Meditech/LSS            | Good Shepherd Healthcare System          |
| Shared EOCCO          | Practice Partners       | Grande Ronde Hospital                    |
| Shared EOCCO          | GE Centricity           | Harney District Hospital                 |
| Shared EOCCO          | e-MDs                   | Blue Mountain Hospital                   |
| Shared EOCCO          | TBD                     | Morrow County Health District            |
| Shared EOCCO          | NextGen                 | St. Alphonsus Medical Group              |
| Shared EOCCO          | SuccessEHS              | Columbia River Community Health Services |
| Shared EOCCO          | Allscripts              | Treasure Valley Pediatric Clinic, P.C.   |
| Shared EOCCO          | Intergy                 | Valley Family Healthcare                 |
| Shared EOCCO          | Epic                    | Yakima Family Farm Workers Clinic        |

###Behavioral Health Required Data Elements

| Table          | Required Status |
|----------------|-----------------|
| Allergy        | Optional        |
| Appoitnment    | Required        |
| Assessment     | Required        |
| Charge         | Required        |
| Encounter      | Required        |
| Maintenance    | Required        |
| Medicationlist | Preferred       |
| Order          | Optional        |
| Patient        | Required        |
| Payer          | Preferred       |
| Prescription   | Preferred       |
| Problem        | Preferred       |
| Provider       | Required        |
| Result         | Optional        |
| Vitals         | Optional        |    
 
 
####Behavioral Maintenance Observations  
* Depression Follow Up 
* Depression Screening 
* Depression Screening Refused 
* Patient Education 
* Patient Reminder 
* Smoking Status 
* Tobacco Screen 
* Tobacco Status 
* PHQ 9 
* Interpreter needed 
* Living situation 
* Dates for changes in living arrangements 
* Disabled 
* Rental Assistance 
* Food Stamps 
* Legal Status 
* SSISA 
* ASAM 
* Pre-Admission Authorization Form 
* Tobacco use -Age at first use 
* Tobacco use -Frequency 
* Tobacco use -Addiction addressed 
* Alcohol use - Current 
* Alcohol use - Age at first use 
* Alcohol use - Frequency 
* Alcohol use - Addiction Addressed 
* Alcohol use - Risk Assessment 
* Recreational Drugs - Current 
* Recreational Drugs - Age at first use 
* Recreational Drugs - Frequency 
* Recreational Drugs - Route of Administration 
* Recreational Drugs - Addiction addressed 
* Recreational Drugs -Risk Assessment 


##Out of Scope

- Back-end data access (CR in process to bring into scope 2/8/16)
- Custom analytics development

##Configurations
### Measures/Reports needed
* CCO 
* HEDIS  


### Periods Processed
	* Historic/Onetime
	* Weekly
	* Nightly




###Deletion of Non Eligible Members
As part of 4.12 only patients who match via the MPI to GOBHI Elig and are eligible at that time will have their data loaded into the warehouse.


Example of which patient's data would be update/inserted into the warehouse  
```sql
SELECT tp.* FROM t_patient tp 
JOIN mpi.person_patient pp 
ON pp.pat_id=tp.pat_id
AND pp.active_ind='Y'
JOIN mpi.person_member pm
ON pm.person_id=pp.person_id
AND pm.active_ind='Y'
JOIN dbo.plan_member_elig pme
ON pme.member_id=pm.member_id
AND pme.delete_ind='N'
AND pme.source_id=(SELECT source_id FROM plan_source WHERE source_desc='GOBHI Eligibility')
AND pme.start_date<=GETDATE() 
AND (pme.end_date>=GETDATE() OR pme.end_date IS NULL)
 
```  



 
##Customization 
* Custom Schema Elements
* MPI Customization(if any)

##External Links
###Jira Issues
* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20GOBHI)
* [Client-Reported Open Issues ](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(GOBHI)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22))
* [Repo on Github](https://github.com/arcadia/qdw-GOHBI) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/GOHBI)
* [Deployment History](https://labs.arcadiaanalytics.com/monitoring_framework#vhistory)

##Attachments
* Put Relevant Attachments Here

