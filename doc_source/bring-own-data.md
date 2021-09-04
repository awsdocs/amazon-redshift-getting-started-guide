# Bringing your own data to Amazon Redshift<a name="bring-own-data"></a>

In this tutorial, you walk through the process to create an Amazon Redshift cluster by bringing your own dataset to Amazon Redshift\. You can use this sample cluster to evaluate the Amazon Redshift service\.

Before you begin setting up an Amazon Redshift cluster, make sure that you complete the [Sign up for AWS](getting-started.md#rs-gsg-prereq-signup) and [Determine firewall rules](getting-started.md#rs-gsg-prereq-firewall-rules)\.

In this tutorial, you perform the steps shown following\.

![\[The steps in this tutorial, outlined following\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/getting-started-bring-own-data.png)

**Important**  
The sample cluster that you create runs in a live environment\. The on\-demand rate is $0\.25 per hour for using the sample cluster that is designed in this tutorial until you delete it\. For more pricing information, go to [the Amazon Redshift pricing page](https://aws.amazon.com/redshift/pricing/)\. If you have questions or get stuck, you can contact the Amazon Redshift team by posting on our [Discussion forum](https://forums.aws.amazon.com/forum.jspa?forumID=155)\.

This tutorial isn't meant for production environments and doesn't discuss options in depth\. After you complete the steps in this tutorial, you can use [Additional resources](additional-resources.md) to find more in\-depth information\. This information can help you plan, deploy, and maintain your clusters, and work with the data in your data warehouse\. 

**Topics**
+ [Step 1: Create an IAM role](rs-gsg-create-an-iam-role.md)
+ [Step 2: Create a sample Amazon Redshift cluster](rs-gsg-launch-sample-cluster.md)
+ [Step 3: Configure inbound rules for SQL clients](rs-gsg-authorize-cluster-access.md)
+ [Step 4: Grant access to the query editor and run queries](rs-gsg-connect-to-cluster.md)
+ [Step 5: Load sample data from Amazon S3](rs-gsg-create-sample-db.md)
+ [Step 6: Try example queries using the query editor](rs-gsg-try-query.md)
+ [Step 7: Reset your environment](rs-gsg-clean-up-tasks.md)