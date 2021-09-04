# Determine the process ID of a running query<a name="determine_pid"></a>

You might need to find the PID for a query that is still running\. For example, you need the PID if you need to cancel a query that is taking too long to run\. You can query the STV\_RECENTS system table to obtain a list of process IDs for running queries, along with the corresponding query string\. If your query returns multiple PIDs, you can look at the query text to determine which PID you need\.

To determine the PID of a running query, run the following SELECT statement\.

```
SELECT pid, user_name, starttime, query
FROM stv_recents
WHERE status='Running';
```