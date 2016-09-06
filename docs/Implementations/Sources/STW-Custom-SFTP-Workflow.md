Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-02-08
ModifyDate: 2016-02-08

#Steward Custom SFTP Workflow

For all Steward sources running through the agent on *shcifma01v*, due to security constraints at Steward, we are unable to connect directly from the Informatica agent server to the Arcadia SFTP server to transfer files.

Steward uses GlobalScape for file management and blocks outgoing traffic from all servers not on their DMZ, and their security team would not allow an exception for our use case unless we could prove that we could not use GlobalScape. 

As a result, we have put in place a custom workflow which allows for the greatest level of logging and traceability for file transfers within the confines of this restriction. Rather than directly moving the files from their server to *qdwsftp01* over SFTP, we place the files into a source-environment specific folder within E:\\SFTPQueue\\ using an Informatica task (e.g. `STW_CPN1_DEV_CLI_Move_All`). 

There are watch rules put in place by Derrick Smith at Steward to automatically move files from that location to the corresponding location on their SFTP server.  Once that move has taken place, we pull files from their SFTP server and place them on our SFTP server using another Informatica task (e.g. `STW_CPN1_DEV_CLI_SFTP_Get`). Before that happens, we check to make sure that the file move done by GlobalScape has completed by checking the contents of the folder in E:\\SFTPQueue\\. This is done by calling `E:\ArcadiaAnalytics\Scripts\WaitForGlobalScape.bat` once per task flow with the `_CLI_WaitFor_GlobalScape` task. 

Once that folder is empty (or when we hit a timeout period), the script terminates and we move on to the SFTP Get step of the job. 

The SFTP connectivity info is:  

* **Host:** 198.89.66.140
* **Port:** 22
* **Username:** eftarcadia02
* **Password:** on LastPass.