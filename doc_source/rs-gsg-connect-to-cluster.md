# Step 5: Connect to the sample cluster and run queries<a name="rs-gsg-connect-to-cluster"></a>

To query databases hosted by your Amazon Redshift cluster, you have two options:
+ Connect to your cluster and run queries on the AWS Management Console with the query editor\. 

  If you use the query editor, you don't have to download and set up an SQL client application\. 
+ Connect to your cluster through an SQL client tool, such as SQL Workbench/J\. 

**Topics**
+ [Querying a database using the query editor](#gsg-query-editor)
+ [Querying a database using a SQL client](#connect-using-sql-client)

## Querying a database using the query editor<a name="gsg-query-editor"></a>

Using the query editor is the easiest way to run queries on databases hosted by your Amazon Redshift cluster\. After creating your cluster, you can immediately run queries using the console\. 

The following cluster node types support the query editor:
+ DC1\.8xlarge
+ DC2\.large
+ DC2\.8xlarge
+ DS2\.8xlarge
+ RA3\.4xlarge
+ RA3\.16xlarge

Using the Amazon Redshift console query editor, you can do the following:
+ Run single SQL statement queries\.
+ Download result sets as large as 100 MB to a comma\-separated value \(CSV\) file\.
+ Save queries for reuse\. You can't save queries in the Europe \(Paris\) Region or the Asia Pacific \(Osaka\-Local\) Region\.
+ View query execution details for user\-defined tables\.

### Query editor considerations<a name="gsg-query-editor-considerations"></a>

For details about considerations when using the query editor, see [Querying a database using the query editor](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor.html) in the *Amazon Redshift Cluster Management Guide\.*

### Enabling access to the query editor<a name="gsg-query-cluster-configure"></a>

To access the query editor, you need permission\. To enable access, attach the `AmazonRedshiftQueryEditor` and `AmazonRedshiftReadOnlyAccess` policies for AWS Identity and Access Management \(IAM\) to the IAM user that you use to access your cluster\.

If you have already created an IAM user to access Amazon Redshift, you can attach the `AmazonRedshiftQueryEditor` and `AmazonRedshiftReadOnlyAccess` policies to that user\. If you haven't created an IAM user yet, create one and attach the policies to the IAM user\.

**To attach the required IAM policies for the query editor**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users**\.

1. Choose the user that needs access to the query editor\.

1. Choose **Add permissions**\.

1. Choose **Attach existing policies directly**\.

1. For **Policy names**, choose **AmazonRedshiftQueryEditor** and **AmazonRedshiftReadOnlyAccess**\.

1. Choose **Next: Review**\.

1. Choose **Add permissions**\.

### Using the query editor<a name="gsg-using-query-editor"></a>

 In the following example, you use the query editor to perform the following tasks:
+ Run SQL commands\.
+ View query execution details\.
+ Save a query\.
+ Download a query result set\.

**Note**  
A new console is available for Amazon Redshift\. Choose either the **New console** or the **Original console** instructions based on the console that you are using\. The **New console** instructions are open by default\.

#### New console<a name="query-editor-getting-started"></a>

**To use the query editor**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

1. On the navigation menu, choose **EDITOR**, then connect to a database in your cluster\. 

   On the **Connect to database** window, enter the values you used when you created the cluster as follows: 
   + **Cluster**: Choose **examplecluster**
   + **Database name**: Enter **dev**
   + **Database user**: Enter **awsuser**
   + **Database password**: Enter **password that you specified when you created the cluster**

   Then choose **Connect to database**\. 

1. For **Schema**, choose **public **to create a new table based on that schema\.

1. Enter the following in the query editor window, and choose **Run** to create a new table\.

   ```
   create table shoes(
                   shoetype varchar (10),
                   color varchar(10));
   ```

1. Choose **Clear**\.

1. Enter the following command in the query editor window, and choose **Run** to add rows to the table\.

   ```
   insert into shoes values 
   ('loafers', 'brown'),
   ('sandals', 'black');
   ```

1. Choose **Clear**\.

1. Enter the following command in the query editor window, and choose **Run** to query the new table\.

   ```
   select * from shoes; 
   ```

   The **Query results** displays the results\.    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/redshift/latest/gsg/rs-gsg-connect-to-cluster.html)

1. Choose **Execution** to view the run details\.

1. Choose **Export** to download the query results as a file\. The supported file formats are CSV, TXT, and HTML\.

#### Original console<a name="query-editor-getting-started-originalconsole"></a>

**To use the query editor**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

1. In the navigation pane, choose **Query editor**\.

1. In the **Credentials** dialog box, enter the following values and then choose **Connect**:
   + **Cluster**: Choose **examplecluster**\.
   + **Database**: **dev**\.
   + **Database user**: **awsuser**
   + **Password**: Enter the password that you specified when you launched the cluster\.

1. For **Schema**, choose **public **to create a new table based on that schema\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-qe-overview.png)

1. Enter the following in the Query editor window and choose **Run query** to create a new table\.

   ```
   create table shoes(
   shoetype varchar (10),
   color varchar(10));
   ```

1. Choose **Clear**\.

1. Enter the following command in the Query editor window and choose **Run query** to add rows to the table\.

   ```
   insert into shoes values 
   ('loafers', 'brown'),
   ('sandals', 'black');
   ```

1. Choose **Clear**\.

1. Enter the following command in the Query editor window and choose **Run query** to query the new table\.

   ```
   select * from shoes;                                       
   ```

   You should see the following results\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-qe-example1.png)

## Querying a database using a SQL client<a name="connect-using-sql-client"></a>

