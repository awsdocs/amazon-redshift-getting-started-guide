# Getting started with Amazon Redshift<a name="getting-started"></a>

 Welcome to the *Amazon Redshift Getting Started Guide*\. Amazon Redshift is a fully managed, petabyte\-scale data warehouse service in the cloud\. An Amazon Redshift data warehouse is a collection of computing resources called *nodes*, which are organized into a group called a *cluster*\. Each cluster runs an Amazon Redshift engine and contains one or more databases\. 

 If you are a first\-time user of Amazon Redshift, we recommend that you begin by reading the following sections: 
+ [Amazon Redshift management overview](https://docs.aws.amazon.com/redshift/latest/mgmt/overview.html) – This topic provides an overview of Amazon Redshift\.
+ [Service highlights and pricing](https://aws.amazon.com/redshift/) – This product detail page provides details about Amazon Redshift service highlights and pricing\.
+ [Amazon Redshift Getting Started](https://docs.aws.amazon.com/redshift/latest/gsg/) \(*this guide*\) – This guide provides a tutorial of using Amazon Redshift to create a sample cluster and work with sample data\.

This guide is a tutorial that walks you through the process of creating a sample Amazon Redshift cluster\. You can use this sample cluster to evaluate the Amazon Redshift service\. In this tutorial, you perform the following steps:  
+ [Step 1: Set up prerequisites](rs-gsg-prereq.md)
+ [Step 2: Create an IAM role](rs-gsg-create-an-iam-role.md)
+ [Step 3: Create a sample Amazon Redshift cluster](rs-gsg-launch-sample-cluster.md)
+ [Step 4: Authorize access to the cluster](rs-gsg-authorize-cluster-access.md)
+ [Step 5: Grant access to the query editor and run queries](rs-gsg-connect-to-cluster.md)
+ [Step 6: Load sample data from Amazon S3](rs-gsg-create-sample-db.md)
+ [Step 7: Try example queries](rs-gsg-try-query.md)
+ [Step 8: Reset your environment](rs-gsg-clean-up-tasks.md)

After you complete this tutorial, you can find more information about Amazon Redshift and next steps in [Additional resources](rs-gsg-additional-resources.md)\.

**Important**  
The sample cluster that you create runs in a live environment\. The on\-demand rate is $0\.25 per hour for using the sample cluster that is designed in this tutorial until you delete it\. For more pricing information, go to [the Amazon Redshift pricing page](https://aws.amazon.com/redshift/pricing/)\. If you have questions or get stuck, you can reach out to the Amazon Redshift team by posting on our [Discussion forum](https://forums.aws.amazon.com/forum.jspa?forumID=155)\.

This tutorial isn't meant for production environments and doesn't discuss options in depth\. After you complete the steps in this tutorial, you can use [Additional resources](rs-gsg-additional-resources.md) to find more in\-depth information\. This information can help you plan, deploy, and maintain your clusters, and work with the data in your data warehouse\. 