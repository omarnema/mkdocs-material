Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-06-08
ModifyDate: 2016-06-08


#VCA Aetna JV/eACO Requirements

Two new products are being sent to the same SFTP/Prestaging as Aetna, JV and eACO. There are specific requirements that we be able to control access to the data being sent for those products (specifically eACO).  

Different feeds can be identified by the `org_cd` or `org_id` value in the prestaging tables. The org codes are a combination of the pod (e.g. WCHN) and the product (EE for eACO, CT2 for JV, and FI or SI for commercial).  

A change to uspUpsert in DEV prestaging has already been made to add an `org_id_scrubbed` column to enrollment and rx tables since in those tables, the org code is concatenated with other values in a shared, fixed-width field. The other tables already have the org_id in its own column.

##Org Code - Business Entity - ID Map  


|Org Code|Business Entity|Center ID|Plan Source ID|  
|-----|-----|-----|-----|  
|CT2_GRF_FI|Griffin JV|40|2|
|CT2_GRF_SI|Griffin JV|40|2|
|CT2_MDS_FI|Middlesex JV|41|2|
|CT2_MDS_SI|Middlesex JV|41|2|
|CT2_SVM_FI|SVMC JV|42|2|
|CT2_SVM_SI|SVMC JV|42|2|
|CT2_WCH_FI|WCHN JV|43|2|
|CT2_WCH_SI|WCHN JV|43|2|
|GRIFF_EE|Griffin eACO|44|3|
|MDSX_EE|Middlesex eACO|45|4|
|WCHN_EE|WCHN eACO|46|5|
|GRIFF_FI|Griffin Commercial|9|1|
|GRIFF_SI|Griffin Commercial|9|1|
|LM_FI|L&M Commercial|10|1|
|LM_SI|L&M Commercial|10|1|
|MDSX_FI|Middlesex Commercial|11|1|
|MDSX_SI|Middlesex Commercial|11|1|
|SVMC_FI|SVMC Commercial|12|1|
|SVMC_SI|SVMC Commercial|12|1|
|WCHN_FI|WCHN Commercial|13|1|
|WCHN_SI|WCHN Commercial|13|1|  


##AETNA  

The current clinical (VAETNCLN) connector queries join to the `PodSourceXWalk` table to get the `center_id` value for the queries. That list needs to be updated to (1) include the new org code values and (2) consolidate by removing the "unscrubbed" org code values (since we now have available a scrubbed version in all tables).

In addition, we need to update all plan queries to join to that table and get the plan source ID. Currently they all use the ?DBID? parameter, which is set to 1.  Given it is plan, we need to make sure this is a varchar value and that it matches what is currently being used for Aetna. Because we are creating new source IDs, we will need new seed data, though it will most likely match what is done for Aetna. 

##VAETNCLN  

After doing this, we will need to register each of the new clinical sites and create a top level location. We will then need to create other location seeds matching those used by VAETNCLN ([Example](https://github.com/arcadia/qdw-vca/blob/master/Database/Warehouse/Scripts/SeedData/2_VAETNCLN_WAREHOUSE.sql)).  This will also require new staging seeds ([Example](https://github.com/arcadia/qdw-vca/blob/master/Database/Staging/Scripts/SeedData/2_VAETNCLN_STAGING.sql)). Most likely these will be the same as those of Aetna CLinical, but we should review them anyway.




