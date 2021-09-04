# Task 1: Create a database<a name="t_creating_database"></a>

After you verify that your cluster is up and running, you can create your own first database\. This database is where you actually create tables, load data, and run queries\. A single cluster can host multiple databases\. For example, you can have a `SALESDB` database and an `ORDERSDB` database on the same cluster\.

For example, to create a database named **SALESDB**, run the following command in your SQL client tool\. 

```
CREATE DATABASE SALESDB;
```

For this exercise, accept the defaults\. For information about more command options, see [CREATE DATABASE](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_DATABASE.html) in the *Amazon Redshift Database Developer Guide*\.

After you have created the SALESDB database, you can connect to the new database from your SQL client\. Use the same connection parameters as you used for your current connection, but change the database name to `SALESDB`\.