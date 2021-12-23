# Task 3: Create a schema<a name="t_creating_schema"></a>

After you create a new database, you can create a new schema in the current database\. A *schema* is a namespace that contains named database objects such as tables, views, and user\-defined functions \(UDFs\)\. A database can contain one or multiple schemas, and each schema belongs to only one database\. Two schemas can have different objects that share the same name\.

You can create multiple schemas in the same database to organize data the way that you want or to group your data functionally\. For example, you can create a schema to store all your staging data and another schema to store all the reporting tables\. You can also create different schemas to store data relevant to different business groups that are in the same database\. Each schema can store different database objects, such as tables, views, and user\-defined functions \(UDFs\)\. In addition, you can create schemas with the AUTHORIZATION clause\. This clause gives ownership to a specified user or sets a quota on the maximum amount of disk space that the specified schema can use\. 

Amazon Redshift automatically creates a schema called `public` for every new database\. When you don't specify the schema name while creating database objects, the objects go into the `public` schema\.

To access an object in a schema, qualify the object by using the `schema_name.table_name` notation\. The qualified name of the schema consists of the schema name and table name separated by a dot\. For example, you might have a `sales` schema that has a `price` table and an `inventory` schema that also has a `price` table\. When you refer to the `price` table, you must qualify it as `sales.price` or `inventory.price`\.

The following example creates a schema named **SALES** for the user `GUEST`\.

```
CREATE SCHEMA SALES AUTHORIZATION GUEST;
```

For information about more command options, see [CREATE SCHEMA](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_SCHEMA.html) in the *Amazon Redshift Database Developer Guide*\.

To view the list of schemas in your database, run the following command\.

```
select * from pg_namespace;
```

The output should look similar to the following\.

```
  nspname             | nspowner |         nspacl
----------------------+----------+--------------------------
  sales               |  100     |
  pg_toast            |   1      |
  pg_internal         |   1      |
  catalog_history     |   1      |
  pg_temp_1           |   1      | 
  pg_catalog          |   1      | {rdsdb=UC/rdsdb,=U/rdsdb}
  public              |   1      | {rdsdb=UC/rdsdb,=U/rdsdb}
  information_schema  |   1      | {rdsdb=UC/rdsdb,=U/rdsdb}
```

For more information on how to query catalog tables, see [Querying the catalog tables](https://docs.aws.amazon.com/redshift/latest/dg/c_join_PG.html) in the *Amazon Redshift Database Developer Guide\.*

Use the GRANT statement to give permissions to users for the schemas\.

The following example grants privilege to the `GUEST` user to select data from all tables or views in the `SALESCHEMA` using a SELECT statement\. 

```
GRANT SELECT ON ALL TABLES IN SCHEMA SALES TO GUEST;
```

The following example grants all available privileges at once to the `GUEST` user\.

```
GRANT ALL ON SCHEMA SALES TO GUEST;
```