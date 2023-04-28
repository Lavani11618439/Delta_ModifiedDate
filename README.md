# Delta_ModifiedDate
## Incremental load SSIS package using DateTime columns

This method is mainly used to do ETL when the source table has LastChangedDate,LastUpdate,LastModifiedDate or Modified, and any column which refers to the date which the source was added new records and old records were updated.  

For example: see the sample of the source table from OLTP AdaventureWords2019.bck (https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms)

## Source (Currency)

![image](https://user-images.githubusercontent.com/114147734/235260487-e1354077-c991-4573-a496-bd7562e2b0c2.png)

## Target/Destination (DimCurrency)

![image](https://user-images.githubusercontent.com/114147734/235263318-47f681cf-43dd-47ba-bfae-7c937d81ffa4.png)



# Set-up

## Step 1: Create two OLE DB connection managers

-Configure the source and target datasets accordingly

## Step 2: Create variables

- In order to query the changes from the source, we have to know the maximum Modified column value from the target dataset
- Query all records that have greater than (>) the Modified column value from the source 

1. Name = Currency_LastUpdate , datatype = Datetime

This will store the value returned from the target (In the result set section set LastUpdate = User::Currency_lastudate)

SQLStatement = select max([ModifiedDate]) as LastUpdate from [Inc_Staging].[dbo].[DimCurrency]

![image](https://user-images.githubusercontent.com/114147734/235268611-fdb9ef50-42b0-43e3-b838-302609f6785a.png)


2. Name = sqlCommand, datatype = String, Expression = as shown in the picture below

![image](https://user-images.githubusercontent.com/114147734/235266436-74d941a1-65b8-45d8-93c5-e3edbb06a770.png)

This variable will filter records from the source where the ModifiedDate > Currency_lastupdate variable








