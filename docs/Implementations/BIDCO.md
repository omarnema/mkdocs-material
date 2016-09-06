Status: Internal-Only
Author: Author;
CreateDate: 2015-12-16
ModifyDate: 2016-05-31

# Beth Israel Deaconess Care Organization

## Sections:
* [Client Details](#client-details)
* [Overview](#overview)
* [Inbound Data Sources](#inbound-data-sources)
* [Outbound Data Sources](#outbound-data-sources)
* [External Links](#external-links)
* [Out of Scope](#out-of-scope)

##Client Details
####Client Name
Beth Israel Deaconess Care Organization

####Client Density Area
Northeast

####Client Acronym
BIDCO, BIDCOUI

####Client Contract IDs
TBD

##Overview

Beginning around 2014, BIDCO started using our product principally as a data aggregation/warehouse platform in order to generate CCDs. They were not using the front end of the product, so measures/reports did not need to be calculated. 

In 2016, BIDCO signed a contract to enable the full analytics product, including the front end and HCC Navigator, in addition to the ongoing CCD generation process.  Because of the two different parallel purposes that our platform needs to accomplish and because there are concerns around CCD dependencies (seed destinations), and more importantly around different processing requirements and challenges, we decided to split into two separate environments and git repositories:  

|Purpose|Connectors|Git Repo|Database Naming Convention|  
|-----|------|------|------|
|CCD Generation| Hosted eCWs + CHCs | qdw-bidco | BIDCO_*_PRD |
|Analytics Front End/HCC Nav.| Above + Claims and more clinical feeds| qdw-bidcoui | BIDCOUI_*_PRD |  
 

###Implementation Strategy for Front End Functionality  

From a high level, the process for implementing front end functionality ("BIDCOUI") is:  

1. **Pilot Practice** (SSIM):  
    * Re-evaluate and update seed data for pilot hosted eCW practice. 
    * Run historical extract and load into DEV.
    * Run DQA on this practice to determine what query changes are needed to bring this and by extension all other eCW connectors up to the required level of data quality for front end functionality. 
    * Add ProgressNote query.
2. Somewhat in parallel with (1), **Initial Claims Connector Builds**
    * BIBCBS, BICCLF
    * All seeds go into qdw-bidcoui. Data are loaded into BIDCOUI environments.
3. **Changes to All Other BIDCO eCW sites** 
    * Apply any query changes identified in (1) + new ProgressNote query
    * Do a full re-seeding for all practices. 
    * All seeds should come from a consolidated list. 
    * Includes eCW CHCs
4. **Additional Connectors** (Timeline TBD)
    * Updates to NextGen/non-MySQL eCW CHCs (JSCHC, JORHOS)
    * Additional Claims Connectors (HPHC, TMP, TMP, United)
    * Additional Clinical Connectors (MAeHC)

###Description
Not yet completed. 

###Location
Massachusetts 

###Other Details


###Front-end URLs
* [QA Front-End](https://BIDCOwebtst01.arcadiahosted.local/) 
* [UAT Front-End](https://BIDCOtest.arcadiaanalytics.com/) 
* [PROD Front-End](https://BIDCO.arcadiaanalytics.com/)


###Contacts  

##Inbound Data Sources

###Claims 

* [CCLF - BICCLF](./Sources/BICCLF.md)
* [Blue Cross Blue Shield - BIBCBS](./Sources/BIBCBS.md)
* [Tufts Commercial - BITUFTS](./Sources/BITUFTS.md)
* [Tufts Medicare - BITMPMA](./Sources/BITMPMA.md)
* Harvard Pilgrim - BIHPHC
* United - BIUNITED


###Clinical

* [(Steinberg) Allergy & Asthma Center of MA  - AAM](./Sources/AAM/index.html) 

* [APG-Blue Hills (Current)  - ABH](./Sources/ABH/index.html) 

* [LGH Autumn Grace (Chih Yeh)  - AGM](./Sources/AGM/index.html) 

* [LGH Andover OB/Gyn  - AOB](./Sources/AOB/index.html) 

* [APG-Sharon  - APGS](./Sources/APGS/index.html) 

* [APG-Ashur  - ASH](./Sources/ASH/index.html) 

* [LGH Andover Surgical  - ASU](./Sources/ASU/index.html) 

* [Boston OB/Gyn  - BAK](./Sources/BAK/index.html) 

* [Barrett  - BAR](./Sources/BAR/index.html) 

* [APG-Family Medicine Center of Needham (BASSLER)  - BASS](./Sources/BASS/index.html) 

* [Izzy & Gomolin  - BCA](./Sources/BCA/index.html) 

* [Biber  - BIB](./Sources/BIB/index.html) 

* [Boston MFM  - BMFM](./Sources/BMFM/index.html) 

* [Community Physicians Associates (CPA)  - CAK](./Sources/CAK/index.html) 

* [Dimock CHC - DCHC](./Sources/DCHC/index.html) 

* [APG-Dedham/Westwood  - DEWD](./Sources/DEWD/index.html) 

* [Dhillon  - DHI](./Sources/DHI/index.html) 

* [Digestive Health  - DHS](./Sources/DHS/index.html) 

* [Diane London MD  - DIA](./Sources/DIA/index.html) 

* [Dye  - DYE](./Sources/DYE/index.html) 

* [Edalji & Komer  - EKO](./Sources/EKO/index.html) 

* [LGH Essex Medical Associated  - EMA](./Sources/EMA/index.html) 

* [Family Care Associates  - FCA](./Sources/FCA/index.html) 

* [Dana Fugelso  - FUG](./Sources/FUG/index.html) 

* [APG-Medfield  - GAR](./Sources/GAR/index.html) 

* [Gastroenterology Consultants of Greater Lowell  - GCL](./Sources/GCL/index.html) 

* [LGH Michael/Josef Gendlerman  - GEN](./Sources/GEN/index.html) 

* [LGH Joan Gitlin  - GIT](./Sources/GIT/index.html) 

* [LGH Michael Gogjian  - GOG](./Sources/GOG/index.html) 

* [BIDCO72 Group as a source - GR-BIDCO72](./Sources/GR-BIDCO72/index.html) 

* [Gregory Kechejian MD  - GRK](./Sources/GRK/index.html) 

* [LGH Michael Grossman  - GRO](./Sources/GRO/index.html) 

* [Tracy Harris  - HAR](./Sources/HAR/index.html) 

* [Hebrew Senior Life - HEBREW](./Sources/HEBREW/index.html) 

* [Greater Boston Internal Medicine/Agostino Iarrobino  - IAR](./Sources/IAR/index.html) 

* [Jeff Silver MD  - JES](./Sources/JES/index.html) 

* [John Markis MD  - JOM](./Sources/JOM/index.html) 

* [Jose Ruano, MD  - JOR](./Sources/JOR/index.html) 

* [Jordan Hospital - JORHOS](./Sources/JORHOS/index.html) 

* [Joseph Smith CHC - JSCHC](./Sources/JSCHC/index.html) 

* [Fred Kantrowitz  - KAN](./Sources/KAN/index.html) 

* [LGH Kevin Berry  - KBE](./Sources/KBE/index.html) 

* [APG-Brian Kenny  - KEN](./Sources/KEN/index.html) 

* [LGH Lawrence Kidd  - KID](./Sources/KID/index.html) 

* [LGH Grace Kim  - KIM](./Sources/KIM/index.html) 

* [APG-Needham Heights  - KOG](./Sources/KOG/index.html) 

* [LGH Michael Landman  - LAN](./Sources/LAN/index.html) 

* [Lichter  - LIC](./Sources/LIC/index.html) 

* [Looney  - LOO](./Sources/LOO/index.html) 

* [Avrohm N. Melnick  - MEL](./Sources/MEL/index.html) 

* [Men's Health Boston  - MHB](./Sources/MHB/index.html) 

* [Michael  Berry Md  - MIB](./Sources/MIB/index.html) 

* [APG - Milton Group (Crown colony, ferante, vue)  - MIL](./Sources/MIL/index.html) 

* [Mowschenson  - MOW](./Sources/MOW/index.html) 

* [LGH Methuen Podiatry (Kline/Ryan)  - MPO](./Sources/MPO/index.html) 

* [Leo Lane - Merrimack Valley Medical  - MVM](./Sources/MVM/index.html) 

* [Vascular Surgeons  - MWM](./Sources/MWM/index.html) 

* [Meeks & Zilberfarb  - MZO](./Sources/MZO/index.html) 

* [New England Cardiology  - NEC](./Sources/NEC/index.html) 

* [Nina Carroll MD  - NIC](./Sources/NIC/index.html) 

* [Outer Cape CHC - OUTC](./Sources/OUTC/index.html) 

* [Randolph Medical Associates  - RMA](./Sources/RMA/index.html) 

* [LGH Ruhke Medial   - RMC](./Sources/RMC/index.html) 

* [LGH Riverside Nephrology/Eduardo Haddad  - RNP](./Sources/RNP/index.html) 

* [Scarlatelli / McLaughlin  - SCA](./Sources/SCA/index.html) 

* [South Cove CHC - SCHC](./Sources/SCHC/index.html) 

* [Shapiro  - SHP](./Sources/SHP/index.html) 

* [Solomon and Freedman  - SOF](./Sources/SOF/index.html) 

* [Song  - SON](./Sources/SON/index.html) 

* [S. Shore Internal Med  - SSIM](./Sources/SSIM/index.html) 

* [Stephan Cohen, MD  - STC](./Sources/STC/index.html) 

* [Cornerstone Medical Group (formerly Stern)  - STE](./Sources/STE/index.html) 

* [LGH Dr. Stupnytsi (Eagle Medicine Associates)  - STU](./Sources/STU/index.html) 

* [Stewart  - STW](./Sources/STW/index.html) 

* [APG-Tong  - TON](./Sources/TON/index.html) 

* [Urology practice Associates  - UPA](./Sources/UPA/index.html) 

* [APG-Upper Falls  - UPP](./Sources/UPP/index.html) 

* [William Goldberg MD  - WIG](./Sources/WIG/index.html) 

<<<<<<< HEAD
* [Pramila Yadav  - YAD](./Sources/YAD/index.html) 

* [BIDCO PayerName Extracts - ALL-PayerName](./Sources/ALL-PayerName/index.html) 

##Outbound Data Sources

The BIDCO instance has a custom component used to extract CCDs.

As of now, no concrete plans for outbound feeds from BIDCOUI environment.

##Out of Scope

##Configurations

###Measures/Periods

Only ACO and HEDIS initiatives. Requesting list of measures within those or all. 

###Reports

TBD - waiting on more info from Client Partner.

###Additional Scope:  

HCC Navigator is required.

 
##Customization 

To allow data to flow to the CCDs, the original seeds contained a large number of 1-to-1 mappings. These never went through the standard clinical review process. 

All data sources should have identical configuration in terms of the Informatica templates and parameters being used. 

##External Links

* [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=labels%20%3D%20BIDCO)
* [Client-Reported Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20%22Client%20Reported%20Indicator%22%20%3D%20Yes%20AND%20status%20NOT%20IN%20(Closed))
* [Known Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20resolution%20IN%20(%22Known%20Issue%22))
* [Priority Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20%22Calculated%20Priority%22%20%3C%205%20AND%20status%20NOT%20IN%20(Closed))
* [Unresolved Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20status%20NOT%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22%2C%20Closed))
* [Resolved Issues Awaiting Deployment](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20status%20IN%20(Resolved%2C%20Complete%2C%20%22Deploy%20to%20DEV%22%2C%20%22Deploy%20to%20QA%22%2C%20%22Deploy%20to%20UAT%22%2C%20%22Deploy%20to%20PROD%22%2C%20%22Validate%20in%20DEV%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20QA%22%2C%20%22Validate%20in%20UAT%22%2C%20%22Validate%20in%20PROD%22))
* [Open Issues](https://jira.arcadiasolutions.com/issues/?jql=%20%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20status%20NOT%20IN%20(Closed))
* [On Hold Issues](https://jira.arcadiasolutions.com/issues/?jql=%22Impacted%20Data%20Sources%22%20IN%20(BIDCO)%20AND%20status%20IN%20(%22On%20Hold%22%2C%20%22On%20Hold-External%22%2C%20%22On%20Hold-Internal%22)%20)
* [Repo on Github](https://github.com/arcadia/qdw-BIDCO) 
* [BOX - SoW](https://arcadia.app.box.com/files/0/f/1570839907/BIDCO)
* Link [Deployment History]

##Attachments
* Put Releveant Attachments Here

