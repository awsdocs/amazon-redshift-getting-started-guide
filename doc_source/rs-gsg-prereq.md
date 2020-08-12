# Step 1: Set up prerequisites<a name="rs-gsg-prereq"></a>

 Before you begin setting up an Amazon Redshift cluster, make sure that you complete the following prerequisites in this section: 
+ [Sign up for AWS](#rs-gsg-prereq-signup)
+ [Determine firewall rules](#rs-gsg-prereq-firewall-rules)

## Sign up for AWS<a name="rs-gsg-prereq-signup"></a>

If you don't already have an AWS account, you must sign up for one\. If you already have an account, you can skip this prerequisite and use your existing account\.

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

## Determine firewall rules<a name="rs-gsg-prereq-firewall-rules"></a>

As part of this tutorial, you specify a port when you launch your Amazon Redshift cluster\. You also create an inbound ingress rule in a security group to allow access through the port to your cluster\.

If your client computer is behind a firewall, you need to know an open port that you can use\. This open port enables you to connect to the cluster from a SQL client tool and run queries\. If you do not know this, you should work with someone who understands your network firewall rules to determine an open port in your firewall\. Though Amazon Redshift uses port 5439 by default, the connection doesn't work if that port is not open in your firewall\. You can't change the port number for your Amazon Redshift cluster after it is created\. Thus, make sure that you specify an open port that works in your environment during the launch process\.