# Common database tasks<a name="database-tasks"></a>

Following, you can find a description and walkthrough for common tasks so you can begin using Amazon Redshift databases\.

After you connect to the initial cluster `dev` database, you can create a new database\. Independent of whether you choose to use the sample dataset or bring your own data to Amazon Redshift while creating a cluster, Amazon Redshift creates the `dev` database\.

The examples in this section assume the following:
+ You have created an Amazon Redshift cluster\. For more information, see [Amazon Redshift clusters and data loading](data-loading.md)\.
+ You have established a connection to the cluster from your SQL client tool, such as the Amazon Redshift console query editor\. For more information, see [Step 3: Grant access to one of the query editors and run queries](rs-gsg-connect-to-cluster.md)\.

**Important**  
The cluster that you deployed for this exercise runs in a live environment\. As long as it's running, it accrues charges to your AWS account\. For pricing information, see [the Amazon Redshift pricing page](https://aws.amazon.com/redshift/pricing/)\.   
To avoid unnecessary charges, delete your cluster when you are done with it\. The final step of the exercise explains how to do so\. 