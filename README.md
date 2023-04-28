# Delta_ModifiedDate
## Incremental load SSIS package using DateTime columns

This method is mainly used to do ETL when the source table has LastChangedDate,LastUpdate,LastModifiedDate or Modified, and any column which refers to the date which the source was added new records and old records were updated.  

For example: see the sample of the source table from OLTP AdaventureWords2019.bck database (https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms)
![image](https://user-images.githubusercontent.com/114147734/235260487-e1354077-c991-4573-a496-bd7562e2b0c2.png)
