# Step 2: Try example queries using the query editors<a name="rs-gsg-sample-data-load-query"></a>

When Amazon Redshift is creating your Amazon Redshift cluster, it automatically uploads the sample dataset Tickit\. Cluster creation might take a few minutes to complete\. After creation completes, the cluster status becomes ACTIVE\. You can view the sample Tickit tables from the sample dataset\.

## Using the query editor<a name="rs-gsg-sample-data-load-query-v2"></a>

You can view the sample Tickit tables in the query editor v2 by choosing the cluster, the `dev` database, and `public` schema\.

After the Amazon Redshift cluster is created, in **Connect to Amazon Redshift clusters**, choose **Query data**\. 

From the query editor v2, connect to a database, and choose the cluster name in the tree\-view panel\. If prompted, enter the connection parameters\.

When you connect to a cluster and its databases, you provide a  **Database** name and **User name**\. You also provide parameters required for one of the following authentication methods:

**Database user name and password**  
With this method, also provide a **Password** for the database that you are connecting to\. 

**Temporary credentials**  
With this method, query editor v2, generates a temporary password to connect to the database\. 

When you select a cluster with query editor v2, depending on the context, you can create, edit, and delete connections using the context \(right\-click\) menu\.

By default, Amazon Redshift creates a default database named `dev` and a default schema named `public`\. To view the individual data files of the sample dataset, choose a cluster, go to the query editor v2, and choose the `dev` database, `public` schema, then `Tables`\.

Alternatively, in the navigation pane, choose **CLUSTERS** and the cluster you want query data on\. Then under **Query data**, choose either **Query in query editor** or **Query in query editor v2** to query data in your specified query editor\.

![\[Screenshot of the console: Query data under Connect to Amazon Redshift clusters\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/query-data.png)

## Trying example queries<a name="rs-gsg-sample-data-load-query-sample"></a>

Try some example queries in one of the query editors, as shown following\. For more information on working with the SELECT command, see [SELECT](https://docs.aws.amazon.com/redshift/latest/dg/r_SELECT_synopsis.html) in the Amazon Redshift Database Developer Guide\.

```
-- Find total sales on a given calendar date.
SELECT sum(qtysold) 
FROM   sales, date 
WHERE  sales.dateid = date.dateid 
AND    caldate = '2008-01-05';

-- Find top 10 buyers by quantity.
SELECT firstname, lastname, total_quantity 
FROM   (SELECT buyerid, sum(qtysold) total_quantity
        FROM  sales
        GROUP BY buyerid
        ORDER BY total_quantity desc limit 10) Q, users
WHERE Q.buyerid = userid
ORDER BY Q.total_quantity desc;

-- Find events in the 99.9 percentile in terms of all time gross sales.
SELECT eventname, total_price 
FROM  (SELECT eventid, total_price, ntile(1000) over(order by total_price desc) as percentile 
       FROM (SELECT eventid, sum(pricepaid) total_price
             FROM   sales
             GROUP BY eventid)) Q, event E
       WHERE Q.eventid = E.eventid
       AND percentile = 1
ORDER BY total_price desc;
```

After you complete the steps in this tutorial, you can use [Additional resources](additional-resources.md) to find more in\-depth information\. This information can help you plan, deploy, and maintain your clusters, and work with the data in your data warehouse\. 

You can also try the [Bringing your own data to Amazon Redshift](bring-own-data.md) tutorial to create a cluster with your own dataset\.