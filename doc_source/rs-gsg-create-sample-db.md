# Step 4: Load data from Amazon S3 to Amazon Redshift<a name="rs-gsg-create-sample-db"></a>

Using one of the Amazon Redshift query editors is the easiest way to load data to tables\. After creating your cluster, you can load data from Amazon S3 to your cluster using the Amazon Redshift console\. 

Use the query editor v2 that simplifies the loading of data using the Load data wizard\. For more information, see [Loading your own data from Amazon S3 to Amazon Redshift using the query editor v2](#gsg-load-sample-data-v2)\. Or use the query editor to create tables and load your data\. For more information, see [Loading sample data from Amazon S3 using the query editor](#gsg-load-sample-data-v1)\.

## Loading your own data from Amazon S3 to Amazon Redshift using the query editor v2<a name="gsg-load-sample-data-v2"></a>

To load your own data from Amazon S3 to Amazon Redshift, Amazon Redshift requires an IAM role that has the required privileges to load data from the specified Amazon S3 bucket\.

First, connect to a database\. Next, create some tables in the database\. Then load your own data from Amazon S3 to Amazon Redshift\. For more information on how to work with the query editor v2, see [Working with query editor v2](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2-using.html) in the *Amazon Redshift Cluster Management Guide*\.

The COPY command generated and used in the query editor v2 Load data wizard supports all the parameters available to the COPY command syntax to load data from Amazon S3\. For information about the COPY command and its options used to copy load from Amazon S3, see [COPY from Amazon Simple Storage Service](https://docs.aws.amazon.com/redshift/latest/dg/copy-parameters-data-source-s3.html) in the *Amazon Redshift Database Developer Guide*\.

## Loading sample data from Amazon S3 using the query editor<a name="gsg-load-sample-data-v1"></a>

At this point, you have a database called `dev` and you are connected to it\. Next, you create some tables in the database, upload data to the tables, and try a query\. For your convenience, the sample data that you load is available in an Amazon S3 bucket\. 

**Note**  
If you're using a SQL client tool, ensure that your SQL client is connected to the cluster\.

After you complete this step, you can do the following:
+ Try example queries at [Step 5: Try example queries using the query editor](rs-gsg-try-query.md)\. 
+ Reset your environment at [Step 6: Reset your environment](rs-gsg-clean-up-tasks.md)\.
+ Find more information about Amazon Redshift at [Additional resources](additional-resources.md)\.

**Note**  
To try querying data in the query editor without loading your own data, choose **Load sample data** in **Sample data**\. If you do, Amazon Redshift loads its sample dataset to your Amazon Redshift cluster automatically during cluster creation\.

**To load sample data from Amazon S3**

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
We recommend using the COPY command to load large datasets into Amazon Redshift from Amazon S3 or Amazon DynamoDB\. For more information about COPY syntax, see [COPY](https://docs.aws.amazon.com/redshift/latest/dg/r_COPY.html) in the *Amazon Redshift Database Developer Guide*\. 

   1. Download the file [tickitdb\.zip](samples/tickitdb.zip), which contains individual sample data files\.

   1.  Unzip and load the individual files to a `tickit` folder in your Amazon S3 bucket in your AWS Region\.

   1.  Edit the COPY commands in this tutorial to point to the files in your Amazon S3 bucket\. For information about how to manage files with Amazon S3, see [Creating and configuring an S3 Bucket](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-configure-bucket.html) in the *Amazon Simple Storage Service User Guide*\.

   1. Provide authentication for your cluster to access Amazon S3 on your behalf to load the sample data\. You provide authentication by referencing the IAM role that you created and set as the default for your cluster in previous steps\.

      The COPY commands include a placeholder for the Amazon Resource Name \(ARN\) for the IAM role, your bucket name, and an AWS Region, as shown in the following example\.

      ```
      copy users from 's3://<myBucket>/tickit/allusers_pipe.txt' 
      iam_role default
      delimiter '|' region '<aws-region>';
      ```

       Your COPY command should look similar to the following example\. 

      ```
      copy users from 's3://<myBucket>/tickit/allusers_pipe.txt' 
      iam_role default
      delimiter '|' region '<aws-region>';
      ```

      To load the sample data, replace *`<myBucket>` * and *`<aws-region>`* in the following COPY commands with your values\. If you are using the Amazon Redshift query editor, individually run the following commands\.

      ```
      copy users from 's3://<myBucket>/tickit/allusers_pipe.txt' 
      iam_role default 
      delimiter '|' region '<aws-region>';
      ```

      ```
      copy venue from 's3://<myBucket>/tickit/venue_pipe.txt' 
      iam_role default
      delimiter '|' region '<aws-region>';
      ```

      ```
      copy category from 's3://<myBucket>/tickit/category_pipe.txt' 
      iam_role default
      delimiter '|' region '<aws-region>';
      ```

      ```
      copy date from 's3://<myBucket>/tickit/date2008_pipe.txt' 
      iam_role default
      delimiter '|' region '<aws-region>';
      ```

      ```
      copy event from 's3://<myBucket>/tickit/allevents_pipe.txt' 
      iam_role default
      delimiter '|' timeformat 'YYYY-MM-DD HH:MI:SS' region '<aws-region>';
      ```

      ```
      copy listing from 's3://<myBucket>/tickit/listings_pipe.txt' 
      iam_role default
      delimiter '|' region '<aws-region>';
      ```

      ```
      copy sales from 's3://<myBucket>/tickit/sales_tab.txt'
      iam_role default
      delimiter '\t' timeformat 'MM/DD/YYYY HH:MI:SS' region '<aws-region>';
      ```