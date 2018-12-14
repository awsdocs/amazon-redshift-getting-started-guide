# Getting Started with Amazon Redshift<a name="getting-started"></a>

 Welcome to the *Amazon Redshift Getting Started Guide*\. Amazon Redshift is a fully managed, petabyte\-scale data warehouse service in the cloud\. An Amazon Redshift data warehouse is a collection of computing resources called *nodes*, which are organized into a group called a *cluster*\. Each cluster runs an Amazon Redshift engine and contains one or more databases\. 

 If you are a first\-time user of Amazon Redshift, we recommend that you begin by reading the following sections: 
+ [Amazon Redshift Management Overview](https://docs.aws.amazon.com/redshift/latest/mgmt/overview.html) – This topic provides an overview of Amazon Redshift\.
+ [Service Highlights and Pricing](https://aws.amazon.com/redshift/) – This product detail page provides the Amazon Redshift value proposition, service highlights, and pricing\.
+ [Amazon Redshift Getting Started](https://docs.aws.amazon.com/redshift/latest/gsg/) \(*this guide*\) – This guide provides a tutorial of using Amazon Redshift to create a sample cluster and work with sample data\.

If you are building a proof\-of\-concept solution with Amazon Redshift, we recommend that you read [Building a Proof of Concept for Amazon Redshift](https://docs.aws.amazon.com/redshift/latest/dg/proof-of-concept-playbook.html)\.

 This guide is a tutorial designed to walk you through the process of creating a sample Amazon Redshift cluster\. You can use this sample cluster to evaluate the Amazon Redshift service\. In this tutorial, you perform the following steps:  
+ [Step 1: Set Up Prerequisites](rs-gsg-prereq.md)
+ [Step 2: Create an IAM Role](rs-gsg-create-an-iam-role.md)
+ [Step 3: Launch a Sample Amazon Redshift Cluster](rs-gsg-launch-sample-cluster.md)
+ [Step 4: Authorize Access to the Cluster](rs-gsg-authorize-cluster-access.md)
+ [Step 5: Connect to the Sample Cluster and Run Queries](rs-gsg-connect-to-cluster.md)
+ [Step 6: Load Sample Data from Amazon S3](rs-gsg-create-sample-db.md)
+ [Step 7: Find Additional Resources and Reset Your Environment](rs-gsg-clean-up-tasks.md)

After you complete this tutorial, you can find more information about Amazon Redshift and next steps in [Where Do I Go From Here?](rs-gsg-clean-up-tasks.md#rs-gsg-where-do-i-go)

**Important**  
The sample cluster that you create will be running in a live environment\. The on\-demand rate is $0\.25 per hour for using the sample cluster that is designed in this tutorial until you delete it\. For more pricing information, go to [the Amazon Redshift pricing page](https://aws.amazon.com/redshift/pricing/)\. If you have questions or get stuck, you can reach out to the Amazon Redshift team by posting on our [Discussion Forum](https://forums.aws.amazon.com/forum.jspa?forumID=155)\.

 This tutorial is not meant for production environments, and does not discuss options in depth\. After you complete the steps in this tutorial, you can use the [Additional Resources](rs-gsg-clean-up-tasks.md#rs-gsg-additional-resources) section to locate more in\-depth information to plan, deploy, and maintain your clusters, and to work with the data in your data warehouse\. 