# Step 2: Try example queries using the query editor<a name="rs-gsg-sample-data-load-query"></a>

After the Amazon Redshift cluster is created, in **Connect to Amazon Redshift clusters**, choose **Query data**\.  

![\[Screenshot of the console: Query data under Connect to Amazon Redshift clusters\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/sample-data-load.png)

The Amazon Redshift query editor appears\. Amazon Redshift establishes connection with the new cluster that is loaded with the sample dataset\. 

By default, Amazon Redshift shows the database created during cluster creation in **Select database** and the default schema named `public`\. To view the individual data files of the sample dataset, go to the query editor and choose the `dev` database and `public` schema\.

Try some example queries in the query editor, as shown following\. For more information on working with the SELECT command, see [SELECT](https://docs.aws.amazon.com/redshift/latest/dg/r_SELECT_synopsis.html) in the *Amazon Redshift Developer Guide*\.

```
-- Find total sales on a given calendar date.
SELECT sum(qtysold) 
FROM   sales, date 
WHERE  sales.dateid = date.dateid 
AND    caldate = '2008-01-05';
```

```
-- Find top 10 buyers by quantity.
SELECT firstname, lastname, total_quantity 
FROM   (SELECT buyerid, sum(qtysold) total_quantity
        FROM  sales
        GROUP BY buyerid
        ORDER BY total_quantity desc limit 10) Q, users
WHERE Q.buyerid = userid
ORDER BY Q.total_quantity desc;
```

```
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

After you complete the steps in this tutorial, you can use [Additional resources](rs-gsg-additional-resources.md) to find more in\-depth information\. This information can help you plan, deploy, and maintain your clusters, and work with the data in your data warehouse\. 

You can also try the [Bringing your own data to Amazon Redshift](bring-own-data.md) tutorial to create a cluster with your own dataset\.