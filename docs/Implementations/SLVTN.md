Status: Internal-Only
Author: Author;
CreateDate: 2015-12-16
ModifyDate: 2015-12-16

# Silverton

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Silverton

####Client Density Area
Northwest

####Client Acronym
SLVTN

####Client Contract IDs
Software Subscription & Services Agreement:1066


##Overview


###Description
* Silverton Health is a CCO (OR-based ACO) comprised of Silverton Hospital, Salem Hospital, two IPA’s, and OR-based YVFWC clinics.  
* The CCO has 11,000 managed care lives, 6,000 of which are managed by YVFWC. 
* Project stakeholders are spread across multiple entities (hospital, YVFWC, IPA’s, WVHA)
###Location
Silverton, OR
###Other Details
N/A
###Front-end URLs
* [QA Front-End](https://SLVTNwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://SLVTNtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://Silverton.arcadiaanalytics.com/)


###Contacts  
| Name               | Position                                                   | Reports To   | Email                           | Phone               | Notes                                                                                                                                                      |
|--------------------|------------------------------------------------------------|--------------|---------------------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Juliana Huff       | Systems Analyst - Accountable Care                         | Sarah Fronza | JHuff3@silvertonhealth.org      | 971.983.5278 Direct | Key project contact; handles reporting for Sarah Fronza.  Works with many different areas to incorporate data (and the analytics platform) into workflows. |
| Joseph Huang       | CMO                                                        | Sarah Fronza | jhuang@silvertonhealth.org      |                     | Following acquisition by Legacy Health, Joe will be moving on to a hospital in Seattle in early 2016.                                                      |
| Sarah Fronza       | Interim CEO                                                | ---          | sfronza@silvertonhealth.org     |                     | Sarah was the VP of Managed Care and stepped up to the interim CEO role to guide Silverton Health through the Legacy acquisition.                          |
| Erin Mendenhall    | Clin. Inform. Srvcs Coordinator, Intergy Analyst & Trainer |              | EMendenhall@silvertonhealth.org | 971.983.5394 Direct | SME for Intergy.  Attends many status meetings.                                                                                                            |
| Heather Pilkington | Project Manager, Interim HIM Manager                       | Sarah Fronza | hpilkington@silvertonhealth.org | (503) 873-1758      | PM counterpart at Silverton - involved with many things related to Legacy Health acquisition, key point person for Sarah Fronza.                           |
| Lisa Ritchey       | Administrative Assistant                                   | Sarah Fronza | lritchey@silvertonhealth.org    | 503.873.1615 Direct | Schedule meetings with Sarah via Lisa.                                                                                                                     |
| Ryan Saddler       | Information Services Manager                               |              | RSaddler@silvertonhealth.org    | 971.983.5297 Direct | Manages our technical connectivity.  Attends most status meetings.                                                                                         |


##Inbound Data Sources
###Claims

* [Willamette Valley Claims - WVP](../Implementations/Sources/WVP/index.html) - Willamette Valley Community Health. See note on source page on name ambiguity. 

###Clinical

* [Family Medical Group - FAMEGR](../Implementations/Sources/FAMEGR/index.html) 

* [Hope Family Medicine - HOPEFM](../Implementations/Sources/HOPEFM/index.html) 

* [Silverton Hospital  - HOSP](../Implementations/Sources/HOSP/index.html) 

* [Northwest Family Medicine - NWESTFM](../Implementations/Sources/NWESTFM/index.html) 

* [Silverton Hospital Associates  - SHA](../Implementations/Sources/SHA/index.html) 




###Inactive 

* [Yakima Valley Farm Workers Clinic - YVFWC](../Implementations/Sources/YVFWC/index.html) - EHR has been inactivated. YVFWC is now using EPIC.

* [Northwest Family Medicine and Hope Family Medicine - NFMHFM](../Implementations/Sources/NFMHFM/index.html) - Replaced by two separate, HOPEFM and NWESTFM connectors.

* [Silverton Hospital TEMPORARY EXTRACT - DBID INCORRECT - HOSPTEMP](../Implementations/Sources/HOSPTEMP/index.html) 


##Outbound Data Sources
###Report Name
* Currently out of scope.


##Out of Scope
Custom managed care reconciliation reports are no longer in scope.

##Configurations

###Periods Processed
As of January 2016, all non default measures have been disabled. By default the product will dynamically run the  periods for the current week, month, quarter, trailing year and year.

Periods **must** be manually enabled to run for the last 12 months, 12 weeks, 12 quarters and 4 years each time new historical data is loaded or new periods/initiatives are enabled.

###Initiatives
* ACO
* ACO 2015
* CCO Claims
* CCO Hybrid
* MU S1
* PCMHS



###Measures

Per the original SOW MU, ACO, PCMH are all included (details below). The CCO measures should also be included though not part of original SOW.

**MU Core/Menu Measures**  
1. MU Allergy List / MU Allergy List Patient  
2. MU Clinical Summary  
3. MU Demographics  
4. MU EHI  
5. MU Lab Results  
6. MU Medical Reconciliation  
7. MU Medication CPOE / MU Medication CPOE Patient  
8. MU Medication eRx Provider Patient  
9. MU Medication List / MU Medication List Patient  
10. MU Medication Orders  
11. MU Patient Education Patient  
12. MU Patient Electronic Access  
13. MU Patient Reminders  
14. MU Problem List / MU Problem List Patient  
15. MU Referral with Care Summary  
16. MU Smoking Status  
17. MU Vitals  
18. MU Vitals Over 3 / MU Vitals Over 3 BP / MU Vitals Over 3 HW 
 
**ACO Measures**  
1. ACO Adult Weight Screening  
2. ACO CAD ACE Therapy  
3. ACO CAD ARB Therapy  
4. ACO CAD Composite  
5. ACO CAD LDL Lowering Drug Therapy  
6. ACO Colorectal Cancer Screening  
7. ACO Depression Screening  
8. ACO Diabetes A1c Control  
9. ACO Diabetes A1c Poor Control  
10. ACO Diabetes Aspirin Use  
11. ACO Diabetes BP Control  
12. ACO Diabetes Composite  
13. ACO Diabetes LDL Control  
14. ACO Diabetes Tobacco Non-Use Person  
15. ACO Fall Risk Screening  
16. ACO HF Beta Blocker Therapy  
17. ACO High BP Screening  
18. ACO Hypertension BP Control  
19. ACO Influenza Immunization  
20. ACO Mammography Screening  
21. ACO Medication Reconciliation  
22. ACO Tobacco Cessation  

**PCMH Operations Measures**  
1. PCMH Appointment No Show  
2. PCMH Active Medication List  
3. PCMH Advance Directive Recorded  
4. PCMH Allergy List  
5. PCMH BP Recorded Patient  
6. PCMH Care Management Support  
7. PCMH Clinical Summary  
8. PCMH Clinical Visits  
9. PCMH Date of Birth Recorded  
10. PCMH Email Address Recorded / PCMH Email Address Recorded Patient  
11. PCMH Ethnicity Recorded  
12. PCMH Gender Recorded  
13. PCMH Generate and Transmit eRx  
14. PCMH Health Insurance Recorded / PCMH Health Insurance Recorded Patient All Time  
15. PCMH Height Recorded Patient  
16. PCMH High Risk  
17. PCMH Lead Screening Children  
18. PCMH Legal Guardian Recorded  
19. PCMH Medical Reconciliation  
20. PCMH Patient Education  
21. PCMH Patient Not Recently Seen  
22. PCMH Preferred Language Recorded  
23. PCMH Primary Caregiver Recorded / PCMH Primary Caregiver Recorded Patient  
24. PCMH Problem List  
25. PCMH Race Recorded  
26. PCMH Record Advance Directives  
27. PCMH Referral To Facility w/ Care Summary  
28. PCMH Referral To Specialist w/ Care Summary  
29. PCMH Specific Medication  
30. PCMH Structured Lab Results  
31. PCMH Summary of Care Within Three Days  
32. PCMH Telephone Numbers Recorded / PCMH Telephone Numbers Recorded Patient  
33. PCMH Tobacco Status Recorded  
34. PCMH Transition Care Summary  
35. PCMH Weight Recorded Patient  



 
##Customization 

###Patient List 
Procedure on Git: [uspPopulatePlanAssignedLocationList](https://github.com/arcadia/qdw-silverton/blob/master/Database/Warehouse/Schema%20Objects/Schemas/rpt/Programmability/Stored%20Procedures/uspPopulatePlanAssignedLocationList.sql)  

**Specifications** 
 
* Only members active for medical products will be considered (dental/bh is dropped)
* Any member with > 15 days of eligibility in a given month will be considered
* For these members, the most recently assigned site/location prior to the end of the period will be selected
* Each assignment will occur at the Plan/Pod/Location level – for example: “WVCH/Silverton/Woodburn”
* Periods will be calculated for every quarter, but the current quarter will be calculated on a rolling basis. For example, when using the portal on 11/15/2015, the user will see the following lists:
	* [Plan] [Pod] [Location] Q2 2015 
Active members and assignments as of the June 2015 eligibility file
	* [Plan] [Pod] [Location] Q3 2015 
Active members and assignments as of the September 2015 eligibility file
	* [Plan] [Pod] [Location] Q4 2015
Active members and assignments as of the October 2015 eligibility file
* Upon receiving the November 2015 eligibility file, the “Q4 2015” list will update with those assignments  
* Historical lists will persist in perpetuity

**User Management**  
To avoid having to manually share each new list as its automatically created each quarter, the procedure contains automatic sharing of the patient list through the procedure by having user emails hard-coded in the procedure. While this is not the ideal approach, it is a work-around for the current limitation of the product as of the most recent release. 

### Custom Schema Elements
The Silverton client repository contains a few custom legacy procedures and tables that were formally used custom managed care reconciliation reporting 
### MPI Customization


The custom logic can be found in the following procedure:    
uspFilter\_FuzzyResults\_SLVTN.sql [View on GitHub](https://github.com/arcadia/qdw-silverton/blob/master/Database/MasterPatientIndex/Scripts/uspFilter_FuzzyResults_SLVTN.sql)

**Enhanced Logic**  
Match Criteria 1:  

* First 5 Characters of Full Last Name,
* First 3 Characters of Full First Name,
* Normalized DOB
* Normalized City
* Normalized Gender
* OR (if available) Social Security Number (SSN)

Match Criteria 2: 

* First 5 characters of last name,
* First 3 characters of first name,
* Medicaid ID,
* (If available) SSN,
* (if available) DOB

Match Criteria 3:

* First 5 characters of last name,
* First 3 characters of first name,
* Normalized DOB,
* Normalized Gender,
* Normalized Address Line 1,
* Normalized City
* OR (if available) SSN


**Base Logic:**
Match Criteria: Exact match on:  

- Normalized First Name,
- Normalized Last Name,
- Normalized Gender,
- Normalized DOB



##External Links
###Jira Issues
* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20SLVTN)
* [Client-Reported Open Issues ](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(SLVTN)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22))
* [Repo on Github](https://github.com/arcadia/qdw-Silverton) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/SLVTN)
* [Deployment History](https://labs.arcadiaanalytics.com/monitoring_framework/#vhistory)

##Attachments
* Put Releveant Attachments Here

