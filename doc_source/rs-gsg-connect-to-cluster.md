# Step 4: Grant access to the query editor and run queries<a name="rs-gsg-connect-to-cluster"></a>

 To query databases hosted by your Amazon Redshift cluster, you have two options:

1. Connect to your cluster and run queries on the AWS Management Console with the query editor\. 

   If you use the query editor, you don't have to download and set up an SQL client application\. 

1. Connect to your cluster through an SQL client tool, such as SQL Workbench/J\. For more information about using SQL Workbench/J, see [Connect to your cluster by using SQL Workbench/J](https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html) in the *Amazon Redshift Cluster Management Guide\.* 

Using the Amazon Redshift query editor is the easiest way to run queries on databases hosted by your Amazon Redshift cluster\. After creating your cluster, you can immediately run queries using the Amazon Redshift console\. For details about considerations when using the Amazon Redshift query editor, see [Querying a database using the query editor](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor.html) in the *Amazon Redshift Cluster Management Guide\.*

**Topics**
+ [Grant access to the query editor](#gsg-query-cluster-configure)
+ [Use the query editor](#gsg-using-query-editor)

## Grant access to the query editor<a name="gsg-query-cluster-configure"></a>

To use the Amazon Redshift query editor, you need permission\. To set access, attach the `AmazonRedshiftQueryEditor` and `AmazonRedshiftReadOnlyAccess` IAM policies to the IAM user that you use to access your cluster\.

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

## Use the query editor<a name="gsg-using-query-editor"></a>

 In the following example, you use the query editor to perform the following tasks:
+ Run SQL commands\.
+ View details about how queries run\.
+ Save a query\.
+ Download a query result set\.

**To use the query editor**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

1. On the navigation menu, choose **EDITOR**, then connect to a database in your cluster\. 

   On the **Connect to database** page, there are two ways to authenticate, namely, **Temporary credentials** and **AWS Secrets Manager**\. For this tutorial, choose **Create a new connection** and **Temporary credentials**, then enter the values that you used when you created the cluster, as follows: 
   + **Cluster**: Choose **examplecluster**\.
   + **Database name**: Enter **dev**\.
   + **Database user**: Enter **awsuser**\.

   Then choose **Connect**\. 

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