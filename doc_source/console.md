# Getting started with the Amazon Redshift console<a name="console"></a>

After you have signed in to the Amazon Redshift console, you can create and manage all Amazon Redshift objects, including clusters, databases, and nodes\. You can also view queries, run queries, and perform other data definition language \(DDL\) and data manipulation language \(DML\) operations\.

If you are a first\-time user of Amazon Redshift, we recommend that you begin by going to the **Dashboard**, **Clusters**, and **query editor v2** pages to get started using the console\. 

To get started with the Amazon Redshift console, watch the following video\. 

[![AWS Videos](http://img.youtube.com/vi/https://www.youtube.com/embed/fr-sAHyKjE0/0.jpg)](http://www.youtube.com/watch?v=https://www.youtube.com/embed/fr-sAHyKjE0)

Following, you can find a screenshot of the Amazon Redshift console and descriptions of its sections\.

![\[Console showing navigation pane\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/console-nav-menu.png)

Following, you can find descriptions of the navigation pane items of the Amazon Redshift console:
+ **Dashboard** – Check **Cluster metrics** and **Query overview** for insights to metrics data \(such as CPU utilization\) and query information\. Using these can help you determine if your performance data is abnormal over a specified time range\.
+ **Clusters** – View a list of clusters in your AWS account, choose a cluster to start querying, or perform cluster\-related actions\. You can also create a new cluster from this page\.
+ **Queries** – Get information for reference or troubleshooting, such as a list of recent queries and the SQL text for each query\.
+ **Editor** – Run queries on databases hosted on your Amazon Redshift cluster, save queries for reuse, or schedule them to run at a future time \(in the query editor only\)\. 
+ **Datashares** – As a producer account administrator, either authorize consumer accounts to access datashares or choose not to authorize access\. To use an authorized datashare, a consumer account administrator can associate the datashare with either an entire AWS account or specific cluster namespaces in an account\. An administrator can also decline a datashare\.
+ **Config** – Connect to Amazon Redshift clusters from SQL client tools over Java Database Connectivity \(JDBC\) and Open Database Connectivity \(ODBC\) connections\. You can also set up an Amazon Redshift–managed virtual private cloud \(VPC\) endpoint\. Doing this provides a private connection between a VPC based on the Amazon VPC service that contains a cluster and another VPC that is running a client tool\. 
+ **Marketplace** – Get information on other tools or AWS services that work with Amazon Redshift\.
+ **Advisor** – Get specific recommendations about changes you can make to your Amazon Redshift cluster to prioritize your optimizations\.
+ **Alarms** – Create alarms on cluster metrics to view performance data and track metrics over a time period that you specify\.
+ **Events** – Track events and get reports on information such as the date the event occurred, a description, or the event source\.
+ **What's new** – View new Amazon Redshift features and product updates\.