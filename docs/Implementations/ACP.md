Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2015-12-16
ModifyDate: 2016-02-12



# Arizona Community Physicians

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Arizona Community Physicians

####Client Density Area
Soutwest

####Client Acronym
ACP

####Client Contract IDs


##Overview


###Description
ACP is an Arizona IPA using our analytics platform for population health management.  

###Location
Headquartered in Tucson, AZ

###Other Details


###Front-end URLs
* [QA Front-End](https://ACPwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://ACPtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://ACP.arcadiaanalytics.com/)


###Contacts  


##Inbound Data Sources

###Clinical
* [Arizona Community Physicians Clinical Data - ACPCLN](../~Implementations/~Sources/ACPCLN/index.html) 
* [Arizona Community Physicians IDX - ACPIDX](../~Implementations/~Sources/ACPIDX/index.html) 
* [Arizona Community Physicians - Discharge Report - ACPDISCH](../~Implementations/~Sources/ACPDISCH/index.html) 


###Claims

* [Arizona Community Physicians - United Health Plan ? Shared Risk - ACPUHP](../Implementations/Sources/ACPUHP/index.html) 
* [Arizona Community Physicians - Blue Cross Blue Shield Shared Risk - ACPBCBS](../Implementations/Sources/ACPBCBS/index.html) 
* [Arizona Community Physicians - Cigna - ACPCIG](../Implementations/Sources/ACPCIG/index.html) 
* [Arizona Community Physicians - Cigna Medicare - ACPCMA](../Implementations/Sources/ACPCMA/index.html)
* [Arizona Community Physicians - Humana Shared Risk - ACPHSR](../Implementations/Sources/ACPHSR/index.html) 
* [Arizona Community Physicians Centers for Medicare and Medicaid Services Medicare Shared Savings Prog - ACPCCLF](../Implementations/Sources/ACPCCLF/index.html) 

##Outbound Data Sources

We are supposed to be shipping them a replica of the prod database on a nightly basis per the contract. Strategy and ownership of that process is TBD. 

##Out of Scope


##Configurations

###Measures/Initiatives:  
- All ACO 
- All HEDIS

* Periods Processed
	* Historic/Onetime
	* Weekly
	* Nightly

 
##Customization 
* HCC Navigator is covered in SOW.  

##External Links

* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=component%20%3D%20ACP%20or%20labels%20%3D%20ACP)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(ACP)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-ACP) 
* [SOW](https://arcadia.box.com/s/agru1omvun9pw6yjsgcbe10pdcadis2q)
* [Known Issue Trackers](https://arcadia.box.com/s/gzvtivpdd3r8ikys6f689qv74xu8wozv)


