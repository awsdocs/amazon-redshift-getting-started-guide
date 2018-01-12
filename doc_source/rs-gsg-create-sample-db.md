# Step 6: Load Sample Data from Amazon S3<a name="rs-gsg-create-sample-db"></a>

At this point you have a database called `dev` and you are connected to it\. Now you will create some tables in the database, upload data to the tables, and try a query\. For your convenience, the sample data you will load is available in an Amazon S3 bucket\. 

**Note**  
Before you proceed, ensure that your SQL Workbench/J client is connected to the cluster\.

After you complete this step, you can find more information about Amazon Redshift and reset your environment at [Where Do I Go From Here?](rs-gsg-clean-up-tasks.md#rs-gsg-where-do-i-go)\.

1. Create tables\.

   Copy and execute the following create table statements to create tables in the `dev` database\. For more information about the syntax, go to [CREATE TABLE](http://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_TABLE_NEW.html) in the *Amazon Redshift Database Developer Guide*\.

   ```
   create table users(
   	userid integer not null distkey sortkey,
   	username char(8),
   	firstname varchar(30),
   	lastname varchar(30),
   	city varchar(30),
   	state char(2),
   	email varchar(100),
   	phone char(14),
   	likesports boolean,
   	liketheatre boolean,
   	likeconcerts boolean,
   	likejazz boolean,
   	likeclassical boolean,
   	likeopera boolean,
   	likerock boolean,
   	likevegas boolean,
   	likebroadway boolean,
   	likemusicals boolean);
   
   create table venue(
   	venueid smallint not null distkey sortkey,
   	venuename varchar(100),
   	venuecity varchar(30),
   	venuestate char(2),
   	venueseats integer);
   
   create table category(
   	catid smallint not null distkey sortkey,
   	catgroup varchar(10),
   	catname varchar(10),
   	catdesc varchar(50));
   
   create table date(
   	dateid smallint not null distkey sortkey,
   	caldate date not null,
   	day character(3) not null,
   	week smallint not null,
   	month character(5) not null,
   	qtr character(5) not null,
   	year smallint not null,
   	holiday boolean default('N'));
   
   create table event(
   	eventid integer not null distkey,
   	venueid smallint not null,
   	catid smallint not null,
   	dateid smallint not null sortkey,
   	eventname varchar(200),
   	starttime timestamp);
   
   create table listing(
   	listid integer not null distkey,
   	sellerid integer not null,
   	eventid integer not null,
   	dateid smallint not null  sortkey,
   	numtickets smallint not null,
   	priceperticket decimal(8,2),
   	totalprice decimal(8,2),
   	listtime timestamp);
   
   create table sales(
   	salesid integer not null,
   	listid integer not null distkey,
   	sellerid integer not null,
   	buyerid integer not null,
   	eventid integer not null,
   	dateid smallint not null sortkey,
   	qtysold smallint not null,
   	pricepaid decimal(8,2),
   	commission decimal(8,2),
   	saletime timestamp);
   ```

1.  Load sample data from Amazon S3 by using the COPY command\. 
**Note**  
 We recommend using the COPY command to load large datasets into Amazon Redshift from Amazon S3 or DynamoDB\. For more information about COPY syntax, see [COPY](http://docs.aws.amazon.com/redshift/latest/dg/r_COPY.html) in the *Amazon Redshift Database Developer Guide*\. 

   The sample data for this tutorial is provided in an Amazon S3 bucket that is owned by Amazon Redshift\. The bucket permissions are configured to allow all authenticated AWS users read access to the sample data files\. 

   To load the sample data, you must provide authentication for your cluster to access Amazon S3 on your behalf\. You can provide either role\-based authentication or key\-based authentication\. We recommend using role\-based authentication\. For more information about both types of authentication, see [CREDENTIALS](http://docs.aws.amazon.com/redshift/latest/dg/copy-parameters-credentials.html) in the Amazon Redshift Database Developer Guide\.

   For this step, you will provide authentication by referencing the IAM role you created and then attached to your cluster in previous steps\.
**Note**  
 If you don’t have proper permissions to access Amazon S3, you receive the following error message when running the COPY command: `S3ServiceException: Access Denied`\.

   The COPY commands include a placeholder for the IAM role ARN, as shown in the following example\.

   ```
   copy users from 's3://awssampledbuswest2/tickit/allusers_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region 'us-west-2';
   ```

   To authorize access using an IAM role, replace *<iam\-role\-arn>* in the CREDENTIALS parameter string with the role ARN for the IAM role you created in [Step 2: Create an IAM Role](rs-gsg-create-an-iam-role.md)\.

    Your COPY command will look similar to the following example\. 

   ```
   copy users from 's3://awssampledbuswest2/tickit/allusers_pipe.txt' 
   credentials 'aws_iam_role=arn:aws:iam::123456789012:role/myRedshiftRole' 
   delimiter '|' region 'us-west-2';
   ```

   To load the sample data, replace *<iam\-role\-arn>* in the following COPY commands with your role ARN\. Then run the commands in your SQL client tool\.

   ```
   copy users from 's3://awssampledbuswest2/tickit/allusers_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region 'us-west-2';
   
   copy venue from 's3://awssampledbuswest2/tickit/venue_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region 'us-west-2';
   
   copy category from 's3://awssampledbuswest2/tickit/category_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region 'us-west-2';
   
   copy date from 's3://awssampledbuswest2/tickit/date2008_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region 'us-west-2';
   
   copy event from 's3://awssampledbuswest2/tickit/allevents_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' timeformat 'YYYY-MM-DD HH:MI:SS' region 'us-west-2';
   
   copy listing from 's3://awssampledbuswest2/tickit/listings_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region 'us-west-2';
   
   copy sales from 's3://awssampledbuswest2/tickit/sales_tab.txt'
   credentials 'aws_iam_role=<iam-role-arn>'
   delimiter '\t' timeformat 'MM/DD/YYYY HH:MI:SS' region 'us-west-2';
   ```

1. Now try the example queries\. For more information, go to [SELECT](http://docs.aws.amazon.com/redshift/latest/dg/r_SELECT_synopsis.html) in the *Amazon Redshift Developer Guide*\.

   ```
   -- Get definition for the sales table.
   SELECT *    
   FROM pg_table_def    
   WHERE tablename = 'sales';    
   
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

1. You can optionally go the Amazon Redshift console to review the queries you executed\. The **Queries** tab shows a list of queries that you executed over a time period you specify\. By default, the console displays queries that have executed in the last 24 hours, including currently executing queries\. 

   + Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

   + In the cluster list in the right pane, choose `examplecluster`\.

   + Choose the **Queries** tab\. 

     The console displays list of queries you executed as shown in the example below\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/cmdws-cluster-query-list.png)

   + To view more information about a query, choose the query ID link in the **Query** column or choose the magnifying glass icon\. 

     The following example shows the details of a query you ran in a previous step\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/cmdws-cluster-query.png)