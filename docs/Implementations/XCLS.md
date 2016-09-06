Status: Internal-Only
Author: Author;
CreateDate: 2015-12-16
ModifyDate: 2016-07-26


# Excellus

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [Out of Scope](#out-of-scope)
* [Configurations](#configurations)
* [Customization](#customization)
* [External Links](#external-links)

##Client Details
####Client Name
Excellus

####Client Density Area
New York

####Client Acronym
XCLS

####Client Contract IDs
Initial Build - 687


##Overview


###Description
Arcadia has been contracted to administer the quality portion of a pay for performance (P4P) contract with the practices in the Excellus community.  Arcadia is responsible for aggregating data across all of the practices participating in a P4P contract and providing our analytics portal to those clients so that they may track their performance on proprietary quality measures defined by Excellus.  In addition to data aggregation and providing providers and health plan employees with the tools to administer this contract, Arcadia sends Excellus a HEDIS supplemental data feed that they can use to enhance their performance on the quality measures that CMS and NCQA hold them accountable to.  This process involves maintenance of an outbound data feed and annual audit support.  There’s a tremendous amount of detail that goes into this arrangement and the program is always growing, changing, and taking on new shapes.
###Location
Rochester, NY
###Other Details
N/A
###Front-end URLs
* [QA Front-End](https://XCLSwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://XCLStest.arcadiaanalytics.com/) 
* [PROD Front-End](https://Excellus.arcadiaanalytics.com/)


###Contacts  

| Name               			| Position                              				| Email                           			| Phone        |
| Dave Barber        			| Contracting (STJ)                     				| David.Barber@Excellus.com     			| 315-200-9362 |
| Brian Barringer       		| Contracting (Crouse)                  				| Brian.Barringer@excellus.com  			| 315-798-4218 |
| Johnny Brown					| Original Owner of Claims Extract						| Johnny.Brown@excellus.com 				| 585-339-3822 |
| Gloriella Burns				| Director of Revenue Integrity & Risk					| gloriela.burns@excellus.com 				| 585-314-1501 |
| Chris Diehl					| Pharmacy Contact 										| Christopher.Diehl@excellus.com  			| 585-530-5648 |
| Paul Eisenstadt 				| Executive Sponsor (Provider Network)					|											|			   |
| Lindsay Federation 			| Project Manager										| Lindsay.Federation@excellus.com 			| 585-339-7938 |
| Laura Ferris					| Lead Clinical Consultant (CAP)						| Laura.Ferris@excellus.com 				| 315-671-7134 |
| Beth Gawronski				| Clinical Consultant (GRIPA, Lifetime)					| Beth.Gawronski@excellus.com 				| 585-820-5463 |
| Terry Greene					| EDW Contact 											| Teresa.Greene@excellus.com 				| 585-238-4223 |
| Patricia Hope					| Sr. Project Manager									| patricia.hope@excellus.com 				|			   |
| Kathleen Janiszeski (KJ)		| Clinical Consultant (STJ, Crouse)			 			| Kathleen.Janiszeski@univerahealthcare.com | 716-857-6214 |
| Chris Kidder					| HEDIS Auditor 							 			| Christopher.Kidder@excellus.com 			| 315-671-6992 |
| Constantinos Kokkinis (Gus)	| Technical Owner of Claims Extract			 			| Constantinos.Kokkinis@excellus.com 		| 585-402-6909 |
| Megan Kosowski				| Clinical Consultant (Bassett)				 			| megan.kosowski@excellus.com 				| 315-798-4246 |
| Sarah Lemley					| Technical Owner of HEDIS Supplemental Data 			| Sarah.Lemley@excellus.com 				| 585-530-5577 |
| Teresa Murray					| Project Sponsor 							 			| Teresa.Murray@excellus.com  				|		   	   |
| Jeff Polk 					| Contracting owner 						 			| jeffrey.polk@excellus.com 				| 585-327-7550 |
| Melissa Ringelberg 			| Contracting (AHP, Lifetime) 							| Melissa.Ringelberg@excellus.com 			| 585-453-6369 |
| Donna Satterlee 				| Primary Contact - Clinical Consultant (AHP, Lourdes) 	| Donna.Satterlee@excellus.com 				| 585-613-1655 |
| Mary Stubley 					| Director, Contracting & Innovative Payment 			| Mary.Stubley@excellus.com 				| 315-798-4292 |
| Krista Ventrone 				| Government Programs Director 							| Krista.Ventrone@excellus.com 				| 315-726-5189 |
| Tony Vitagliano 				| Executive Sponsor (Contractng) 						|											|			   |


##Inbound Data Sources
###Claims

* [Excellus Claims - XCLSC](../Implementations/Sources/XCLSC/index.html) 

###Clinical

* [Abbasey Medical PLLC - ABBA](../Implementations/Sources/ABBA/index.html) 

* [Dr. Akowuah - AKOWUAH](../Implementations/Sources/AKOWUAH/index.html) 

* [Dr. Alagappan - ALAGA](../Implementations/Sources/ALAGA/index.html) 

* [Alexander Medical Group - ALX](../Implementations/Sources/ALX/index.html) 

* [Arnot Ogden Medical Center - ARNOT](../Implementations/Sources/ARNOT/index.html) 

* [Bayoumi Medical PLLC - BAYOU](../Implementations/Sources/BAYOU/index.html) 

* [Dr. Breen - BREEN](../Implementations/Sources/BREEN/index.html) 

* [Brighton Family Medicine - BRIFM](../Implementations/Sources/BRIFM/index.html) 

* [Canandaigua MC - CANADA](../Implementations/Sources/CANADA/index.html) 

* [Chittenango Medical & Wellness - CHT](../Implementations/Sources/CHT/index.html) 

* [Central New York Family - CNYFAMC](../Implementations/Sources/CNYFAMC/index.html) 

* [Dar Medical Associates](../Implementations/~Sources/DAR/index.html) 

* [Dr. Depner - DEP](../Implementations/~Sources/DEP/index.html) 

* [Endwell Family Physicians - EFP](../Implementations/Sources/EFP/index.html) 

* [Eastside Pediatrics - EST](../Implementations/Sources/EST/index.html) 

* [Family Care Medical Group - FCR](../Implementations/Sources/FCR/index.html) 

* [FF Thompson - FFT](../Implementations/Sources/FFT/index.html) 

* [Family Medicine Associates of CNY - FMA](../Implementations/Sources/FMA/index.html) 

* [Family Medicine of Carthage - FMC](../Implementations/Sources/FMC/index.html) 

* [Family Practice Associates - FPASSOC](../Implementations/Sources/FPASSOC/index.html) 

* [Goodman Pediatrics - GDP](../Implementations/Sources/GDP/index.html) 

* [Genesis Pediatrics](../Implementations/~Sources/GNS/index.html) 

* [Goodman Pediatrics - GDP](../Implementations/~Sources/GDP/index.html) 

* [His Branches Health Services - HBH](../Implementations/Sources/HBH/index.html) 

* [Honeoye Valley Family Practice  - HONEVAL](../Implementations/Sources/HONEVAL/index.html) 

* [Internal Medicine Associates of Auburn - IMA](../Implementations/Sources/IMA/index.html) 

* [Independent IMB - INDIMB](../Implementations/Sources/INDIMB/index.html) 

* [Jefferson Family Medicine - JEFFERS](../Implementations/Sources/JEFFERS/index.html) 

* [Jones Memorial - JONES](../Implementations/Sources/JONES/index.html) 

* [Kerper - KERP](../Implementations/Sources/KERP/index.html) 

* [Keuka Family Practice Associates - KEU](../Implementations/Sources/KEU/index.html) 

* [Lake Country Family Medicine - LAKECON](../Implementations/Sources/LAKECON/index.html) 

* [Letchworth Family Practice - LETFM](../Implementations/Sources/LETFM/index.html) 

* [Lewis County General Hospital - LEWGEN](../Implementations/Sources/LEWGEN/index.html) 

* [Dr. Lewis - LEWIS](../Implementations/Sources/LEWIS/index.html) 

* [Legacy Pediatrics - LGY](../Implementations/Sources/LGY/index.html) 

* [Lourdes - LOURDES](../Implementations/Sources/LOURDES/index.html) 

* [Elmwood Pediatrics - LWD](../Implementations/Sources/LWD/index.html) 

* [Mahoney, Hrohoe & Garneau - MAHHROGAR](../Implementations/Sources/MAHHROGAR/index.html) 

* [Marcellus Family Medicine - MFM](../Implementations/Sources/MFM/index.html) 

* [Naples Valley Family Medicine - NAP](../Implementations/Sources/NAP/index.html) 

* [Northern Allegany Medical Group - NORALLE](../Implementations/Sources/NORALLE/index.html) 

* [Noyes Employed - NOYES](../Implementations/Sources/NOYES/index.html) 

* [Panorama Pediatric Group - PAN](../Implementations/Sources/PAN/index.html) 

* [Bassett - PR-BAST](../Implementations/Sources/PR-BAST/index.html) 

* [Preventive Medicine Associates - PREVMA](../Implementations/Sources/PREVMA/index.html) 

* [Pathway Pediatrics  - PWP](../Implementations/Sources/PWP/index.html) 

* [Dr. Qureshi - QURESHI](../Implementations/Sources/QURESHI/index.html) 

* [Dr. Smith - SMITH](../Implementations/Sources/SMITH/index.html) 

* [Stony Brook Peds](../Implementations/Sources/STONBROK/index.html) 

* [St.Joseph's Hospital Health Center - STJ](../Implementations/Sources/STJ/index.html) 

* [Sunrise Pediatrics - SUN](../Implementations/Sources/SUN/index.html) 

* [Twelve Corners Pediatrics - TCP](../Implementations/Sources/TCP/index.html) 

* [Dr. Tinkelman - TNK](../Implementations/Sources/TNK/index.html) 

* [Tri-county Family Medicine - TRICON](../Implementations/Sources/TRICON/index.html) 

* [United Health Services - UHS](../Implementations/Sources/UHS/index.html) 

* [University Health Services - UNIV](../Implementations/Sources/UNIV/index.html) 

* [University Rochester Medical Center - URMC](../Implementations/Sources/URMC/index.html) 

* [University Rochester Medical Center - SafteyNet](../Implementations/Sources/URMCSN/index.html) 

* [Victor Health - VIC](../Implementations/Sources/VIC/index.html) 

* [Valley View Family Practice Associates - VVF](../Implementations/Sources/VVF/index.html)
* [Dr. Yavorek - YAV](../Implementations/Sources/YAV/index.html) 
* [Zoneci Medical - ZONECI](../Implementations/Sources/ZONECI/index.html) 


##Outbound Data Sources

* [Excellus Claims Outbound Feed - OF-XCLSC](../Implementations/Sources/OF-XCLSC/index.html) 

* [HEDIS Outbound Feed - OF-IPPSUP](../Implementations/Sources/OF-IPPSUP/index.html) 


##Configurations
###Periods Processed
By default the product will dynamically run the periods for the current month, quarter, trailing year and year.  In addition the previous two trailing years are also calculated as part of the nightly job.  These additional trailing years are configured during a client deploy, so if for any reason there hasn't been a client deploy in more than a month the nightly job will be processing different trailing years than intended.

Periods **must** be manually enabled to run for all Month, Quarter, Trailing Year and Year periods whose start dates range from the previous year to the current time period each time new historical data is loaded or new measures/initiatives are enabled.  These periods should then be disabled after the historical load is complete to reduce the run time of the nightly job.

####Out of Scope
A **frozen trailing year** period was previously used, but is no longer in scope.

**UHS** previously agreed to have their clinical data in our warehouse, but as of 11/2015 they withdrew from the program citing data security concerns and all UHS data has been purged from all environments.

###Initiatives
* ACO
* IPP/AQCA

###Measures
 
ACO measures are enabled in all environments, but IPP/ACQA measures are limited by environment to allow for newly created measures to be tested in QA before being promoted to higher environments.

**ACO Measures**  

* Adult BMI  
* BP Screen  
* Breast Cancer Screen  
* CAD ACE/ARB  
* CAD Composite  
* CAD LDL Drug  
* Colo Cancer Screen  
* Depression Screen  
* DM A1C <= 9  
* DM A1c Control  
* DM A1C Poor Control  
* DM Aspirin  
* DM BP Control  
* DM Composite  
* DM LDL Control  
* DM Tobacco Non Use  
* Fall Risk Screen  
* HF Beta Blocker  
* HTN BP Control  
* Influenza Imm  
* IVD Aspirin  
* IVD LDL Control  
* Med Reconciliation  
* Pneumo Vaccine  
* Tobacco Cessation  

**IPP/AQUA Measures Enabled in UAT/PRD** 

* ABX Avoidance for Bronchitis  
* Adolescent BMI Pct  
* Adolescent Imm  
* Adolescent Prev Care  
* Approp Test Child Pharyngitis  
* Appropriate URI Tx  
* Breast Cancer Screen  
* CAD/IVD Aspirin  
* CAD/IVD BP Control  
* Childhood Imm  
* Colo Cancer Screen  
* DM A1c < 8.0  
* DM A1c <= 9.0  
* DM BP Control  
* DM Eye Exam  
* DM Nephropathy  
* Fall Risk Management  
* HTN BP Control  
* Lead Screen  

**Additional IPP/AQUA Measures Enabled in QA**  

* AMM Acute  
* AMM Continuation  
* Asthma Med Dispensing  
* Asthma Med Rx Management  
* CAD IVD Statin Rx Coverage  
* CAD Statin Dispensing Coverage  
* DM ACE/ARB Dispensing Coverage  
* DM Statin Dispensing Coverage  
* DM Statin Rx Coverage  
* DM/HTN ACE/ARB Prescribed  
* Follow Up ADHD Med Continue  
* Follow Up ADHD Med Initiate  
* Medication Reconciliation  
* Urinary Incontinence  

##Customization 

###Patient List  

Procedure on Git: [dbo.PopulatePatientLists](https://github.com/arcadia/qdw-excellus/blob/master/Database/Warehouse/Schema%20Objects/Schemas/rpt/Programmability/PopulatePatientLists.sql) 

The stored procedure generates two different types of patients lists for all sites active in the environment: Contracted Provider List with Active Patients and Active Excellus Member List.  

**Contracted Provider List Specification**  

* Only include persons who are functionally assigned to a provider participating in the program or functionally assigned to 'unassigned provider'. (This provider list is currently manually maintained in the sproc, but we are building a connector to automate this in the future)
* Only include patients with a pat_status = 'active'
* Exclude any persons associated with a patient who has a death date in any clinical source

**Active Excellus Member List List Specification**  

Same requirements as Contracted Provider List plus:  

* Only include persons who have an active match between mpi.person_patient mpi.person_member
* Exclude any persons whose most recent memeber eligibliity end date is older than 45 days

**User Management**  

Currently all patient lists have to be assigned to users manually, though if the patient list is shared with the user admin for a given organization that user can disseminate to the remaining users in their group.  The planned future state is to automatically assign patient lists to users based on each user's location configureation.

###Excellus Member ID Custom Step  	

This custom step is inserted before the scrub step in the nightly job and is necessary because member IDs from Excellus can change from month to month.  Check out the links below for an indepth look at that process.

Procedure on Git: [ExcellusMemberIDStep](https://github.com/arcadia/qdw-excellus/blob/master/Build/NantPostDeployScripts/Warehouse/ExcellusMemberIDStep.sql)   
Design document on Box: [Excellus Member ID Design Prosposal](https://arcadia.box.com/s/s1bxizdq2v4fclileo7r)  

###Measure Weights and Thresholds for IPP/ACQA Measures

The measure thresholds for all IPP/ACQA measures are given to us by Excellus and need to be configured within the product for each calendar year.  The thresholds are used universally for all practices and they are configured in this [script](https://github.com/arcadia/qdw-excellus/blob/master/Database/Warehouse/Scripts/SeedData/Measure_Thresholds.sql).

On the other hand, measure weights are practice specific and are the result of a negotiation between Excellus and the practices.  An example of a measure weight script can be found [here](https://github.com/arcadia/qdw-excellus/blob/master/Database/Warehouse/Scripts/SeedData/Measure_Weights_BAST.sql).  

However, there are instances, such as AHP, where all groups under a parent location have the same measure weights and in these instances one script can be used to assign measure weights to all those groups simliar to [this](https://github.com/arcadia/qdw-excellus/blob/master/Database/Warehouse/Scripts/SeedData/Measure_Weights_AHPCommunity.sql) example.

###Member Eligibility Lag  

Due to the fact that the claims feed from Excellus is a monthly feed, the member eligiblity lag is configured to 2 months in order to allow Excellus users to view data for their members in the portal.  This configuration is done in the post-deployment script which can be found [here](https://github.com/arcadia/qdw-excellus/blob/master/Database/Warehouse/Scripts/Post-Deployment/Script.PostDeployment.sql).  

##External Links
###Jira Issues
* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20XCLS)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(XCLS)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(xcls)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(xcls)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(xcls)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(xcls)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(xcls)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(xcls)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-Excellus) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/XCLS)
* [Deployment History](https://labs.arcadiaanalytics.com/monitoring_framework/#vhistory)

