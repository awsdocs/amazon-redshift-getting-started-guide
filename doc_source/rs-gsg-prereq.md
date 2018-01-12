# Step 1: Set Up Prerequisites<a name="rs-gsg-prereq"></a>

 Before you begin setting up an Amazon Redshift cluster, make sure that you complete the following prerequisites in this section: 

+ [Sign Up for AWS](#rs-gsg-prereq-signup)

+ [Install SQL Client Drivers and Tools](#rs-gsg-prereq-sql-client)

+ [Determine Firewall Rules](#rs-gsg-prereq-firewall-rules)

## Sign Up for AWS<a name="rs-gsg-prereq-signup"></a>

If you don’t already have an AWS account, you must sign up for one\. If you already have an account, you can skip this prerequisite and use your existing account\.

1. Open [https://aws\.amazon\.com/](https://aws.amazon.com/), and then choose **Create an AWS Account**\.
**Note**  
This might be unavailable in your browser if you previously signed into the AWS Management Console\. In that case, choose **Sign in to a different account**, and then choose **Create a new AWS account**\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a PIN using the phone keypad\.

## Install SQL Client Drivers and Tools<a name="rs-gsg-prereq-sql-client"></a>

You can use most SQL client tools with Amazon Redshift JDBC or ODBC drivers to connect to an Amazon Redshift cluster\. In this tutorial, we show you how to connect using SQL Workbench/J, a free, DBMS\-independent, cross\-platform SQL query tool\. If you plan to use SQL Workbench/J to complete this tutorial, follow the steps below to get set up with the Amazon Redshift JDBC driver and SQL Workbench/J\. For more complete instructions for installing SQL Workbench/J, go to [Setting Up the SQL Workbench/J Client](http://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html) in the *Amazon Redshift Cluster Management Guide*\. If you use an Amazon EC2 instance as your client computer, you will need to install SQL Workbench/J and the required drivers on the instance\.

**Note**  
You must install any third\-party database tools that you want to use with your clusters; Amazon Redshift does not provide or install any third\-party tools or libraries\.

### To Install SQL Workbench/J on Your Client Computer<a name="rs-gsg-how-to-install-sql-client-drivers-and-tools"></a>

1. Review the [SQL Workbench/J software license](http://www.sql-workbench.net/manual/license.html#license-restrictions)\.

1. Go to the [SQL Workbench/J website](http://www.sql-workbench.net/) and download the appropriate package for your operating system\.

1. Go to the [Installing and starting SQL Workbench/J page](http://www.sql-workbench.net/manual/install.html) and install SQL Workbench/J\.
**Important**  
Note the Java runtime version prerequisites for SQL Workbench/J and ensure you are using that version, otherwise, this client application will not run\.

1. Go to [Configure a JDBC Connection](http://docs.aws.amazon.com/redshift/latest/mgmt/configure-jdbc-connection.html) and download an Amazon Redshift JDBC driver to enable SQL Workbench/J to connect to your cluster\.

For more information about using the Amazon Redshift JDBC or ODBC drivers, see [Configuring Connections in Amazon Redshift](http://docs.aws.amazon.com/redshift/latest/mgmt/configuring-connections.html)\.

## Determine Firewall Rules<a name="rs-gsg-prereq-firewall-rules"></a>

As part of this tutorial, you will specify a port when you launch your Amazon Redshift cluster\. You will also create an inbound ingress rule in a security group to allow access through the port to your cluster\.

If your client computer is behind a firewall, you need to know an open port that you can use so you can connect to the cluster from a SQL client tool and run queries\. If you do not know this, you should work with someone who understands your network firewall rules to determine an open port in your firewall\. Though Amazon Redshift uses port 5439 by default, the connection will not work if that port is not open in your firewall\. Because you cannot change the port number for your Amazon Redshift cluster after it is created, make sure that you specify an open port that will work in your environment during the launch process\.