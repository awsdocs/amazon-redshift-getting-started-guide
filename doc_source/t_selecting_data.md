# Select data from a table<a name="t_selecting_data"></a>

After you create a table and populate it with data, use a SELECT statement to display the data contained in the table\. The SELECT \* statement returns all the column names and row values for all of the data in a table\. Using SELECT is a good way to verify that recently added data was correctly inserted into the table\.

To view the data that you entered in the **DEMO** table, run the following command\.

```
SELECT * from SALES.DEMO;
```

The result should looks like the following\.

```
 personid |   city    
----------+-----------
      781 | San Jose
      990 | Palo Alto
(2 rows)
```

For more information about using the SELECT statement to query tables, see [SELECT](https://docs.aws.amazon.com/redshift/latest/dg/r_SELECT_synopsis.html)\.