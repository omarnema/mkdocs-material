#Master Extract

*column mappings for Master Person Demographic Extract.*

| Extract Column | QDW Table           | QDW Column                                     |
|----------------|---------------------|------------------------------------------------|
| prsn_key       | mpi.person_member   | person_id                                      |
| mrn            | t_patient           | pat_medical_record_number                      |
| Member No      | plan_member_elig    | concat(mbr_no,ISNULL('-' + p.mbr_no_suffix,''))|
| first name     | plan_member         | first_name                                     |
| last name      | plan_member         | last_name                                      |
| middle name    | plan_member         | middle_name                                    |
| date of birth  | plan_member         | dob                                            |
| gender         | plan_member         | sex                                            |
| address        | plan_member_address | concat(Address_Line1,ISNULL(' ' + Address_Line2,''))        |
| city           | plan_member_address | city                                           |
| state          | plan_member_address | state                                          |
| zip            | plan_member_address | zip                                            |
| ssn            | plan_member         | ssn                                            |
| phone_1        | plan_member         | COALESCE(home_phone,cell_phone,business_phone) |
| Source_System  | site_master         | site_EMR_Name                                  |
