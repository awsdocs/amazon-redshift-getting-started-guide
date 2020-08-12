# Step 6: Load sample data from Amazon S3<a name="rs-gsg-create-sample-db"></a>

At this point, you have a database called `dev` and you are connected to it\. Next, you create some tables in the database, upload data to the tables, and try a query\. For your convenience, the sample data you load is available in an Amazon S3 bucket\. 

**Note**  
If you're using a SQL client tool, ensure that your SQL client is connected to the cluster\.

After you complete this step, you can find more information about Amazon Redshift and reset your environment at [Where do I go from here?](rs-gsg-clean-up-tasks.md#rs-gsg-where-do-i-go)\.

**To load sample data**

1. Create tables\.

   If you are using the Amazon Redshift query editor, individually copy and run the following create table statements to create tables in the `dev` database\. For more information about the syntax, see [CREATE TABLE](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_TABLE_NEW.html) in the *Amazon Redshift Database Developer Guide*\.

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
   ```

   ```
   create table venue(
   	venueid smallint not null distkey sortkey,
   	venuename varchar(100),
   	venuecity varchar(30),
   	venuestate char(2),
   	venueseats integer);
   ```

   ```
   create table category(
   	catid smallint not null distkey sortkey,
   	catgroup varchar(10),
   	catname varchar(10),
   	catdesc varchar(50));
   ```

   ```
   create table date(
   	dateid smallint not null distkey sortkey,
   	caldate date not null,
   	day character(3) not null,
   	week smallint not null,
   	month character(5) not null,
   	qtr character(5) not null,
   	year smallint not null,
   	holiday boolean default('N'));
   ```

   ```
   create table event(
   	eventid integer not null distkey,
   	venueid smallint not null,
   	catid smallint not null,
   	dateid smallint not null sortkey,
   	eventname varchar(200),
   	starttime timestamp);
   ```

   ```
   create table listing(
   	listid integer not null distkey,
   	sellerid integer not null,
   	eventid integer not null,
   	dateid smallint not null  sortkey,
   	numtickets smallint not null,
   	priceperticket decimal(8,2),
   	totalprice decimal(8,2),
   	listtime timestamp);
   ```

   ```
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
We recommend using the COPY command to load large datasets into Amazon Redshift from Amazon S3 or DynamoDB\. For more information about COPY syntax, see [COPY](https://docs.aws.amazon.com/redshift/latest/dg/r_COPY.html) in the *Amazon Redshift Database Developer Guide*\. 

   Download file [tickitdb\.zip](samples/tickitdb.zip) that contains individual sample data files\. Unzip and load the individual files to a `tickit` folder in your Amazon S3 bucket in your AWS Region\. Edit the COPY commands in this tutorial to point to the files in your Amazon S3 bucket\. For information about how to manage files with Amazon S3, see [Creating and configuring an S3 Bucket](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-configure-bucket.html) in the *Amazon Simple Storage Service Console User Guide*\. 

   To load the sample data, you must provide authentication for your cluster to access Amazon S3 on your behalf\. You can provide either role\-based authentication or key\-based authentication\. We recommend using role\-based authentication\. For more information about both types of authentication, see [CREDENTIALS](https://docs.aws.amazon.com/redshift/latest/dg/copy-parameters-credentials.html) in the *Amazon Redshift Database Developer Guide\.*

   For this step, you provide authentication by referencing the IAM role that you created and then attached to your cluster in previous steps\.
**Note**  
If you don't have proper permissions to access Amazon S3, you receive the following error message when running the COPY command: `S3ServiceException: Access Denied`\. For information about IAM permissions for the COPY command, see [COPY](https://docs.aws.amazon.com/redshift/latest/dg/copy-usage_notes-access-permissions.html) in the *Amazon Redshift Database Developer Guide*\.

   The COPY commands include a placeholder for the Amazon Resource Name \(ARN\) for the IAM role, your bucket name, and an AWS Region, as shown in the following example\.

   ```
   copy users from 's3://<myBucket>/tickit/allusers_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region '<aws-region>';
   ```

   To authorize access using an IAM role, replace `<iam-role-arn>` in the CREDENTIALS parameter string with the role ARN for the IAM role that you created in [Step 2: Create an IAM role](rs-gsg-create-an-iam-role.md)\.

    Your COPY command looks similar to the following example\. 

   ```
   copy users from 's3://<myBucket>/tickit/allusers_pipe.txt' 
   credentials 'aws_iam_role=arn:aws:iam::123456789012:role/myRedshiftRole' 
   delimiter '|' region '<aws-region>';
   ```

   To load the sample data, replace *<myBucket>*, *<iam\-role\-arn>*, and *<aws\-region>* in the following COPY commands with your values\. If you are using the Amazon Redshift query editor, individually run the following commands\.

   ```
   copy users from 's3://<myBucket>/tickit/allusers_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region '<aws-region>';
   ```

   ```
   copy venue from 's3://<myBucket>/tickit/venue_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region '<aws-region>';
   ```

   ```
   copy category from 's3://<myBucket>/tickit/category_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region '<aws-region>';
   ```

   ```
   copy date from 's3://<myBucket>/tickit/date2008_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region '<aws-region>';
   ```

   ```
   copy event from 's3://<myBucket>/tickit/allevents_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' timeformat 'YYYY-MM-DD HH:MI:SS' region '<aws-region>';
   ```

   ```
   copy listing from 's3://<myBucket>/tickit/listings_pipe.txt' 
   credentials 'aws_iam_role=<iam-role-arn>' 
   delimiter '|' region '<aws-region>';
   ```

   ```
   copy sales from 's3://<myBucket>/tickit/sales_tab.txt'
   credentials 'aws_iam_role=<iam-role-arn>'
   delimiter '\t' timeformat 'MM/DD/YYYY HH:MI:SS' region '<aws-region>';
   ```

1. Now try the example queries\. For more information, see [SELECT](https://docs.aws.amazon.com/redshift/latest/dg/r_SELECT_synopsis.html) in the *Amazon Redshift Developer Guide*\.

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