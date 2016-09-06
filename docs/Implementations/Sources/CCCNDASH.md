Status: Internal-Only
Author: Simon Ioffe
CreateDate: 2016-06-08
ModifyDate: 2016-06-15


#CCCNDASH (CONTRACT DASHBOARD QUERIES)

**Client(s)**: [CCCN](../CCCN.md)  
**Density Area**: Northwest   

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
| Data Source Name| **CCCN CONTRACT DASHBOARD** |
| Data Source Acronym| **CCCNDASH** |
| Type | **OUTBOUND-INTERNAL** |
| Site ID | **N/A** |
| Architecture Model | **N/A**|
| Database hosting | **INTERNAL** |
| Schedule | **WEEKLY: Saturday** |



##Requirements
Will be used to feed data for the [Contract Dashboard on Arcadia Labs](https://labs.arcadiaanalytics.com/cccn_dashboard). Will be sourcing data on a monthly basis.

The files should **not** be encrypted and should follow below naming convention with no timestamp. Previous files should be overwritten.


###Quality Measures

```sql
SELECT   
       [valueNum]  
      ,[valueDenom]  
      ,[date]  
      ,[pod]  
      ,[practice]       
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMeasures]   
  WHERE [type] =  --Paramters for distinct values. One distinct value per extract. (SELECT DISTINCT [type] FROM [CCCN_WAREHOUSE_QA].[dash].[outputMeasures])
  --ouput name 'Quality - [type].csv'
```

###Leakage

```sql
SELECT [valueNum]
      ,[valueDenom]
      ,[date]
      ,[pod]
      ,[practice]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputLeakage]
  WHERE [category]=
   --Paramters for distinct values. One distinct value per extract. (SELECT DISTINCT [category] FROM [CCCN_WAREHOUSE_QA].[dash].[outputLeakage])
  --ouput name 'Leakage - [category]].csv'
```

###Medical Expense

```sql
SELECT [valueNum]
      ,[valueDenom]
      ,[date]
      ,[pod]
      ,[practice]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputExpense]
  WHERE [category]=
   --Paramters for distinct values. One distinct value per extract. (SELECT DISTINCT [category] FROM [CCCN_WAREHOUSE_QA].[dash].[outputExpense])
  --ouput name 'Medical Expense - [category]].csv'
```

###Network Summary 

**Excludes Member Month**  
```sql
SELECT [valueNum]
      ,[valueDenom]
      ,[date]
      ,[pod]
      ,[practice]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics]
  WHERE [type]=
   --Paramters for distinct values. One distinct value per extract. (SELECT DISTINCT [type] FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics] WHERE [type] not in ('Member Months','Total Costs'))
  --ouput name 'Network Summary - [type].csv'
```

**Member Month**  
```sql
SELECT 
       [date]
      ,[pod]
      ,[practice]
      ,[valueNum] as [value]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics]
  WHERE [type]='Member Months'
--ouput name 'Network Summary - Member Months.csv'
```

**Total Costs**  
```sql
SELECT 
       [date]
      ,[pod]
      ,[practice]
      ,[valueNum] as [value]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics]
  WHERE [type]='Member Months'
--ouput name 'Network Summary - Total Costs.csv'
```

##Example Dynamic SQL Output Query
```sql
DECLARE @name VARCHAR(255)

-----------------------------QUALITY
  
  DECLARE categoryCursor CURSOR FOR  
  SELECT DISTINCT [type] FROM [CCCN_WAREHOUSE_QA].[dash].[outputMeasures]

OPEN categoryCursor   
FETCH NEXT FROM categoryCursor INTO @name   

WHILE @@FETCH_STATUS = 0   
BEGIN   

SELECT 'Quality - '+@name+'.csv' as ouputFileName;

SELECT   
       [valueNum]  
      ,[valueDenom]  
      ,cast([date] as date) [date] 
      ,[pod]  
      ,[practice]       
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMeasures]   
  WHERE [type]=@name 
  

       FETCH NEXT FROM categoryCursor INTO @name   
END   

CLOSE categoryCursor   
DEALLOCATE categoryCursor
  
  
  
  
  
  ------------------------------LEAKAGE
 
  DECLARE categoryCursor CURSOR FOR  
  SELECT DISTINCT [category] FROM [CCCN_WAREHOUSE_QA].[dash].[outputLeakage]

OPEN categoryCursor   
FETCH NEXT FROM categoryCursor INTO @name   

WHILE @@FETCH_STATUS = 0   
BEGIN   

SELECT 'Leakage - '+@name+'.csv' as ouputFileName;

       SELECT [valueNum]
      ,[valueDenom]
      ,cast([date] as date) [date]
      ,[pod]
      ,[practice]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputLeakage]
  WHERE [category]=@name 
  

       FETCH NEXT FROM categoryCursor INTO @name   
END   

CLOSE categoryCursor   
DEALLOCATE categoryCursor




------------------------------Medical Expense
 
  DECLARE categoryCursor CURSOR FOR  
  SELECT DISTINCT [category] FROM [CCCN_WAREHOUSE_QA].[dash].[outputExpense]

OPEN categoryCursor   
FETCH NEXT FROM categoryCursor INTO @name   

WHILE @@FETCH_STATUS = 0   
BEGIN   

SELECT 'Medical Expense - '+@name+'.csv' as ouputFileName;

       SELECT [valueNum]
      ,[valueDenom]
      ,cast([date] as date) [date]
      ,[pod]
      ,[practice]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputExpense]
  WHERE [category]=@name 
  

       FETCH NEXT FROM categoryCursor INTO @name   
END   

CLOSE categoryCursor   
DEALLOCATE categoryCursor





------------------------------Network Summary
 
  DECLARE categoryCursor CURSOR FOR  
  SELECT DISTINCT [type] FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics] WHERE [type] not in ('Member Months','Total Costs');

OPEN categoryCursor   
FETCH NEXT FROM categoryCursor INTO @name   

WHILE @@FETCH_STATUS = 0   
BEGIN   

SELECT 'Network Summary - '+@name+'.csv' as ouputFileName;

SELECT [valueNum]
      ,[valueDenom]
      ,cast([date] as date) [date]
      ,[pod]
      ,[practice]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics]
  WHERE [type]=@name 
  

       FETCH NEXT FROM categoryCursor INTO @name   
END   

CLOSE categoryCursor   
DEALLOCATE categoryCursor



------------------Member Month


SELECT 'Network Summary - Member Months.csv' as ouputFileName;

SELECT cast([date] as date) [date]
      ,[pod]
      ,[practice]
      ,[valueNum] as [value]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics]
  WHERE [type]='Member Months'
  
   ------------------Total Costs

SELECT 'Network Summary - Total Costs.csv' as ouputFileName;

SELECT --cast([date] as date) [date]
       [date]
      ,[pod]
      ,[practice]
      ,[valueNum] as [value]
  FROM [CCCN_WAREHOUSE_QA].[dash].[outputMetrics]
  WHERE [type]='Total Costs' 
```

##Data Source

The data is pulled from the .dash schema within the CCCN Warehouse

##Operations
|Restriction | |
|-----|-----|
|Time of day extract/access restrictions| *10 AM EASTERN* |
|Is the database production?| *N/A*  |
|Frequency of Extracts| *Weekly*  |


##Known Issues

*Contact the Solution Architect for details.*


##External Documents
- [JIRA Open Issues](https://jira.arcadiasolutions.com/issues/?jql=(labels%20%3D%20HOPEFM%20or%20%22Data%20Source%20Acronym%22%20~%20CCCNDASH)%20and%20status%20!%3D%20Closed)
- [Connector Deployment History](https://github.com/arcadia/qdw/wiki/connector-version)
- Build Request (*Unknown. Follow up with the Solution Architect*)
- SOW (*Unknown. Follow up with the Solution Architect*)
