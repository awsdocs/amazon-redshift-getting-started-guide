# Amazon Redshift provisioned clusters console<a name="console"></a>

Before you begin setting up an Amazon Redshift cluster, make sure that you complete the following prerequisites: 
+ [Signing up for AWS](#provisioned-prereq-signup)
+ [Determine firewall rules](#rs-gsg-prereq-firewall-rules)

## Signing up for AWS<a name="provisioned-prereq-signup"></a>

If you don't already have an AWS account, sign up for one\. If you already have an account, you can skip this prerequisite and use your existing account\.

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

   When you sign up for an AWS account, an *AWS account root user* is created\. The root user has access to all AWS services and resources in the account\. As a security best practice, [assign administrative access to an administrative user](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html), and use only the root user to perform [tasks that require root user access](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html)\.

## Determine firewall rules<a name="rs-gsg-prereq-firewall-rules"></a>

As part of this tutorial, you specify a port when you launch your Amazon Redshift cluster\. You also create an inbound ingress rule in a security group to allow access through the port to your cluster\.

If your client computer is behind a firewall, make sure that you know an open port that you can use\. Using this open port, you can connect to the cluster from a SQL client tool and run queries\. If you don't know an open port, work with someone who understands your network firewall rules to determine an open port in your firewall\. 

Though Amazon Redshift uses port 5439 by default, the connection doesn't work if that port isn't open in your firewall\. You can't change the port number for your Amazon Redshift cluster after it's created\. Thus, make sure that you specify an open port that works in your environment during the launch process\.

This prerequisite applies only when you bring your own data to Amazon Redshift\. For more information, see [Bringing your own data to Amazon Redshift](bring-own-data.md)\.

After you have signed in to the Amazon Redshift console, you can create and manage all Amazon Redshift objects, including clusters, databases, and nodes\. You can also view queries, run queries, and perform other data definition language \(DDL\) and data manipulation language \(DML\) operations\.

If you are a first\-time user of Amazon Redshift, we recommend that you begin by going to the **Dashboard**, **Clusters**, and **query editor v2** pages to get started using the console\. 

To get started with the Amazon Redshift console, watch the following video\. 

[![AWS Videos](http://img.youtube.com/vi/https://www.youtube.com/embed/fr-sAHyKjE0/0.jpg)](http://www.youtube.com/watch?v=https://www.youtube.com/embed/fr-sAHyKjE0)

Following, you can find descriptions of the navigation pane items of the Amazon Redshift console:
+ **Amazon Redshift serverless** – Access and analyze data without the need to set up, tune, and manage Amazon Redshift provisioned clusters\.
+ **Provisioned clusters dashboard** – Check **Cluster metrics** and **Query overview** for insights to metrics data \(such as CPU utilization\) and query information\. Using these can help you determine if your performance data is abnormal over a specified time range\.
+ **Clusters** – View a list of clusters in your AWS account, choose a cluster to start querying, or perform cluster\-related actions\. You can also create a new cluster from this page\.
+ **Query editor** – Run queries on databases hosted on your Amazon Redshift cluster, save queries for reuse, or schedule them to run at a future time \(in the query editor only\)\. 
+ **Query editor v2** – Use the query editor v2 that is a separate web\-based SQL client application to author and run queries on your Amazon Redshift data warehouse\. You can visualize your results in charts and collaborate by sharing your queries with others on your team\. 
+ **Queries and loads** – Get information for reference or troubleshooting, such as a list of recent queries and the SQL text for each query\.
+ **Datashares** – As a producer account administrator, either authorize consumer accounts to access datashares or choose not to authorize access\. To use an authorized datashare, a consumer account administrator can associate the datashare with either an entire AWS account or specific cluster namespaces in an account\. An administrator can also decline a datashare\.
+ **Configurations** – Connect to Amazon Redshift clusters from SQL client tools over Java Database Connectivity \(JDBC\) and Open Database Connectivity \(ODBC\) connections\. You can also set up an Amazon Redshift–managed virtual private cloud \(VPC\) endpoint\. Doing so provides a private connection between a VPC based on the Amazon VPC service that contains a cluster and another VPC that is running a client tool\. 
+ **Advisor** – Get specific recommendations about changes you can make to your Amazon Redshift cluster to prioritize your optimizations\.
+ **AWS Marketplace** – Get information on other tools or AWS services that work with Amazon Redshift\.
+ **Alarms** – Create alarms on cluster metrics to view performance data and track metrics over a time period that you specify\.
+ **Events** – Track events and get reports on information such as the date the event occurred, a description, or the event source\.
+ **What's new** – View new Amazon Redshift features and product updates\.