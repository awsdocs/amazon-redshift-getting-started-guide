# Step 5: Connect to the Sample Cluster and Run Queries<a name="rs-gsg-connect-to-cluster"></a>

To query databases hosted by your Amazon Redshift cluster, you have two options:
+ Connect to your cluster and run queries on the AWS Management Console with the Query Editor\. 

  If you use the Query Editor, you don't have to download and set up a SQL client application\. 
+ Connect to your cluster through a SQL client tool, such as SQL Workbench/j\. 

**Topics**
+ [Querying a Database Using the Query Editor](#gsg-query-editor)
+ [Querying a Database Using a SQL Client](#connect-using-sql-client)

## Querying a Database Using the Query Editor<a name="gsg-query-editor"></a>

Using the Query Editor is the easiest way to run queries on databases hosted by your Amazon Redshift cluster\. After creating your cluster, you can immediately run queries by using the Query Editor on the Amazon Redshift console\.

The following cluster node types support the Query Editor:
+ DC1\.8xlarge
+ DC2\.large
+ DC2\.8xlarge
+ DS2\.8xlarge

Using the Query Editor, you can do the following:
+ Run single SQL statement queries\.
+ Download result sets as large as 100 MB to a comma\-separated value \(CSV\) file\.
+ Save queries for reuse\. You can't save queries in the EU \(Paris\) Region or the Asia Pacific \(Osaka\-Local\) Region\.
+ View query execution details for user\-defined tables\.

### Query Editor Considerations<a name="gsg-query-editor-considerations"></a>

Be aware of the following considerations when you use the Query Editor:
+ Up to 50 users can connect to a cluster with the Query Editor at the same time\.
+ Up to 500 users can connect to a cluster simultaneously\. This total includes the users connecting through the Query Editor\.
+ Up to 50 workload management \(WLM\) query slots can be active at the same time\. For more information about query slots, see [Implementing Workload Management](https://docs.aws.amazon.com/redshift/latest/dg/cm-c-implementing-workload-management.html)\.
+ Query Editor only runs short queries that can complete within two minutes\. 
+ Query result sets are paginated with 100 rows per page\.
+ You can't use the Query Editor with Enhanced VPC routing\. 
+ You can't use transactions in the Query Editor\. For more information about transactions, see [BEGIN](https://docs.aws.amazon.com/redshift/latest/dg/r_BEGIN.html) in the *Amazon Redshift Database Developer Guide\.*

### Enabling Access to the Query Editor<a name="gsg-query-cluster-configure"></a>

To access the Query Editor, you need permission\. To enable access, attach the `AmazonRedshiftQueryEditor` and `AmazonRedshiftReadOnlyAccess` policies for AWS Identity and Access Management \(IAM\) to the AWS account that you use to access your cluster\.

If you have already created an IAM user to access Amazon Redshift, you can attach the `AmazonRedshiftQueryEditor` and `AmazonRedshiftReadOnlyAccess` policies to that user\. If you haven't created an IAM user yet, create one and attach the policies to the IAM user\.

**To attach the required IAM policies for the Query Editor**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users**\.

1. Choose the user that needs access to the Query Editor\.

1. Choose **Add permissions**\.

1. Choose **Attach existing policies directly**\.

1. For **Policy names**, choose **AmazonRedshiftQueryEditor** and **AmazonRedshiftReadOnlyAccess**\.

1. Choose **Next: Review**\.

1. Choose **Add permissions**\.

### Using the Query Editor<a name="gsg-using-query-editor"></a>

 In the following example, you use the Query Editor to perform the following tasks:
+ Run SQL commands\.
+ View query execution details\.
+ Save a query\.
+ Download a query result set\.

**To use the Query Editor**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

1. In the navigation pane, choose **Query Editor**\.

1. In the Credentials dialog, enter the following values and then choose **Connect**:
   + **Cluster**: Choose **redshift\-cluster\-1**\.
   + **Database**: **dev**\.
   + **Database user**: **awsuser**
   + **Password**: Enter the password you specified when you launched the cluster\.

1. For **Schema**, choose **public **to create a new table based on that schema\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-qe-overview.png)

1. Enter the following in the Query Editor window and choose **Run query** to create a new table\.

   ```
   create table shoes(
   shoetype varchar (10),
   color varchar(10));
   ```

1. Choose **Clear**\.

1. Enter the following command in the Query Editor window and choose **Run query** to add rows to the table\.

   ```
   insert into shoes values 
   ('loafers', 'brown'),
   ('sandals', 'black');
   ```

1. Choose **Clear**\.

1. Enter the following command in the Query Editor window and choose **Run query** to query the new table\.

   ```
   select * from shoes;                                       
   ```

   You should see the following results\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-qe-example1.png)

## Querying a Database Using a SQL Client<a name="connect-using-sql-client"></a>

Now you will connect to your cluster by using a SQL client tool and run a simple query to test the connection\. You can use most SQL client tools that are compatible with PostgreSQL\. For this tutorial, you’ll use the SQL Workbench/J client that you installed in the prerequisites section of this tutorial\. Complete this section by performing the following steps: 
+ [Install SQL Client Drivers and Tools](#rs-gsg-sql-client)
+ [To Get Your Connection String](#rs-gsg-how-to-get-connection-string)
+ [To Connect from SQL Workbench/J to Your Cluster](#rs-gsg-how-to-connect-from-workbench)

After you complete this step, you can determine whether you want to load sample data from Amazon S3 in [Step 6: Load Sample Data from Amazon S3](rs-gsg-create-sample-db.md) or find more information about Amazon Redshift and reset your environment at [Where Do I Go From Here?](rs-gsg-clean-up-tasks.md#rs-gsg-where-do-i-go)\.

### Install SQL Client Drivers and Tools<a name="rs-gsg-sql-client"></a>

You can use most SQL client tools with Amazon Redshift JDBC or ODBC drivers to connect to an Amazon Redshift cluster\. In this tutorial, we show you how to connect using SQL Workbench/J, a free, DBMS\-independent, cross\-platform SQL query tool\. If you plan to use SQL Workbench/J to complete this tutorial, follow the steps below to get set up with the Amazon Redshift JDBC driver and SQL Workbench/J\. For more complete instructions for installing SQL Workbench/J, go to [Setting Up the SQL Workbench/J Client](https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html) in the *Amazon Redshift Cluster Management Guide*\. If you use an Amazon EC2 instance as your client computer, you will need to install SQL Workbench/J and the required drivers on the instance\.

**Note**  
You must install any third\-party database tools that you want to use with your clusters; Amazon Redshift does not provide or install any third\-party tools or libraries\.

#### To Install SQL Workbench/J on Your Client Computer<a name="rs-gsg-how-to-install-sql-client-drivers-and-tools"></a>

1. Review the [SQL Workbench/J software license](http://www.sql-workbench.net/manual/license.html#license-restrictions)\.

1. Go to the [SQL Workbench/J website](http://www.sql-workbench.net/) and download the appropriate package for your operating system\.

1. Go to the [Installing and starting SQL Workbench/J page](http://www.sql-workbench.net/manual/install.html) and install SQL Workbench/J\.
**Important**  
Note the Java runtime version prerequisites for SQL Workbench/J and ensure you are using that version, otherwise, this client application will not run\.

1. Go to [Configure a JDBC Connection](https://docs.aws.amazon.com/redshift/latest/mgmt/configure-jdbc-connection.html) and download an Amazon Redshift JDBC driver to enable SQL Workbench/J to connect to your cluster\.

For more information about using the Amazon Redshift JDBC or ODBC drivers, see [Configuring Connections in Amazon Redshift](https://docs.aws.amazon.com/redshift/latest/mgmt/configuring-connections.html)\.

### To Get Your Connection String<a name="rs-gsg-how-to-get-connection-string"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose `examplecluster` to open it, and make sure you are on the **Configuration** tab\.

1. On the **Configuration** tab, under **Cluster Database Properties**, copy the JDBC URL of the cluster\. 
**Note**  
The endpoint for your cluster is not available until the cluster is created and in the available state\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-mgmt-clusters-cluster-database-properties-jdbc.png)

### To Connect from SQL Workbench/J to Your Cluster<a name="rs-gsg-how-to-connect-from-workbench"></a>

This step assumes you installed SQL Workbench/J in [Step 1: Set Up Prerequisites](rs-gsg-prereq.md)\.

1. Open SQL Workbench/J\.

1. Choose **File**, and then choose **Connect window**\.

1. Choose **Create a new connection profile**\.

1. In the **New profile** text box, type a name for the profile\.

1. Choose **Manage Drivers**\. The **Manage Drivers** dialog opens\.

1. Choose the **Create a new entry** button\. In the **Name** text box, type a name for the driver\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/jdbc-manage-drivers.png)

   Choose the folder icon next to the **Library** box, navigate to the location of the driver, select it, and then choose **Open**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/redshift_jdbc_file.png)

   If the **Please select one driver** dialog box displays, select **com\.amazon\.redshift\.jdbc4\.Driver** or **com\.amazon\.redshift\.jdbc41\.Driver** and choose **OK**\. SQL Workbench/J automatically completes the **Classname** box\. Leave the **Sample URL** box blank, and then choose **OK**\. 

1. In the **Driver** box, choose the driver you just added\.

1. In **URL**, copy the JDBC URL from the Amazon Redshift console and paste it here\.

1. In **Username**, type *masteruser*\.

1. In **Password**, type the password associated with the master user account\.

1. Choose the **Autocommit** box\. 

1. Choose the **Save profile list** icon, as shown below:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/sql_workbench_save.png)

1. Choose **OK**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/redshift_driver_sql_workbench.png)

1. Enter the following command in the query window and choose **SQL**, **Execute Current** to add rows to the table\.

   ```
   create table shoes(
   shoetype varchar (10),
   color varchar(10));
   ```

1. Run the following command to add rows to the table\.

   ```
   insert into shoes values 
   ('loafers', 'brown'),
   ('sandals', 'black');
   ```

1. Run the following command to query the new table\.

   ```
   select * from shoes;                                       
   ```