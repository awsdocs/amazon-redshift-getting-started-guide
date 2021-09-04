# Getting started with Amazon Redshift<a name="getting-started"></a>

Welcome to the *Amazon Redshift Getting Started Guide Guide*\. Amazon Redshift is a fully managed, petabyte\-scale data warehouse service in the AWS Cloud\. An Amazon Redshift data warehouse is a collection of computing resources called *nodes*, which are organized into a group called a *cluster*\. Each cluster runs an Amazon Redshift engine and contains one or more databases\. 

 If you are a first\-time user of Amazon Redshift, we recommend that you begin by reading the following sections: 
+ [Amazon Redshift management overview](https://docs.aws.amazon.com/redshift/latest/mgmt/overview.html) – In this topic, you can find an overview of Amazon Redshift\.
+ [Service highlights and pricing](https://aws.amazon.com/redshift/) – On this product detail page, you can find details about Amazon Redshift service highlights and pricing\.
+ [Amazon Redshift Getting Started Guide](https://docs.aws.amazon.com/redshift/latest/gsg/) \(*this guide*\) – In this guide, you can find a tutorial of using Amazon Redshift to create a sample cluster and work with sample data\.

In this guide, you can find tutorials that walk you through one of the following:
+ [Getting started with the Amazon Redshift console](console.md)
+ [Connecting to Amazon Redshift](connection.md)
+ [Getting started with Amazon Redshift clusters and data loading](data-loading.md)
+ [Getting started with common database tasks](database-tasks.md)
+ [Getting started querying your data lake](data-lake.md)
+ [Getting started querying data on remote data sources](federated-query.md)
+ [Getting started accessing data in other Amazon Redshift clusters](datasharing.md)
+ [Getting started training machine learning models with Amazon Redshift data](machine-learning.md)

If your organization is eligible, you might be able to create a cluster under the Amazon Redshift free trial program\. To do this, choose **Free trial** to create a configuration with the dc2\.large node type\. For more information about choosing a free trial, see [Amazon Redshift free trial](http://aws.amazon.com/redshift/free-trial/)\. 

## Prerequisites<a name="prerequisites"></a>

Before you begin setting up an Amazon Redshift cluster, make sure that you complete the following prerequisites: 
+ [Sign up for AWS](#rs-gsg-prereq-signup)
+ [Determine firewall rules](#rs-gsg-prereq-firewall-rules)

### Sign up for AWS<a name="rs-gsg-prereq-signup"></a>

If you don't already have an AWS account, sign up for one\. If you already have an account, you can skip this prerequisite and use your existing account\.

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

### Determine firewall rules<a name="rs-gsg-prereq-firewall-rules"></a>

As part of this tutorial, you specify a port when you launch your Amazon Redshift cluster\. You also create an inbound ingress rule in a security group to allow access through the port to your cluster\.

If your client computer is behind a firewall, make sure that you know an open port that you can use\. Using this open port, you can connect to the cluster from a SQL client tool and run queries\. If you don't know an open port, work with someone who understands your network firewall rules to determine an open port in your firewall\. Though Amazon Redshift uses port 5439 by default, the connection doesn't work if that port isn't open in your firewall\. You can't change the port number for your Amazon Redshift cluster after it's created\. Thus, make sure that you specify an open port that works in your environment during the launch process\.

This prerequisite is only applicable when you bring your own data to Amazon Redshift\. For more information, see [Bringing your own data to Amazon Redshift](bring-own-data.md)\.