Next, you connect to your cluster by using a SQL client tool and run a simple query to test the connection\. You can use most SQL client tools that are compatible with PostgreSQL\. For this tutorial, you use the SQL Workbench/J client\.  Complete this section by performing the following steps: 
+ [Install SQL client drivers and tools](#rs-gsg-sql-client)
+ [To get your connection string](#rs-gsg-how-to-get-connection-string)
+ [To connect from SQL Workbench/J to your cluster](#rs-gsg-how-to-connect-from-workbench)

After you complete this step, you can determine whether you want to load sample data from Amazon S3 in [Step 6: Load sample data from Amazon S3](rs-gsg-create-sample-db.md) or find more information about Amazon Redshift and reset your environment at [Where do I go from here?](rs-gsg-clean-up-tasks.md#rs-gsg-where-do-i-go)\.

### Install SQL client drivers and tools<a name="rs-gsg-sql-client"></a>

You can use most SQL client tools with Amazon Redshift JDBC or ODBC drivers to connect to an Amazon Redshift cluster\. In this tutorial, you connect using SQL Workbench/J, a free, DBMS\-independent, cross\-platform SQL query tool\. If you plan to use SQL Workbench/J to complete this tutorial, use the steps following to set up the Amazon Redshift JDBC driver and SQL Workbench/J\. For more complete instructions for installing SQL Workbench/J, go to [Setting up the SQL Workbench/J client](https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html) in the *Amazon Redshift Cluster Management Guide*\. If you use an Amazon EC2 instance as your client computer, install SQL Workbench/J and the required drivers on the instance\.

**Note**  
Install any third\-party database tools that you want to use with your clusters yourself\. Amazon Redshift doesn't provide or install any third\-party tools or libraries\.

#### To install SQL Workbench/J on your client computer<a name="rs-gsg-how-to-install-sql-client-drivers-and-tools"></a>

1. Review the [SQL Workbench/J software license](http://www.sql-workbench.net/manual/license.html#license-restrictions)\.

1. Go to the [SQL Workbench/J website](http://www.sql-workbench.net/) and download the appropriate package for your operating system\.

1. Go to the [Installing and starting SQL Workbench/J page](http://www.sql-workbench.net/manual/install.html) and install SQL Workbench/J\.
**Important**  
Note the Java runtime version prerequisites for SQL Workbench/J and ensure you are using that version\. Otherwise, the client application doesn't run\.

1. Go to [Configure a JDBC connection](https://docs.aws.amazon.com/redshift/latest/mgmt/configure-jdbc-connection.html) and download an Amazon Redshift JDBC driver to enable SQL Workbench/J to connect to your cluster\.

For more information about using the Amazon Redshift JDBC or ODBC drivers, see [Configuring connections in Amazon Redshift](https://docs.aws.amazon.com/redshift/latest/mgmt/configuring-connections.html)\.

### To get your connection string<a name="rs-gsg-how-to-get-connection-string"></a>

To connect to your cluster with your SQL client tool, you need the cluster connection string\. You can find the cluster connection string in the Amazon Redshift console, on a cluster's details page\.

**Note**  
A new console is available for Amazon Redshift\. Choose either the **New console** or the **Original console** instructions based on the console that you are using\. The **New console** instructions are open by default\.

#### New console<a name="connect-drivers-url-getting-started"></a>

**To find the connection string for a cluster**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

1. On the navigation menu, choose **CLUSTERS**, then choose the cluster name from the list to open its details\. 

1. Choose the **Properties** tab for the cluster, and view the **Connection details** to see the values for **JDBC URL** and **ODBC URL**\. The connection string is based on the AWS Region where the cluster runs\. 

1. Choose **Copy** to copy the string on this page\. 

#### Original console<a name="connect-drivers-url-getting-started-originalconsole"></a>

**To find the connection string for a cluster**

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose **examplecluster** to open it, and make sure that you are on the **Configuration** tab\.

1. On the **Configuration** tab, under **Cluster Database Properties**, copy the JDBC URL of the cluster\. 
**Note**  
The endpoint for your cluster is not available until the cluster is created and in the available state\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-mgmt-clusters-cluster-database-properties-jdbc.png)

### To connect from SQL Workbench/J to your cluster<a name="rs-gsg-how-to-connect-from-workbench"></a>

This step assumes that you installed SQL Workbench/J\.

1. Open SQL Workbench/J\.

1. Choose **File**, and then choose **Connect window**\.

1. Choose **Create a new connection profile**\.

1. For **New profile**, enter a name for the profile\.

1. Choose **Manage Drivers**\. The **Manage Drivers** dialog box opens\.

1. Choose **Create a new entry**\. For **Name**, enter a name for the driver\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/jdbc-manage-drivers.png)

   Choose the folder icon next to the **Library** box, navigate to the location of the driver, choose it, and then choose **Open**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/redshift_jdbc_file.png)

   If the **Please select one driver** dialog box displays, choose **com\.amazon\.redshift\.jdbc4\.Driver** or **com\.amazon\.redshift\.jdbc41\.Driver** and then choose **OK**\. SQL Workbench/J automatically completes the **Classname** box\. Keep **Sample URL** blank, and choose **OK**\. 

1. For **Driver**, choose the driver that you just added\.

1. For **URL**, copy the JDBC URL from the Amazon Redshift console and paste it here\.

1. For **Username**, enter **awsuser** for the master user\.

1. For **Password**, enter the password associated with the master user account\.

1. Choose **Autocommit**\. 

1. Choose the **Save profile list** icon, as shown following\.  
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