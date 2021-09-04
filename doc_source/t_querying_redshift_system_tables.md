# Task 6: Query the system tables<a name="t_querying_redshift_system_tables"></a>

In addition to the tables that you create, your database contains a number of system tables\. These system tables contain information about your installation and about the various queries and processes that are running on the system\. You can query these system tables to collect information about your database\.

**Note**  
The description for each table in this documentation indicates whether a table is visible to all users or only to superusers\. Log in as a superuser to query tables that are visible only to superusers\.

Amazon Redshift provides access to the following types of system tables:
+  [STL tables](https://docs.aws.amazon.com/redshift/latest/dg/c_intro_STL_tables.html) 

  These system tables are generated from Amazon Redshift log files to provide a history of the system\. Logging tables have an STL prefix\.
+  [STV tables](https://docs.aws.amazon.com/redshift/latest/dg/c_intro_STV_tables.html) 

  These tables are virtual system tables that contain snapshots of the current system data\. Snapshot tables have an STV prefix\.
+  [System views](https://docs.aws.amazon.com/redshift/latest/dg/c_intro_system_views.html) 

  System views contain a subset of data found in several of the STL and STV system tables\. Systems views have an SVV or SVL prefix\.
+  [System catalog tables](https://docs.aws.amazon.com/redshift/latest/dg/c_intro_catalog_views.html) 

  The system catalog tables store schema metadata, such as information about tables and columns\. System catalog tables have a PG prefix\.

To retrieve system table information about a query, you might need to specify the process ID associated with that query\. For more information, see [Determine the process ID of a running query](determine_pid.md)\.

## View a list of table names<a name="t_querying_redshift_system_tables-view-a-list-of-table-names"></a>

To view a list of all tables in a schema, you can query the PG\_TABLE\_DEF system catalog table\. You can first examine the setting for `search_path`\.

```
SHOW search_path;
```

The result should look similar to the following,

```
  search_path
---------------
 $user, public
(1 row)
```

The following example adds the `SALES` schema to the search path and shows all the tables in the `SALES` schema\.

```
set search_path to '$user', 'public', 'sales';
                
SHOW search_path;
      search_path       
------------------------
 "$user", public, sales
(1 row)

select * from pg_table_def where schemaname = 'sales';
 schemaname | tablename |  column  |          type          | encoding | distkey | sortkey | notnull 
------------+-----------+----------+------------------------+----------+---------+---------+---------
 sales      | demo      | personid | integer                | az64     | f       |       0 | f
 sales      | demo      | city     | character varying(255) | lzo      | f       |       0 | f
(2 rows)
```

The following example shows a list of all tables called `DEMO` in all schemas on the current database\.

```
select * from pg_table_def where tablename = 'demo';
 schemaname | tablename |  column  |          type          | encoding | distkey | sortkey | notnull 
------------+-----------+----------+------------------------+----------+---------+---------+---------
 public     | demo      | personid | integer                | az64     | f       |       0 | f
 public     | demo      | city     | character varying(255) | lzo      | f       |       0 | f
 sales      | demo      | personid | integer                | az64     | f       |       0 | f
 sales      | demo      | city     | character varying(255) | lzo      | f       |       0 | f
(4 rows)
```

For more information, see [PG\_TABLE\_DEF](https://docs.aws.amazon.com/redshift/latest/dg/r_PG_TABLE_DEF.html)\.

You can also use the Amazon Redshift query editor to view all the tables in a specified schema by first choosing a database that you want to connect to\.

## View users<a name="t_querying_redshift_system_tables-view-database-users"></a>

You can query the PG\_USER catalog to view a list of all users, along with the user ID \(USESYSID\) and user privileges\. 

```
SELECT * FROM pg_user;
  usename   | usesysid | usecreatedb | usesuper | usecatupd |  passwd  | valuntil | useconfig
------------+----------+-------------+----------+-----------+----------+----------+-----------
 rdsdb      |        1 | true        | true     | true      | ******** | infinity |
 awsuser    |      100 | true        | true     | false     | ******** |          |
 guest      |      104 | true        | false    | false     | ******** |          |
(3 rows)
```

The user name `rdsdb` is used internally by Amazon Redshift to perform routine administrative and maintenance tasks\. You can filter your query to show only user\-defined user names by adding `where usesysid > 1` to your SELECT statement\.

```
SELECT * FROM pg_user;
  usename   | usesysid | usecreatedb | usesuper | usecatupd |  passwd  | valuntil | useconfig
------------+----------+-------------+----------+-----------+----------+----------+-----------
 awsuser    |      100 | true        | true     | false     | ******** |          |
 guest      |      104 | true        | false    | false     | ******** |          |
(2 rows)
```

## View recent queries<a name="t_querying_redshift_system_tables-view-recent-queries"></a>

In the previous example, the user ID \(USESYSID\) for `adminuser` is 100\. To list the five most recent queries run by `adminuser`, you can query the SVL\_QLOG view\. 

The SVL\_QLOG view is a friendlier subset of information from the STL\_QUERY table\. You can use this view to find the query ID \(QUERY\) or process ID \(PID\) for a recently run query\. You can also use this view to check how long it took a query to complete\. SVL\_QLOG includes the first 60 characters of the query string \(SUBSTRING\) to help you locate a specific query\. Use the LIMIT clause with your SELECT statement to limit the results to five rows\. 

```
SELECT query, pid, elapsed, substring from svl_qlog
WHERE userid = 100
ORDER BY starttime desc
LIMIT 4;
```

The result look something like the following\. 

```
 query|  pid  |  elapsed |       substring
------+-------+----------+----------------------------------------------------------------
 892  | 21046 |  55868   | SELECT query, pid, elapsed, substring from svl_qlog WHERE us 
 620  | 17635 | 1296265  | SELECT query, pid, elapsed, substring from svl_qlog WHERE us
 610  | 17607 |  82555   | SELECT * from DEMO; 
 596  | 16762 |  226372  | INSERT INTO DEMO VALUES (100);)
```