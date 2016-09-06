Status: Internal-Only
Author: Jeff Solomon
CreateDate: 2016-02-10
ModifyDate: 2016-02-10


#WCHNDANB (Western Connecticut Health Network - Danbury Medical Group)

**Client(s)**: [WCHN](../WCHN.md)  
**Density Area**: Northeast   

## Sections:
* [Overview](#overview-and-architecture)
* [Custom Configurations](#custom-configurations)
* [Operations](#operations)
* [Data Source](#data-source)
* [Known Issues](#known-issues)
* [External Documentation Links](#external-documents)

##Overview and Architecture

| Overview ||
|-----|-----|
| Data Source Name| **Western Connecticut Health Network - Danbury Medical Group** |
| Data Source Acronym| **WCHNDANB** |
| Type | **** |
| Site ID | **16** |
| Architecture Model | [**Client DB Extract (Prestaging)**](../../Tech_Delivery/Standard-Implementations/Client-DB-Extract-Prestaging.md)|
| Database hosting | **Arcadia Hosted** |


<a href="../../../img/Connector-Client-DB-Extract-Prestaging.png">![](../../img/Connector-Client-DB-Extract-Prestaging.png)</a>

###Database Connection Information  

|Database Connectivity||
|-----|-----|
|Type|MSSQL|
|Host|PRESTGSQLPRD01|
|Port|1433|
|Name|WCHNDANB_PRD_PRESTAGING|
|User Name|WCHNDANB_PRESTAGING_PRD|  


###Location Hierarchy Configuration

*Not documented at this time. Contact the Solution Architect for details.*

##Custom Configurations

This connector uses custom C# code ([GitHub](https://github.com/arcadia/informatica/tree/master/Danbury%20CTree%20Extract)) to extract data from a C-Tree Database into CSV files.  This currently has not been set up to run regularly on the client's system, so all we have is a data set from December 2015. 

##Data Source

Set of files extracted from the CTree DB as described above.  These files have the same (or almost the same) schema as the McKesson native databases, so the queries should be similar.  

Files loaded into prestaging for this source are:  


|Archrg99||
|-----|-----|
| Table Name | Archrg99|
| File Name Patterne | Archrg99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,GTID,N_Chrg,N_Chrg_Seq,OPID,D_Posting,D_ServiceFrom,D_ServiceTo,D_Pat_Billed,D_Ins_Billed,D_System,D_Last_Changed,N_Encounter,TPL_RBA,D_Start_PatAging,AdjCode_UID,Fee_UID,Chrg_Units,Chrg_Units_Req,OB_Additional_Units,Ins_Claim_Info,Acct_ID,Case_ID,Ref_Desc,Practice_ID,Dept_ID,Batch_ID,N_Ref_Auth,Chrg_Type,Proc_Code,Modifier1,Modifier2,Modifier3,Modifier4,Dx_Code1,Dx_Code2,Dx_Code3,Dx_Code4,Dx_Code5,Dx_Code6,Dx_Code7,Dx_Code8,Dx_Code9,Dx_Code10,Dx_Code11,Dx_Code12,Chrg_PVID,Place_Of_Service,Location_Of_Service,Acct_Plan1,Acct_Plan2,Acct_Plan3,Acct_Plan4,Rel_Plan1,Rel_Plan2,Rel_Plan3,Rel_Plan4,Chrg_Statement,Chrg_Ins_Bill1,Chrg_Ins_Bill2,Chrg_Ins_Bill3,Chrg_Ins_Bill4,Chrg_User_Flag,Chrg_Amt,Chrg_Bal,Pat_Portion,Chrg_Paid,Pat_Paid,Ins_Paid,Chrg_Adj,Pat_Adj,Ins_Adj,Next_Ins_Amt,Track_Amt,AR_Type,EEF_Post,Outside,Chrg_COB,Chrg_EPSDT,Chrg_EMG,Cross_Over,Surface,Quadrant,Tooth,Purch_Serv_Test,Prov_Specialty,Rev_Tfer,Immun_Batch_Number,NDC,POA1,POA2,POA3,POA4  

|Assc99||
|-----|-----|
| Table Name | Assc99|
| File Name Patterne | Assc99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,AGID,OPID,Appt_Track,D_Appt,T_Appt,Block_Time,Appt_Seq,Block_Seq,Appt_Slot_Type,Practice_ID,PVID,Appt_Reason,Appt_Length,Appt_Type,Appt_Status,Appt_Room,Appt_Slot,Appt_New,Appt_Old_Type,Appt_Print,Appt_Trns,Appt_Chart_Req,Appt_Rem_Req,Appt_Xray_Req,Appt_Xray_Print,Appt_Interpret,Appt_Notes_Flag  

|Assx99||
|-----|-----|
| Table Name | Assx99|
| File Name Patterne | Assx99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,D_Appt,T_Appt,T_Interp,T_INOUT1,T_INOUT2,T_INOUT3,T_INOUT4,T_INOUT5,T_INOUT6,T_INOUT7,T_INOUT8,T_INOUT9,T_INOUT10,Appt_Seq,Interp_Seq,Del_Seq,Case_Seq,Practice_ID,PVID,Visit_notes,Interp_Lang,Interp_Pref,Interp_Pref_Sex,Interp_Confirm,Interp_Assign,Interp_ID,Interp_Practice,Ref_PVID,Ref_Source,Ref_Process,Resource1,Resource2,Resource3,Cancel_Note,Ref_Source1,Ref_Source1_Type,Ref_Source1_Ori,Ref_Source2,Ref_Source2_Type,Ref_Source2_Ori,Ref_Source3,Ref_Source3_Type,Ref_Source3_Ori,Ref_Source4,Ref_Source4_Type,Ref_Source4_Ori,Ref_Source5,Ref_Source5_Type,Ref_Source5_Ori,Ref_Source6,Ref_Source6_Type,Ref_Source6_Ori,Case_ID,Appt_Done,N_Encounter,Acct_ID,Ext_Encounter  

|FMPRBM99||
|-----|-----|
| Table Name | FMPRBM99|
| File Name Patterne | FMPRBM99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,D_Problem,D_LastProblem,D_ProblemLastResolv,MemberSequence,HL7FamilyName,AgeAffected,SNOMEDCode,Problem,Status,Note  

|MRAY99||
|-----|-----|
| Table Name | MRAY99|
| File Name Patterne | MRAY99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: PTID,OPID,OPID_Change,D_Allergy,T_Allergy,D_Add_Allergy,T_Add_Allergy,D_Chg_Allergy,T_Chg_Allergy,Allergy_Seq,Rx_Med_Name,Rx_Med_Name_UC,Allergy_Type,Allergy_Reaction,Allergy_Severity,KDC,Allergy_Code1,Allergy_Code2,Current_Key  

|MRCI99||
|-----|-----|
| Table Name | MRCI99|
| File Name Patterne | MRCI99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,MRCI_UID,PTID,Clin_List_Seq,N_Linked_Clin_List,D_Clin_List,T_Clin_List,D_Clin_List_Onset,T_Clin_List_Onset,D_Clin_List_Last,T_Clin_List_Last,D_Clin_List_Res,T_Clin_List_Res,D_Clin_List_Res_A,T_Clin_List_Res_A,OPID,OPID_Resolved,Clin_List_Indent,Clin_List_Section,Clin_List_Name,Clin_List_Notes,Clin_List_Type,Clin_List_Status,Clin_List_LC,Clin_List_E_name,Clin_List_Name_UC,Clin_List_Code1,Clin_List_Code2,Clin_List_Label,Resp_Provider,Resp_Provider_Type,PVID,PVID_Resolved,Clin_List_Alert,Clin_List_Priority,Protocol_Apply,Clin_List_Encount,Clin_List_Confirm,Current_Key,Clin_List_Misc1,Clin_List_Misc2,Code1_Sys,Code1_Sys_Ver,Code2_Sys,Code2_Sys_Ver,Provenance  

|Mrhd99||
|-----|-----|
| Table Name | Mrhd99|
| File Name Patterne | Mrhd99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,OPID,OPID_Change,D_HM,T_HM,D_HM_Change,T_HM_Change,D_HM_Ordered,T_HM_Ordered,HM_Name,HM_Item_Current,HM_Status,HM_Comment,PVID,Active  

|MRHE99||
|-----|-----|
| Table Name | MRHE99|
| File Name Patterne | MRHE99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,D_HM,T_HM,D_Expiration,HM_FacilityUID,HM_Given_By,HM_DoseNumber,D_VIS_Published1,D_VIS_Published2,D_VIS_Published3,D_VIS_Presented1,D_VIS_Presented2,D_VIS_Presented3,HM_EnteredBy,HM_PPCONT_Id,HM_PPLIST_Id,HM_Name,HM_Dose,HM_Route,HM_Location,HM_Manufact,HM_Device,N_HM_Lot,HM_Misc1,HM_Misc2,HM_Comment,Active,HM_VFCStatus,HM_VaccineType1,HM_VaccineType2,HM_VaccineType3,HM_RequestedBy  

|Mrin99||
|-----|-----|
| Table Name | Mrin99|
| File Name Patterne | Mrin99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,D_Sig_On_File,D_Last_Bill,D_Effective,D_Expires,D_Ins_Birth,Plan_Ded_Amt,Plan_Ded_Paid,Plan_Pat_Copay,Plan_Pat_Paid,Plan_Chrg_YTD,Plan_Ben_Paid_YTD,Plan_Ben_Paid_Life,Plan_Ben_Year_Max,Plan_Ben_Life_Max,Acct_ID,Carrier_ID,Plan_ID,Acct_Plan,Ins_Last_Name,Ins_First_Name,Ins_MI,Ins_Name_Key,Ins_Suffix,Ins_SSN,Ins_Sex,Ins_ID,Group_Number,Empl_Name,Empl_Address1,Empl_Address2,Empl_Address3,Empl_City,Empl_County,Empl_State,Empl_Postal,Empl_Country,Empl_Tel,Empl_Tel_Ext,Ins_Benefits,Ins_Assign,Ins_Relcert,Ins_Empl_Status,Ins_Alt_Name,Ins_Alt_Address1,Ins_Alt_Address2,Ins_Alt_Address3,Ins_Alt_City,Ins_Alt_State,Ins_Alt_Postal,Ins_Alt_Country,Other_Empl_L_Name,Other_Empl_F_Name,Other_Empl_MI,Other_Empl_SSN,Other_Empl_Name,Other_Empl_Address1,Other_Empl_Address2,Other_Empl_Address3,Other_Empl_City,Other_Empl_State,Other_Empl_Postal,Other_Empl_Country,Other_Empl_Tel,Plan_Ben_1stmo,Reason_Disenroll,Acct_Plan_Status,PatSignature_Code  

|MROR99||
|-----|-----|
| Table Name | MROR99|
| File Name Patterne | MROR99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,Order_Seq,D_Ordered,T_Ordered,D_Sent,T_Sent,D_Received,T_Received,D_Overdue,T_Overdue,D_First_Received,T_First_Received,D_Last_Received,T_Last_Received,PVID_Sig,Repeat_ID,OPID_Creator,PVID,Order_Name,Order_Type,Hidden_Set,Hidden_Set_Name,Order_Proc_Code1,Order_Proc_Code2,Order_Proc_Code3,Order_Proc_Code4,Order_Proc_Code5,Order_Proc_Code6,Order_Proc_Code7,Order_Proc_Code8,Order_Proc_Code9,Order_Proc_Code10,Diag_Code1,Diag_Code2,Diag_Code3,Diag_Code4,Order_Note,Pat_Ext_ID,Order_Status,Order_Urgency,Order_Number2,Practice_ID,Sent_PVID1,Sent_PVID2,Sent_PVID3,Sent_PVID4,Osort,Signing_PVID,Facility_ID,Acct_ID,Case_ID,Acct_Plan1,Acct_Plan2,Acct_Plan3,Acct_Plan4,Issued,Safety_Warning,Care_Rec_Provided,Standing_Order,Completed_By_Note  

|MRPA99||
|-----|-----|
| Table Name | MRPA99|
| File Name Patterne | MRPA99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,D_Birth,D_PVID,D_Added,D_Posted,D_Last_Edit,D_Last_Appt,D_Last_Active,D_Last_Physical,D_Last_Care_Plan,Pats_Referred,Appt_Status,Old_ID,Pat_Ext_ID,Pat_Last_Name,Pat_First_Name,Pat_MI,Pat_Name_Key,Pat_Suffix,Pat_Address1,Pat_Address2,Pat_Address3,Pat_City,Pat_County,Pat_State,Pat_Postal,Pat_Country,Pat_Home_Tel,Pat_Home_Tel_Flag,Pat_Bus_Tel,Pat_Bus_Ext,Pat_Bus_Tel_Flag,Pat_Cell_Tel,Pat_Cell_Tel_Flag,Pat_Fax,Pat_Pager,Pat_Pager_Flag,Pat_Email,Pat_SSN,Pat_Sex,Pat_Race,Pat_Race2,Pat_Marital,Pat_Status,Pat_Occup,Pat_Employer_Flag,Pat_Employer,Pat_School_Flag,Pat_School,Usual_PVID,Primary_Type,Primary_PVID,Prev_Primary_Type,Prev_Primary_PVID,Attend_PVID,Resid_PVID,Practice_ID,HOH_ID_Type,HOH_ID,Sib_ID,Pat_Greeting,Pat_Records,Pat_Del,Thank_You,NoteF,Photo,OK_To_Mail,Pat_Prev_Status,Pat_Archived,Pat_Transfer,Pat_Import,Acct_ID,OK_To_Email,Interp_Language,Interp_Pref_ID,Interp_Pref_Name,Interp_Pref_Sex,Pat_Switches,Pat_Ethnicity,Birth_Time,Reminder_Pref,Adopted,Direct_Email  

|MRRV99||
|-----|-----|
| Table Name | MRRV99|
| File Name Patterne | MRRV99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,MRRV_UID,PTID,D_Lab_Drawn,T_Lab_Drawn,D_Lab_Recvd,T_Lab_Recvd,D_Prog_Note,D_Lab_Report,T_Lab_Report,Lab_Source,Order_Seq,Lab_Type,Lab_Change_Seq,Seq_Entry,Lab_HLNA,Pat_Ext_ID,Lab_Reviewed,PVID,Prov_Status,Other_PVID1,Other_PVID2,Other_PVID3,Other_PVID4,Other_PVID5,Oper_ID,Lab_Priority,Lab_Corrected,Lab_Category,Lab_Name,Lab_Result,Lab_Normals,Lab_Units,Lab_Prog_Title,Lab_Misc1,Facility_ID,Order_Name,NoteF,Flow_Templ_Name,Lab_Signature,LOINC,Lab_Facility_ID,Filler_Order_Number,Result_Status,Lab_Provider,Placer_Order,Order_Status,Specimen_Source,Ordered_By_ID,Ordered_By_Name,Copied_To_Name  

|MRRX99||
|-----|-----|
| Table Name | MRRX99|
| File Name Patterne | MRRX99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,MRRX_UID,PTID,KDC1,OPID_Sig1,OPID_Sig2,D_Rx,T_Rx,D_Orig_Rx,T_Orig_Rx,D_DC,T_DC,D_Sign1,T_Sign1,D_Sign2,T_Sign2,D_Pat_pickup1,T_Pat_pickup1,D_Pat_pickuplast,T_Pat_pickuplast,D_Rx_Authorized,T_Rx_Authorized,D_Rx_Old,T_Rx_Old,D_DC_Old,T_DC_Old,D_Next_Print,OPID_Creator,OPID_Sender,ARELFL_UID,Rx_Ref,Rx_Refills_left,Rx_Seq,Rx_Ref_Old,Rx_Med_Name,Rx_Size,Rx_Amt,Rx_Freq,Rx_Take,Rx_Form,Rx_Dur,Rx_Size_Unit,Rx_Take_Unit,Rx_Amt_Unit,PVID,PVID_Cosign,Rx_Type,Rx_Route,Rx_Print,Rx_Print_Old,Rx_Electronic_Sent,Rx_Tracking,Rx_Tracking2,NDC,Pharmacy,Pharmacy_ID,Practice_ID,Rx_Tfbits,Extended_Sig,Use_Extended_only,Rx_Note,Limit_Refills,Change_Sig_Req,Outside,OTC,Substitution_OK,Progress_Note,Allergy_Warn,Interact_Warn,DEA_Class,Patient_Handout,Rx_Signed,Rx_Suspend,Indication1,Indication2,Rx_Oper_Sig1,Rx_Oper_Sig2,Rx_Misc,Prov_Sig1,Prov_Sig2,Rx_Non_Medication,FormularyStatus,RxNormID,ThirdPartyRst,DosageFormCCode,SUMCode,PotencyUnitCCode,Indication1Qual,Indication2Qual,BrandGeneric,Rx_Provenance  

|MRTX99||
|-----|-----|
| Table Name | MRTX99|
| File Name Patterne | MRTX99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,Note_Seq,D_Note,T_Note,D_Note_Printed,T_Note_Printed,D_Note_Saved,T_Note_Saved,D_Last_Mod,T_Last_Mod,D_Sig1,D_Sig2,D_Sig3,D_Sig4,D_Sig5,D_Sig6,D_Sig7,D_Sig8,D_Sig9,D_Sig10,T_Sig1,T_Sig2,T_Sig3,T_Sig4,T_Sig5,T_Sig6,T_Sig7,T_Sig8,T_Sig9,T_Sig10,Order_Seq,Order_Seq2,Order_Seq3,Order_Seq4,Order_Seq5,N_Encounter,Rec_Type,Note_Misc,PVID,Sig_PVID,Sig_PVID1,Sig_PVID2,Sig_PVID3,Sig_PVID4,Sig_PVID5,Sig_PVID6,Sig_PVID7,Sig_PVID8,Sig_PVID9,Sig_PVID10,Note_Sign,Practice_ID,Note_Title,Note,Pat_Ext_ID,Note_Print,Note_Permanent,Note_Format,Format_Misc,Note_Image,mnprbits,Note_ID,Result_Status  

|Mrvi99||
|-----|-----|
| Table Name | Mrvi99|
| File Name Patterne | Mrvi99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PTID,D_Vitals,Vitals_bitmap,Vitals_Seq,Vitals_Type,Pat_Ext_ID,var_text001,var_text002,var_text003,var_text004,var_text005,var_text006,var_text007,var_text008,var_text009,var_text010,var_text011,var_text012,var_text013,var_text014,var_text015,var_text016,var_text017,var_text018,var_text019,var_text020  

|MRVL99||
|-----|-----|
| Table Name | MRVL99|
| File Name Patterne | MRVL99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,MRVL_UID,PTID,OPID,OPID_Change,D_Vital,T_Vital,D_Change_Vital,T_Change_Vital,Signature,PVID,Vital_Name,Element_Type,Element_Definition,Vital_Result,Vital_Units,Vital_Attrib,Vital_HLNA,Current_Key,NoteF,Vital_Provenance  

|PPCENC99||
|-----|-----|
| Table Name | PPCENC99|
| File Name Patterne | PPCENC99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,PPCENC_UID,PTID,D_Created,T_Created,D_Encounter,T_Encounter,D_Printed_Summ,T_Printed_Summ,D_Elect_Summ,T_Elect_Summ,Encounter_Type,PVID,Practice_ID,TOC_Inbound,TOC_Outbound,TOC_Summ_Prov_Phys,TOC_Summ_Prov_Elec,Med_Recon,Printed_Summ,Elect_Summ,Refused_Summ,Status,Ed_Resources_Provid  

|PPDIAG99||
|-----|-----|
| Table Name | PPDIAG99|
| File Name Patterne | PPDIAG99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,D_Diag_Start,D_Diag_Exp,Diag_ICD10,Diag_SNOMED,Diag_SNOMED_Ver,Diag_Code,Diag_Office_Code,Diag_Status,Diag_Type,Diag_DRG_Amt,Diag_Desc_Short,Diag_Desc_Long,Diag_ICD10_Desc_Sho,Diag_ICD10_Desc_Lon,Diag_SNOMED_Desc,Diag_Friendly_Desc  

|Ppprov99||
|-----|-----|
| Table Name | Ppprov99|
| File Name Patterne | Ppprov99|
| Delimiter | ,|
| Text Qualifier | "|
| Fixed Width? | False|
| Has Header? | True|
| Add Row Number? | False|  

**Columns**: CTPADBYTE,D_Prov_Add,D_Prov_Last_Edit,Prov_New_Pat_DTD,Prov_New_Pat_MTD,Prov_New_Pat_YTD,Prov_Seen_Pat_MTD,Prov_Seen_Pat_YTD,D_First_Web_Access,D_Last_Web_Access,D_Web_Expiration,D_RVM_Start,Lab_Msg_OPID,Processing_OPID,Download_Msg_OPID,PVID,Prov_Type,Prov_Last_Name,Prov_First_Name,Prov_MI,Prov_Suffix,Prov_Title,Prov_UC_Name,Prov_Kind,Supervisor_PVID,Billing_PVID,Pay_To_PVID,Prov_Address1,Prov_Address2,Prov_Address3,Prov_City,Prov_County,Prov_State,Prov_Postal,Prov_Country,Prov_Home_Tel,Prov_Bus_Tel,Prov_Bus_Ext,Prov_Cell_Tel,Prov_Fax,Prov_Pager,Prov_Email,Prov_SSN,Prov_Greeting,Prov_TOV,Prov_Length,Prov_Sort,Prov_Oncall_Note,Prov_DTD_Chrg,Prov_MTD_Chrg,Prov_YTD_Chrg,Prov_DTD_Pay,Prov_MTD_Pay,Prov_YTD_Pay,Prov_DTD_Adj,Prov_MTD_Adj,Prov_YTD_Adj,Prov_DTD_Deb,Prov_MTD_Deb,Prov_YTD_Deb,Prov_Cur_AR,Prov_Cur_AR30,Prov_Cur_AR60,Prov_Cur_AR90,Prov_Cur_AR120,Prov_Begin_AR,Prov_Begin_AR30,Prov_Begin_AR60,Prov_Begin_AR90,Prov_Begin_AR120,Prov_Begin_ACR,Prov_Fee_Schedule,Prov_Bill_Insur,Prov_Specialty1,Prov_Specialty2,Prov_Specialty3,Prov_Specialty4,Prov_Specialty5,Prov_Specialty6,Practice_ID,Prov_Encounter,Prov_EEF,Prov_EEF_Def_Prac,Prov_Status,Prov_Rx,Prov_Rx_Fax,Web_Flag,Web_Login,Prov_RCTY,Prov_Default,Cur_RVM_Work,Cur_RVM_Pract_Exp,Cur_RVM_Malpract,Cur_RVM_NPract_Exp,Cur_RVM_General,New_RVM_Work,New_RVM_Pract_Exp,New_RVM_Malpract,New_RVM_NPract_Exp,New_RVM_General,Old_RVM_Work,Old_RVM_Pract_Exp,Old_RVM_Malpract,Old_RVM_NPract_Exp,Old_RVM_General,Prov_NPI,Prov_Sig_File,Prov_Rx_Header,Prov_SS,Prov_Rxh,Rx_Fax_Cover,Letter_Fax_Cover,Chart_Fax_Cover,Prov_Flags,Prov_Sig,Web_Password,Past_Web_Password,Entity_Type_2  

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *Unknown. Follow up with the Solution Architect* |
|Is the database production?| *Unknown. Follow up with the Solution Architect*  |
|Frequency of Extracts| *Unknown. Follow up with the Solution Architect*  |

##Known Issues

*Not documented at this time. Contact the Solution Architect for details.*

##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20WCHNDANB%20or%20%22Data%20Source%20Acronym%22%20~%20WCHNDANB)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)