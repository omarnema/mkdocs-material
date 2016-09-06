Status: Internal-Only
Author: Author;
CreateDate: 2015-12-16
ModifyDate: 2015-12-16

# CHPW - Community Health Plan of Washington 

<a href="../../../img/chpw_logo.jpg">![](../../img/chpw_logo.jpg)</a>


## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Community Health Plan of Washington

####Client Density Area
Northwest

####Client Acronym
CHPW

####Client Contract IDs
Exhibit K - Analytics Conversion:869


##Overview


###Description
The Community Health Plan of Washington (CHPW) is a not-for-profit health plan founded in 1992 by a network of Community and Migrant Health Centers in Washington State (CHNW). There are a total of 19 Community Health Centers (CHC) operating 97 Clinic Sites, with over 2,700 primary care providers. CHPW offers health insurance through public programs under contract with the State of Washington (Medicaid, Medicare, Washington Health Program, Basic Health). Currently there are over 315,000 plan members.

Arcadia first helped CHPW with provider attribution in 2011. In 2012 Arcadia delivered QDW v2.x to CHPW. The 2.x platform was retired in 2015. Alongside the Analytics platform CHPW is also leveraging Arcadia's Adoption team.

In 2014 Arcadia delivered Arcadia Analytics (QDW v4.x) to CHPW and continues to expand the program and integrate with more other CHCs as well as help CHPW  


###Location
720 Olive Way #300, Seattle, WA 98101
###Other Details
In addition to the standard Analytics Implementation CHPW is levergaing Arcadia for some custom reporting and data feed. (See Inbound & outbound data sources)

CHPW plan data is also a source for other Analytics integrations like CCCN. See [CHPW-Claims - CHPWCLM](../Implementations/Sources/CHPWCLM/index.html)

