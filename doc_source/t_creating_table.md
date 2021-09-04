# Task 4: Create a table<a name="t_creating_table"></a>

After you create your new database, create tables to hold your data\. Specify any column information when you create the table\.

In the following example, the `GUEST` user logs on to the `SALESDB` and creates a new table\.

For example, to create a table named **DEMO**, run the following command\.

```
CREATE TABLE Demo (
  PersonID int,
  City varchar (255)
);
```

You can also create a table using the `schema_name.object_name` notation to create the table in the `SALES` schema\.

```
CREATE TABLE SALES.DEMO (
  PersonID int,
  City varchar (255)
);
```

To view and inspect schemas and their tables, you can use the Amazon Redshift query editor\. Or you can see the list of tables in schemas using system views\. For more information, see [Task 6: Query the system tables](t_querying_redshift_system_tables.md)\.

By default, new database objects, such as tables, are created in the default schema named `public` created during cluster creation\. You can use another schema to create database objects\. For more information about schemas, see [Managing database security](https://docs.aws.amazon.com/redshift/latest/dg/r_Database_objects.html) in the *Amazon Redshift Database Developer Guide*\.

The `encoding`, `distkey`, and `sortkey` columns are used by Amazon Redshift for parallel processing\. For more information about designing tables that incorporate these elements, see [Amazon Redshift best practices for designing tables](https://docs.aws.amazon.com/redshift/latest/dg/c_designing-tables-best-practices.html)\.