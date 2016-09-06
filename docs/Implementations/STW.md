Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2015-12-16
ModifyDate: 2016-06-17

<<<<<<< HEAD
# Steward (STW)

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name

Steward Healthcare Network

####Client Density Area
Massachusetts

####Client Acronym
STW

####Client Contract IDs
Client Contacts


##Overview


###Description
Description of Steward  

###Location  
Massachusetts  

###Other Details  

**IMPLEMENTATION ROUND 1: Steward Migration Notes**:   

* *Scope of project is to Migrate Steward's instance of QDW from 3.x hosted in the Steward Network to 4.x hosted at Arcadia*  
* **OVERALL MIGRATION STRATEGY**:  
    * To migrate connectors, the plan is to convert DRVS queries to Informatica, but make no changes beyond that scope. The goal is to have data match what is in 3.x, not to improve its accuracy.   
    * We should not be making major fixes to these queries. If the defect is the result of a bad transaltion from DRVS query to Informatica, it should be fixed. Otherwise, the goal is to exactly match what is in 3.x.  
    * In addition, we will be performing a migration of 3.x data to 4.x to back fill any missing data that we can no longer capture through our connectors.   
* **Seed data**: Some values were removed due to new constraints introduced 4.x. Otherwise, the seeds should not have changed between 3.x and 4.x. There was no clinical review of these seeds, not will there be unless at a later date Steward decides to pay for full product functionality.   
* Issues w/ Row Counts   
    * A number of queries are unable to capture full time data because it either no longer exists in the eCW DBs or because our queries exclude certain records and the records no longer meet the criteria for inclusion.    
    * This is more relevant in CPN1 than PrimaCARE, since CPN1 has had a connector running for 5 (?) years, and PrimaCARE just came online last year  
    * For connector handoff, I handled this by looking only at more recently loaded data    
        * For some queries, full historical data is pulled every weeknight  
        * For the rest, full historical extracts run once per week  
    * Queries used for handoff testing: [4.x Row Counts](https://arcadia.box.com/s/n957leo4qc52wbhy7tgvqqoyfbs2xfux), [3.x Row Counts](https://arcadia.box.com/s/ldbm55cn8x8tgs0140j0dxq43w7tm63e).   
* Most other issues should be explainable by either data model changes or scrub/warehouse load changes (e.g. scrubbing order type, which was introduced post 4.0)  
* The ultimate goal of the migration is to reproduce an extract that we are currently sending from 3.x to Athena.  
    * In 3.x, these are in stored procedures, all starting with "uspHDS..."  
    * In 4.x, these are in views in warehouse, all starting with "v_HDS..."  
    * If a field does not impact any of these views, we do not need to worry about fixing it. It should be documented and communicated to Phil/Max/Steve Copans, but doesn't necessarily have to be fixed  
* Other causes of issues may be artifacts of the old queries we are using
    * E.g. a number of queries, esp. maintenance, may produce duplicate rows. Scrubbing will essentially pick one of those at random  
    * Many of the queries use the current datetime as create/modify timestamp or even as the relevant datetime field in QDw (e.g. maintenance completed date), so we expect those to be different between 3.x and 4.x  
    * As mentioned above, some of the queries explicity exclude certain rows from the extract, so that can impact the data we have an cause mismatches.   
* **Access to 3.x Environment**  
    * 3.x production instance:  
        * Server: SHCCSQLP01MI2\sql12  
        * DB Names: QDW_<Staging/Warehouse>_Prod  
    * There is also a replica that has been restored on qdwsqlqa03.  
    * **Data sources**:  
        * CPN1 is on MySQL, and can be accessed through MySQL Workbench, which is installed on most Steward servers, e.g. shcarcadia105. PrimaCARE is on SQL Server (shcecwdbp01v).  
        * Access credentials for all data sources on [Box](https://arcadia.box.com/s/pgejoftb0mvzbfzmz263owqcbi3brg8x)  
        * These each have a custom workflow, but the DEV/QA task flows have already been updated to reflect that. More documentation on this available [here](./Sources/STW-Custom-SFTP-Workflow.md).  
    * 3.x Queries at Steward are in the following location: \\\\shcidssis101\QDW\Connector_PROD\Config\Queries\Base\



**IMPLEMENTATION ROUND 2: HCC Navigator Notes**:     

* Two new grouping constructs have been created to roll out eCW connector query changes: GR-STWMySQL and GR-STWMSSQL. These are used to track the implementation of eCW query changes validated for the pilot practices to all MySQL and SQL Server eCW practices. These will also be used for round 3, which will involve enabling the front end. *The documentation of these changes have been captured on the page for the broader [GR-STWMIG](./Sources/GR-STWMIG.md) group.*  
* Query changes here are limited to those needed to make sure HCC navigator and MPI work well.  
  

###Front-end URLs

* Front end will be added in Implementation Round 3. 


###Contacts  

##Inbound Data Sources  

###Clinical

* [Steward Hosted eCW Sources (Group) - GR-STWMIG](../Implementations/Sources/GR-STWMIG/index.html) 
    * Pilot: [Carney Pulmonary - CPN1](../Implementations/Sources/CPN1/index.html) 
    * Pilot: [Prima CARE - PRIMACARE](../Implementations/Sources/PRIMACARE/index.html)   
* Steward Black Box Connectors:  
    * [NBPT Medical Associates - NEWMA](../Implementations/Sources/NEWMA.md)
    * [NBPT Family Practice - NEWFP](../Implementations/Sources/NEWFP.md)  
    * [Children's Health Care - CHIHC](../Implementations/Sources/CHIHC.md)  
    * [Emerald Physicians - EMRLDPHYS](../Implementations/Sources/EMRLDPHYS.md)  

###Claims

* [Steward Consolidated Claims Feed - STWCLM](./Sources/STWCLM.md)


##Outbound Data Sources

###Athena HDS Extract (Legacy Version - Still in Place from 4.x)
* [OF-STWHDS](../~Implementations/~Sources/OF-STWHDS/index.html) . Views are direct conversions of stored procedures from 3.x environment. 
    - For reference, code for 3.x views on [GitHub](https://github.com/arcadia/qdw-steward/tree/3.x/Database/Warehouse/Schema%20Objects/Schemas/dbo/Programmability/Stored%20Procedures)

###"4.x" Data Warehouse Feeds  
* [OF-STWDW](../~Implementations/~Sources/OF-STWDW.md)
* [OF-STWATHENA](../~Implementations/~Sources/OF-STWATHENA.md)

##Out of Scope
All of the front end features, measures, etc. available in 4.x. 

##Configurations
* **1. Migration:** No Measures/Reports are needed, as Steward is strictly using the product for data aggregation/warehousing and to provide an extract to Athena at this time.   

* **2. HCC Navigator** For the second implementation round, the front end will not be enabled, only the HCC Navigator, which has a separate URL. 

 
##Customization 
* HDS Extract views on [GitHub](https://github.com/arcadia/qdw-steward/tree/master/Database/Warehouse/Schema%20Objects/Schemas/dbo/Views) 


##External Links

* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20STW)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(STW)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-steward) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/STW)


##Attachments

