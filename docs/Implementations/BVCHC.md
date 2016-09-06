Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-07-28
ModifyDate: 2016-07-28

# Blackstone Valley CHC 

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Blackstone Valley CHC 

####Client Density Area
Northeast

####Client Acronym
BVCHC

##Overview

[About BVCHC](http://www.blackstonechc.org/pages/view/2/About-BVCHC)


###Location
Rhode Island

###Other Details

All infrastructure will be build in AWS. 

###Front-end URLs
* [QA Front-End](https://bvchcwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https:/bvchctest.arcadiaanalytics.com/) 
* [PROD Front-End](https://bvchc.arcadiaanalytics.com/)


###Contacts  

##Inbound Data Sources

###Claims


* [Neighborhood Health Plan of Rhode Island - NHPRI](./Sources/NHPRI.md)

###Clinical

* [NextGen EHR - BVCHCNG](./Sources/BVCHCNG.md)


##Outbound Data Sources

None at this time. 

##Out of Scope

HCC Navigator.

##Configurations
* Measures/Initiatives:
    * ACO
    * HEDIS
* Reports:
    * ED Utilization
    * MEM
    * Patient Registries
    * SPR
    * Care Management Tools
* Periods Processed
	* Standard configuration

 
##Customization 

No known customizations.

##External Links

###Box Links  

* [SOW](https://arcadia.box.com/s/i1batfuya2lo1bd3b6pyvelubwnel29m)
* [Client questionnaires, including the connectivity doc](https://arcadia.box.com/s/v6hf873pk6s7jxbsnnjkbu3htlvtul6j)
* [Project plan](https://arcadia.box.com/s/whieqq8ml5oyb4ebqyqwmm8t83lcu822)

###Jira Issues
* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20BVCHC)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BVCHC)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-VCA) 
* [BOX - SoW](https://arcadia.box.com/s/wd9pq9ege3px1o61pdvd09xjdc27aro7)




