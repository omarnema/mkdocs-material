Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2015-12-16
ModifyDate: 2016-02-12

# Value Care Alliance

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Value Care Alliance

####Client Density Area
Client Density Area

####Client Acronym
VCA

####Client Contract IDs
Client Contacts


##Overview


###Description
Description of Value Care Alliance
###Location
Location of Value Care Alliance
###Other Details
Other  details
###Front-end URLs
* [QA Front-End](https://VCAwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://VCAtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://VCA.arcadiaanalytics.com/)


###Contacts  

##Inbound Data Sources
###Claims

* [VCA - Aetna_eACO - Claims - VAETEACO](../Implementations/Sources/VAETEACO/index.html) 

* [VCA - Aetna_JV - Claims - VAETJV](../Implementations/Sources/VAETJV/index.html) 
* [VCA - Connecticare (Legacy) - Claims - VLGYCNTCR](../Implementations/Sources/VLGYCNTCR/index.html) 
* [VCA - Aetna_Norwalk - Claims - VLGYAETNW](../Implementations/Sources/VLGYAETNW/index.html) 

* [Western Connecticut Health Network- Claims and Claims Line Feed - WCHNCCLF](../Implementations/Sources/WCHNCCLF/index.html) 

* [VCA CCLFs - VCAMSSP](../Implementations/Sources/VCAMSSP/index.html)  
* [Aetna Inc. - AETNA](../Implementations/Sources/AETNA/index.html) 

###Clinical

* [VCA - Aetna_eACO - Clinical - VAETEACOCLN](../Implementations/Sources/VAETEACOCLN/index.html) 
* [VCA - Aetna_JV - Clinical - VAETJVCLN](../Implementations/Sources/VAETJVCLN/index.html) 
* [VCA - ConnectiCare_Legacy - VLGYCNTCR](../Implementations/Sources/VLGYCNTCR/index.html) 
* [VCA Aetna Clinical - VAETNCLN](../Implementations/Sources/VAETNCLN/index.html) 
* [VCA - eACO_Rx - VCVS](../Implementations/Sources/VCVS/index.html) 
* [VCA - Aetna_Norwalk - Clinical - VLGYAETNWCLN](../Implementations/Sources/VLGYAETNWCLN/index.html) 
* [VCA - Anthem_Legacy - VLGYANTM](../Implementations/Sources/VLGYANTM/index.html) 

####Western Connecticut (Shared Environment)
Currently, WCHN and VCA use a shared environment, so the client label for many of these data sources, especially in Informatica, is "VCA". However, they are two distinct customers and should be treated as such. 

If a connector appears to be missing from this list, check [WCHN](./WCHN.md).

**Update** WCHN now has its own set of environments, but still uses the qdw-vca git repo, as there is a potential to merge the environments together in the future. 




##Outbound Data Sources
###Report Name
* Details

###Report Name 
* Details


##Out of Scope
Out of scope

##Configurations
* Initiatives:
    * MSSP (ACO)
    * Aetna ACO
    * HEDIS
* Periods Processed
    * Standard configuration

 
##Customization 
* MPI Customizations

##External Links

* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20VCA)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(VCA)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-VCA) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/VCA)
* Link [Deployment History]

##Attachments
* Put Releveant Attachments Here