###Front-end URLs
* [QA Front-End](https://CHPWwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://CHPWtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://CHPW.arcadiaanalytics.com/)


###Contacts  

##Inbound Data Sources
**Note:** When adding new inbound sources be sure to add it to the **dbo.uspPlanClinicSiteLink**  procedure as well as enabling historical measures for one nightly job run.

###Claims


* [CHPW Claims - CHPWC](../~Implementations/~Sources/CHPWC/index.html)   **To be decommissioned Feb 2016**
* [CHPW-Claims - CHPWCLM](../~Implementations/~Sources/CHPWCLM/index.html) **To be implemented Feb 2016**  

###Clinical

* [Neighborcare  - CARE](../~Implementations/~Sources/CARE/index.html) 
* [Columbia Basin Health Association - CBHA](../~Implementations/~Sources/CBHA/index.html) 
* [Community Health Association of Spokane - CHAS](../~Implementations/~Sources/CHAS/index.html) 
* [CHPW Regulatory Affairs Professionals Society - CHPWRAPS](../~Implementations/~Sources/CHPWRAPS/index.html) 
* [Country Doctor  - DOC](../~Implementations/~Sources/DOC/index.html) 
* [Family Care  - FAM](../~Implementations/~Sources/FAM/index.html) 
* [Healthpoint  - HPHC](../~Implementations/~Sources/HPHC/index.html) 
* [Interfaith - INFAITH](../~Implementations/~Sources/INFAITH/index.html) 
* [Moses Lake - MOSES](../~Implementations/~Sources/MOSES/index.html) 
* [NEWHP  - NEWHP](../~Implementations/~Sources/NEWHP/index.html) 
* [Peninsula Community Health Services - PCHS](../~Implementations/~Sources/PCHS/index.html) 
* [Seattle Maryville - SEAMAR](../~Implementations/~Sources/SEAMAR/index.html) 
* [Tacoma - TACMA](../~Implementations/~Sources/TACMA/index.html) 
* [Tri-Cities - TRICIT](../~Implementations/~Sources/TRICIT/index.html) 
* [ValleyView Health Center - VALVW](../~Implementations/~Sources/VALVW/index.html) 
* [Yakima Neighborhood Health Services  - YNHS](../~Implementations/~Sources/YNHS/index.html) 
* [Yakima Valley Farm Workers Clinic - YVFWC](../~Implementations/~Sources/YVFWC/index.html) 
* [International Community Health Services - ICHS](../~Implementations/~Sources/ICHS/index.html) 
* 
###Custom
* [CHPW RAPS -CHPWRAPS](../~Implementations/~Sources/CHPWRAPS/index.html) 
* [CHPW Restated Enrollment -R1264](../~Implementations/~Sources/R1264/index.html) 
* [CHPW Migration from QDW 2.X to QDW 4.X - QDWTWOMIG](../~Implementations/~Sources/QDWTWOMIG/index.html)  *Deprecated*

##Outbound Data Sources
###PCP Extract
* [PCP Data Extract - OF-CHPWPCP](../~Implementations/~Sources/OF-CHPWPCP/index.html) 





##Configurations
**Initiatives**  

* P4P 2015 
* P4P 2016
* UDS  

**Periods**  

Periods **must** be manually enabled to run for the last 12 months, 12 weeks, 12 quarters and 4 years each time new historical data is loaded or new periods/initiatives are enabled.

**Risk Score**  
CDPS

 
##Customization 

###Custom Schema Elements 

####Custom Schema Elements for [PCP Data Extract:   OF-CHPWPCP](../~Implementations/~Sources/OF-CHPWPCP/index.html)  


Send only most recent encounters  
All patients for that month's roster  
All location, site, provider, mpi data  

**dbo.uspPlanClinicSiteLink** - Procedure to generate plan clinic site links analogous to the lookup table used in the 2.x instance. Was needed when bringing over the roster logic from the retired 2.x CHPW Platform  
 
**dbo.uspRosterPatients** - Procedure to populate the needed roster tables(see below). By default runs for the current month but can take a start date parameter. Is executed without a parameter by the Informatica task flow.

**dbo.encounter_roster** / **dbo.v_encounter_roster** Table and view which contain the subset of patient encounters needed for the roster

**dbo.patient_roster** / **dbo.v_patient_roster** Table and view which contain the subset of patients needed for the roster

Extract Naming Example
||Location_Master||e.g. 2015_04_29_223400_003_001_Location.csv||
|Site_Master|e.g. 2015_04_29_223400_003_001_Site.csv|
|Provider_Master|e.g. 2015_04_29_223400_003_001_Provider.csv|
|v_patient_roster*|e.g. 2015_04_29_223400_003_001_Patient.csv|
|v_encounter_roster*|e.g. 2015_04_29_223400_003_001_Encounter.csv|
|mpi_person_member|e.g. 2015_04_29_223400_003_001_PersonMember.csv|
|mpi_person_patient|e.g. 2015_04_29_223400_003_001_PersonPatient.csv|



<<<<<<< HEAD

####Custom Schema Elements for [CHPW RAPS: CHPWRAPS](../Implementations/Sources/CHPWRAPS/index.html)  



**staging.v_RAPS_detail** - Staging view for warehouse table [wrk].[RAPS_detail] used for Informatica destination to load data into. It is needed because Informatica expects certain columns and data types that are not in the core table or core staging synonym. The view converts the datatypes in Informatica friendly ways in addition to providing a few dummy columns.  While inserting into a view is possible, the dummy columns that are mapped to hardcoded values present a problem for data insertion. Due to this, this view is nothing more than a way to trick Informatica to complete the load. The actual insert is done by the trigger on the view below.  

**staging.TRGI_VW_RAPS_detail** - An insert trigger on the view staging.v_RAPS_detai. Is used any time data is attempted to be inserted into the staging view, and instead inserts it into the proper format directly into [wrk].[RAPS_detail]  



####Custom Schema Elements for Security Layer Change, Roster Patient Lists and [Restated Enrollment: R1264](../~Implementations/~Sources/R1264/index.html) 
>>>>>>> parent of 53f788b... Removing ~ signs
**Overview:** Based on the custom feed R1264 from CHPW, patient lists will be created based on member assignments per quarter per center. The patient list procedure will be run each nightly job but will only update the patient lists once new data is loaded from the R1264 connector feed to the rpt.planSupplementRoster table. New patient lists for the corresponding quarter will be created 15 days after the start of that quarter.  If a member is enrolled in more than one site within a quarter, they will only be present on the patient list for the site in which they had the longest continuous assignment span within that quarter.


####Custom Schema Elements for Security Layer Change, Roster Patient Lists and [Restated Enrollment: R1264](../Implementations/~Sources/R1264/index.html) 
**Overview:** Based on the custom feed R1264 from CHPW, patient lists will be created using the R1264 member assignments per quarter per center. The patient list procedure will be run each nightly job but will only update the patient lists once new data is loaded from the R1264 connector feed into the rpt.planSupplementRoster table. New patient lists for the corresponding quarter will be created 15 days after the start of that quarter.  If a member is enrolled in more than one site within a quarter, they will only be present on the patient list for the site in which they had the longest continuous assignment span within that quarter. For example, in the rare case where during the coarse of a quarter a member was assigned to Site A for 3 weeks, then site B for 5 week, then back to Site A for 3 weeks. For that quarter, the person will appear only on Site B because that is the longest eligibility span within the quarter

The front end security layer will be appended to use the same set of logic to include all members who were assigned  at a site to be viewed by that corresponding site's front-end users. Just like the patient lists, only sites were members were assigned for the longest span in at least one quarter will be added. For example, if a member has been continuously enrolled in Site A then had two weeks assigned to Site B before going back to Site A - the member will NOT be added to the Site B roster. All members who appear on any quarter patient list, even if they are no longer assigned, will be appended to the site's security view.  The customized security layer change will only add, never remove, members from the core product security layer.  

<a href="../../../img/CHPW_R1264.png">![](../../img/CHPW_R1264.png)</a>



**staging.planSupplementRoster** - Staging synonym for the Warehouse table [rpt].[planSupplementRoster] used for Informatica destination to load data into.  

**rpt.planSupplementRoster** Warehouse table which contains the R1264 restated enrollment roster data. 
 
**lookup.supplementLocations**
A lookup table with location_names from the R1264 mapped to the product location in Location_Master. A post deploy script will populate the initial seeds.


**lookup.supplementRosterUsers** 
A lookup table with front-end user email domains. Which is used to crosswalk the front-end users to the the sites.  Patient lists are then automatically shared with the corresponding site's users based on their email.  New sites/email domains should be added to the table via an existing post-deploy script.  Domains can be crosswalked to a orig_site_id or to the value "ALL" which gives them access to all patient lists. **Only CHPW and Arcadia users should be marked as "ALL"**  

**rpt.uspPopulatePatientList**
The procedure uses the rpt.planSupplementRoster table as a base table. Since the table will not be scrubbed, the IDs will be not be consistent with the other plan sourced tables.  To get the member_id consistent with the other tables, the table will be joined to dbo.plan_member_elig on the member_no.  The member_id is then be checked against mpi.person_member and mpi.person_patient. Any person’s with an active corresponding entry the site in mpi.person_patient is added to the table rpt.memberSiteSupllement with the corresponding site from rpt.planSupplementRoster.

**rpt. memberSiteSupplement**
A table populated by the patient_list procedure [rpt].[planSupplementRoster]  which contains persons and all time assignments for R1264. This is the table that is used along with the core security layer logic for what persons front-end users can see. The table will include all persons for each site who are or have been assigned to that site on the R1264 extract/rpt.planSupplementRoster table.

**dbo.v_personSource_CHPW**
The a modified version of a core view which will unions rpt. memberSiteSupplement with the regular core security logic. The view is essentially selects all from the rpt.PersonSource_CHPW table. The filterconfig procedure will be updated to point to this view, instead of the regular core view: dbo.v_personSource. To implement the core security view. To remove the custom security logic, remove the post deploy and run a core deploy.

**rpt.PersonSource_CHPW**
Table which contains the union of the custom R1264 person-assignments from rpt. memberSiteSupplement in addition to what is found in the core security layer view dbo.v_personSource. The reason both the view v_personSource_CHPW and the table rpt.PersonSource_CHPW needs to exists, is because of core contraints which require the security layer to be a view and have view index.

**rpt.uspPopulatePersonSource**
Populates rpt.PersonSource_CHPW. Is executed as the last step by rpt.uspPopulatePatientList.


**R1264_security_layer_update.sql**  
Post deploy script to create index view on v_personSource_CHPW which is a core constraint. It also updated the core dbo.filterconfig table used to set which filter tables and views append the front-end.



###MPI Customization(if any)  

##External Links
###Jira Issues
* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20CHPW)
* [Client-Reported Open Issues ](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(CHPW)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22))

* [Repo on Github](https://github.com/arcadia/qdw-CHPW) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/CHPW)
* [Deployment History](https://labs.arcadiaanalytics.com/monitoring_framework/#vhistory)

##Attachments
* N/A

