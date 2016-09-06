Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-02-18
ModifyDate: 2016-02-18

#LHCQF ED Registry Onboarding Process

Our contract with LHCQF for the ED Registry project requires us to be able to turn around new connectors in a matter of days. We must have the data in UAT so that they can validate in their replica instance before moving immediately to production. 

Each new data provider should be generating files that match this [specification](#). As a result, our prestaging databases, configuration, and load, and our extract queries should be **identical** across all implementations. **Any discrepancies in the file causing errors in the ETL should be escalated to the IL and fixed by the submitter.**

To get ahead of the process and avoid the scramble of infrastructure requests, these instances may be pre-configured as generic "LAED" connectors. This can be confusing from an Informatica/labelling perspective, but it allows us to just plug in a file when we have a new file submitter and test its ability to be processes. 

Because all feeds are identical, the process for onboarding is as follows:

Prior to receiving data:  
 
1. Ensure environment build is complete
2. Deploy prestaging DB
3. Create prestaging loads (dev + prd)
4. Create connector for DEV
5. Run connector end to end with no data to confirm everything is functioning
6. Create initial Release for connector 
7. Deploy connector to UAT and PRD  

  
*Note*: This will allow us to immediately move forward with the rest of the build once we have the actual files

Once 1-7 have been completed, if we still do not have data, place the tickets back on hold.  
  
After receiving data, the process for bringing the new submitter on will be: 

1. Inspect file: validate that columns are correct and that file can be loaded successfully to dev prestaging.
2. Change request & load to prestaging PRD
3. Test ETL in DEV once
4. Generate location seeds, commit to client repo.
5. Change notification, client deploy to UAT, and run UAT connector. (Not sure right now who owns this) 
6. Communicate to LHCQF that the file has been loaded to UAT
7. Once LHCQF has validated the data, product support will manage deploy to PRD


