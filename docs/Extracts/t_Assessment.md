#t_assessment

*column mappings for t_assessment Extract.*

| Extract Column | QDW Table | QDW Column |
| --- | --- | --- |
| rendering_provider_first_name | dbo.Provider_Master | prov_first_name |
| rendering provider last name | dbo.Provider_Master | prov_last_name |
| rendering provider print name | dbo.Provider_Master | prov_fullname |
| rendering provider degree | dbo.Provider_Master | prov_degree_1 |
| rendering provider specialty | dbo.Provider_Master | prov_specialty_1 |
| rendering provider NPI  | dbo.Provider_Master | prov_NPI |
| rendering_plan_provider_id | plan_provider | provider_id (match based on providerpersonsource) |
| service location | location_master | location_display_name |
| service from date | [dbo].[t_encounter] | enc_timestamp |
| service to date | [dbo].[t_encounter]  | enc_timestamp  |
| TypeBillCode | NULL | Blank for Future enhancement |
| PlaceOfServiceCode | NULL | Blank for Future enhancement |
| DRG Version | NULL | Blank for Future enhancement |
| DRGCode | NULL | Blank for Future enhancement |
| DischargeStatus | NULL | Blank for Future enhancement |
| EpisodeOfIllness | NULL | Blank for Future enhancement |
| AdmitDate | NULL | Blank for Future enhancement |
| DischargeDate | NULL | Blank for Future enhancement |
| AdmitCount | NULL | Blank for Future enhancement |
| CoveredDays | NULL | Blank for Future enhancement |
| primary diagnosis | dbo.t_assessment | icd10_code or icd9_code  (primary_diagnosis_ind) |
| primary diagnosis type  | dbo.t_assessment | 'ICD10' or 'ICD9'  With (primary_diagnosis_ind = 1)
| secondary diagnosis 1 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 2 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 3 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 4 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 5 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 6 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 7 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 8 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 9 | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 10  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 11  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 12  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 13  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 14  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 15  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 16  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 17  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 18  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 19  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 20  | dbo.t_assessment | icd10_code or icd9_code  |
| secondary diagnosis 1 type  |  | 'ICD10' or 'ICD9' |
| secondary diagnosis 2 type  |  | 'ICD10' or 'ICD9' |
| secondary diagnosis 3 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 4 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 5 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 6 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 7 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 8 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 9 type  |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 10 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 11 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 12 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 13 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 14 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 15 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 16 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 17 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 18 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 19 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 20 type |  | 'ICD10' or 'ICD9'  |
| secondary diagnosis 1 POA |  | Indicator that diagnosis was present on admission. Blank for future enhancement |
| secondary diagnosis 2 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 3 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 4 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 5 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 6 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 7 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 8 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 9 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 10 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 11 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 12 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 13 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 14 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 15 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 16 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 17 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 18 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 19 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |
| secondary diagnosis 20 POA |  | Indicator that diagnosis was present on admission Blank for future enhancement |


