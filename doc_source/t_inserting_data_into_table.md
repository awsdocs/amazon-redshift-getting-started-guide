# Insert data rows into a table<a name="t_inserting_data_into_table"></a>

After you create a table, insert rows of data into that table\.

**Note**  
The [INSERT](https://docs.aws.amazon.com/redshift/latest/dg/r_INSERT_30.html) command inserts rows into a table\. For standard bulk loads, use the [COPY](https://docs.aws.amazon.com/redshift/latest/dg/r_COPY.html) command\. For more information, see [Use a COPY command to load data](https://docs.aws.amazon.com/redshift/latest/dg/c_best-practices-use-copy.html)\.

For example, to insert values into the `DEMO` table, run the following command\.

```
INSERT INTO DEMO VALUES (781, 'San Jose'), (990, 'Palo Alto');
```