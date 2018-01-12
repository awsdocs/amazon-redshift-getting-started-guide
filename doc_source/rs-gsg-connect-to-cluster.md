# Step 5: Connect to the Sample Cluster<a name="rs-gsg-connect-to-cluster"></a>

Now you will connect to your cluster by using a SQL client tool and run a simple query to test the connection\. You can use most SQL client tools that are compatible with PostgreSQL\. For this tutorial, you’ll use the SQL Workbench/J client that you installed in the prerequisites section of this tutorial\. Complete this section by performing the following steps: 

+ [To Get Your Connection String](#rs-gsg-how-to-get-connection-string)

+ [To Connect from SQL Workbench/J to Your Cluster](#rs-gsg-how-to-connect-from-workbench)

After you complete this step, you can determine whether you want to load sample data from Amazon S3 in [Step 6: Load Sample Data from Amazon S3](rs-gsg-create-sample-db.md) or find more information about Amazon Redshift and reset your environment at [Where Do I Go From Here?](rs-gsg-clean-up-tasks.md#rs-gsg-where-do-i-go)\.

## To Get Your Connection String<a name="rs-gsg-how-to-get-connection-string"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose `examplecluster` to open it, and make sure you are on the **Configuration** tab\.

1. On the **Configuration** tab, under **Cluster Database Properties**, copy the JDBC URL of the cluster\. 
**Note**  
The endpoint for your cluster is not available until the cluster is created and in the available state\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-mgmt-clusters-cluster-database-properties-jdbc.png)

## To Connect from SQL Workbench/J to Your Cluster<a name="rs-gsg-how-to-connect-from-workbench"></a>

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