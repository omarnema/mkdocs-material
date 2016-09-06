Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2015-12-16
ModifyDate: 2016-03-08

# Louisiana Healthcare Quality Forum

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details

####Client Name
Louisiana Healthcare Quality Forum

####Client Density Area
Southeast

####Client Acronym
LHCQF

####Client Contract IDs





##Overview

###Description
Most of LHCQF's current contracts involve expansion of either the data sources we take in or the files we generate for the following programs.  


Additionally, LHCQF receives outbound files every morning by 10AM EST that reports on encounters for individuals that are deemed eligible from the eligibliity sources. These outbound files leverage a view from the warehouse and restricts dat based upon a particular plan name.


Specifics about these particular feeds are outlined in their relevant data source link. 

All prestaging databases are found on the production server, LHCQFSQLPRD02.


###Location
Louisiana

###Other Details


###Front-end URLs
* [QA Front-End](https://LHCQFwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://LHCQFtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://laedie.lhcqf.org/)

###Back-end Servers
* DEV - QDWSQLDEV02
* QA - QDWSQLQA03
* UAT - QDWSQLQA02
* PRD - LHCQFSQLPRD02


###Contacts  

##Inbound Data Sources

###Claims
* [LHCQF Molina Medicaid Eligibility - LAMOELG](../~Implementations/~Sources/LAMOELG/index.html) 
* [Group Louisiana Eligibility - GR-LAELIG](../~Implementations/~Sources/GR-LAELIG/index.html) (Retired)  


###Clinical


##Inbound Data Sources

###Claims
* [LHCQF Molina Medicaid Eligibility - (LAMOELG)](./Sources/LAMOELG/index.html) 
* [LHCQF LSU Eligibility - (LALSU)](./Sources/LALSU/index.html)
* [LHCQF Adelade Eligibility - (LaDADE)](./Sources/LADADE/index.html)
* [Group Louisiana Eligibility - (GR-LAELIG)](./Sources/GR-LAELIG/index.html) (Retired)  


###Clinical


* [ORION Data Feed - (LAORION)](./Sources/LAORION.md)

* ED Registry Program (see [onboarding process](./Sources/LHCQF-ED-Registry-Onboarding.md))
    * [Group Louisiana Emergency Departments - (GR-LAED)](./Sources/GR-LAED/index.html) 
    * [Louisiana Heart Hospital - (LAHH)](./Sources/LAHH.md)
    * [Slidell Memorial Hospital - (LASMHED)](./Sources/LASMHED.md)
    * [Ochsner Health System - (OCHSNERED)](./Sources/OCHSNERED.md)
    * [LARMC](./Sources/LARMC.md) | No Data Currently
    * [LAPATH](./Sources/LAPATH.md) | No Data Currently
    * [LASCMH](./Sources/LASCMH.md) | No Data Currently
    * [LHCQF Riverland Medical Center - (LARMC)](./Sources/LARMC.md) | No Data Currently
    * [Louisiana Orion ED - LAORIED](./Sources/LAORIED/index.html) (Retired) | No Data Currently


* Healthy Baton Rouge Sources:
    * [Franciscian Missionaries of Our Lady Health System, QDW 4.X - FMOLOL](./Sources/FMOLOL/index.html) 
    * [Ochsner Medical Center - OCHSNER](./Sources/OCHSNER/index.html) 
    * [Baton Rouge General Medical Center - BATMC](./Sources/BATMC/index.html) | No Data Currently

###Outbound Data Sources

* [Louisiana DHH - OF-LADHH](./Sources/OF-LADHH/index.html) 
* [Louisiana Aetna - OF-LAAETNA](./Sources/OF-LAAETNA/index.html) 
* [Louisiana AmeriHealth - OF-LAAMH](./Sources/OF-LAAMH/index.html) 
* [Louisiana AmeriGroup - OF-LAAMG](./Sources/OF-LAAMG/index.html) 
* [Louisiana LALSU - OF-LALSU](./Sources/OF-LALSU/index.html) 
* [Louisiana LaDADE - OF-LADADE](./Sources/OF-LADADE/index.html) 
* [Louisiana LHC - OF-LALHC](./Sources/OF-LALHC/index.html) | No Data Currently
* [Louisiana United - OF-LAUNIT](./Sources/OF-LAUNIT/index.html) | No Data Currently


##Out of Scope
Measure calculation and testing is not currently required. 

##Configurations
* Measure Calculation is not currently required
* Reports:
    * ED Detail
    * Utilization Detail
    * Visit Reports
    * Single Patient
 



##Customization 
The LaHIE (LAORION) data feed is entirely custom. Specifics about this data feed are highlighted in the relevant source link. In general, it includes - 
* Custom step in the QDW Nightly Job
* Seperate Nightly Job (LHCQF EXTRACT JOB) to run the SSIS package and generate the LAORION Extract

The ED Registry feed is used to generate Outbound feeds, and utilizes a view called rpt.EDRegistryOutboundUtilization.

LCHQF does have access to a replication database for the UAT and PROD database that gets refreshed daily at 3 AM. 


##Customization 
* Not yet documented


##External Links

* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20LHCQF)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(LHCQF)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-LHCQF) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/LHCQF)
* Link [Deployment History]

##Attachments
* Put Releveant Attachments Here

