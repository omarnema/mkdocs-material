Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2015-12-16
ModifyDate: 2016-02-12

<<<<<<< HEAD
 #Western Connecticut Health Network 

 Sections:
* [Client Details](client-details)
* [Overview](overview)
* [Inbound Data Sources](inbound-data-sources)
* [Outbound Data Sources](outbound-data-sources)
* [External Links](external-links)
* [Out of Scope](out-of-scope)

##Client Details

=======
# Western Connecticut Health Network 

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details

####Client Name
Western Connecticut Health Network 

####Client Density Area
Northeast

####Client Acronym
WCHN

####Client Contract IDs


##Overview

**Key Technical Note:** WCHN Code lives in the qdw-vca git repository. Originally, the two were intended to share infrastructure, so they used the same repo. However, due to time constraints in getting WCHN live on 4.10 with outreach enabled, they were split up. At this point there is no confirmed plan to merge the two data sets, though it is possible.


###Description
To be documented. 

###Location
Connecticut

###Other Details



###Front-end URLs
* [QA Front-End](https://VCAwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://VCAtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://VCA.arcadiaanalytics.com/)




###Inbound Data Sources

####Claims

* [Western Connecticut Health Network- Claims and Claims Line Feed - WCHNCCLF](../Implementations/Sources/WCHNCCLF/index.html) 
* [Western Connecticut Health Network - Anthem ACO - WCHNAACO](../Implementations/Sources/WCHNAACO/index.html) 
* [Western Connecticut Health Network - Anthem Employee Group - WCHNAEG](../Implementations/Sources/WCHNAEG/index.html) 
* [Western Connecticut Health Network - Employee Group - WCHNEMPG](../Implementations/Sources/WCHNEMPG/index.html) 
* [Western Connecticut Health Network - Aetna Medicare Advantage - WCHNAMA](../Implementations/Sources/WCHNAMA/index.html)  
* [Western Connecticut Health Network - ConnectiCare - WCHNCNTCR](../Implementations/Sources/WCHNCNTCR.md)  


####Clinical

* [Western Connecticut Health Network - Allscripts Touchworks - WCHNASTW](../Implementations/Sources/WCHNASTW/index.html) 
* [Western Connecticut Health Network- Cerner - WCHNCERN](../Implementations/Sources/WCHNCERN/index.html) 
* [Western Connecticut Health Network- NextGen - WCHNNXT](../Implementations/Sources/WCHNNXT/index.html) 
* [Western Connecticut Health Network - Associated Family Physicians - WCHNAFP](../Implementations/Sources/WCHNAFP/index.html) 
* [Western Connecticut Health Network - Dr. Blum - WCHNBLUM](../Implementations/Sources/WCHNBLUM/index.html) 
* [Western Connecticut Health Network - Danbury Medical Group - WCHNDANB](../Implementations/Sources/WCHNDANB/index.html) 
* * [Western Connecticut Health Network - Athena Practice Management - WCHNATHENA](../Implementations/Sources/WCHNATHENA/index.html) 
* [Western Connecticut Health Network - Dr. Anderson - WCHNAND](../Implementations/Sources/WCHNAND/index.html) 
* [Western Connecticut Health Network - Dr. Diaz - WCHNDIAZ](../Implementations/Sources/WCHNDIAZ/index.html) 
* [Western Connecticut Health Network- Greenway - WCHNGRN](../Implementations/Sources/WCHNGRN/index.html) 
* [Western Connecticut Health Network- McKesson - WCHNMCK](../Implementations/Sources/WCHNMCK/index.html) 

####Out of Scope



####Configurations


##Configurations

* Measures/Initiatives:
    * ACO
    * Aetna ACO (from VCA)
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

* See [GPRO Extract](../Implementations/Sources/OF-WCHNGPRO/index.html) for deatils on custom schema elements added for that extract. 
* HCC Navigator is covered in SOW.  Strategy/ownership TBD. 
* Data warehouse replica is covered in SOW. Strategy/ownership TBD. 

##External Links
###Jira Issues
* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20WCHN)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(WCHN)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-VCA) 
* [BOX - SoW](https://arcadia.box.com/s/wd9pq9ege3px1o61pdvd09xjdc27aro7)




