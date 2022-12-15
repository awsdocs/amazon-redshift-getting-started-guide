# Prerequisites<a name="prerequisites"></a>

Before you begin setting up an Amazon Redshift cluster, make sure that you complete the following prerequisites: 
+ [Sign up for AWS](#rs-gsg-prereq-signup)
+ [Determine firewall rules](#rs-gsg-prereq-firewall-rules)

## Sign up for AWS<a name="rs-gsg-prereq-signup"></a>

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