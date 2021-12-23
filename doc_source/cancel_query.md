# Task 7: Cancel a query<a name="cancel_query"></a>

If you run a query that is taking too long or is consuming excessive cluster resources, cancel the query\. For example, create a list of ticket sellers that includes the seller's name and quantity of tickets sold\. The following query selects data from the `SALES` table and `USERS` table and joins the two tables by matching SELLERID and USERID in the WHERE clause\.

```
SELECT sellerid, firstname, lastname, sum(qtysold)
FROM sales, users
WHERE sales.sellerid = users.userid
GROUP BY sellerid, firstname, lastname
ORDER BY 4 desc;
```

The result looks something like the following\.

```
 sellerid | firstname | lastname | sum
----------+-----------+----------+------
  48950   |   Nayda   |   Hood   | 184
  19123   |   Scott   | Simmons  | 164
  20029   |    Drew   | Mcguire  | 164
  36791   |  Emerson  | Delacruz | 160
  13567   |   Imani   |   Adams  | 156
  9697    |  Dorian   |    Ray   | 156
  41579   | Harrison  | Durham   | 156
  15591   |  Phyllis  |  Clay    | 152
  3008    |  Lucas    | Stanley  | 148
  44956   |  Rachel   |Villarreal| 148
```

**Note**  
This is a complex query\. For this tutorial, you don't need to worry about how this query is constructed\.

The previous query runs in seconds and returns 2,102 rows\.

Suppose that you forget to put in the WHERE clause\.

```
SELECT sellerid, firstname, lastname, sum(qtysold)
FROM sales, users
GROUP BY sellerid, firstname, lastname
ORDER BY 4 desc;
```

The result set includes all of the rows in the `SALES` table multiplied by all the rows in the `USERS` table \(49989\*3766\)\. This is called a Cartesian join, and it isn't recommended\. The result is over 188 million rows and takes a long time to run\.

To cancel a running query, use the CANCEL command with the query's PID\.

To find the process ID, start a new session and query the STV\_RECENTS table, as shown in the previous step\. The following example shows how you can make the results more readable\. To do this, use the TRIM function to trim trailing spaces and show only the first 20 characters of the query string\.

```
SELECT pid, trim(user_name), starttime, substring(query,1,20) 
FROM stv_recents
WHERE status='Running';
```

The result looks something like the following\.

```
  pid  |   btrim    |         starttime          |      substring
-------+------------+----------------------------+----------------------
 610   | adminuser  | 2013-03-28 18:39:49.355918 | select sellerid, fir
(1 row)
```

To cancel the query with PID 18764, run the following command\.

```
CANCEL 610;
```

**Note**  
The CANCEL command doesn't stop a transaction\. To stop or roll back a transaction, use the ABORT or ROLLBACK command\. To cancel a query associated with a transaction, first cancel the query then stop the transaction\.

If the query that you canceled is associated with a transaction, use the ABORT or ROLLBACK command to cancel the transaction and discard any changes made to the data:

```
ABORT;
```

Unless you are signed on as a superuser, you can cancel only your own queries\. A superuser can cancel all queries\.

## Cancel a query from another session<a name="cancel_query-cancel-a-query-from-another-session"></a>

If your query tool doesn't support running queries concurrently, start another session to cancel the query\. For example, the query editor that we use in the *Amazon Redshift Getting Started Guide* doesn't support multiple concurrent queries\. To start another session with the query editor, choose **File**, **New Window** and connect using the same connection parameters\. Then you can find the PID and cancel the query\. 

## Cancel a query using the superuser queue<a name="cancel_query-cancel-a-query-using-the-superuser-queue"></a>

If your current session has too many queries running concurrently, you might not be able to run the CANCEL command until another query finishes\. In that case, run the CANCEL command using a different workload management query queue\.

By using workload management, you can run queries in different query queues so that you don't need to wait for another query to complete\. The workload manager creates a separate queue, called the Superuser queue, that you can use for troubleshooting\. To use the Superuser queue, log on a superuser and set the query group to 'superuser' using the SET command\. After running your commands, reset the query group using the RESET command\.

To cancel a query using the Superuser queue, run these commands\.

```
SET query_group TO 'superuser';
CANCEL 610;
RESET query_group;
```