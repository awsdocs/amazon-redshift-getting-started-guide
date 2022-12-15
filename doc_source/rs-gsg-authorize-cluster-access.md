# Step 2: Configure inbound rules for SQL clients<a name="rs-gsg-authorize-cluster-access"></a>

Later in this tutorial, you access your cluster from within a virtual private cloud \(VPC\) based on the Amazon VPC service\. However, if you use an SQL client from outside your firewall to access the cluster, make sure that you grant inbound access\. 

You can skip this step if you plan to access the cluster with the Amazon Redshift query editor from within your VPC\.

**To check your firewall and grant inbound access to your cluster**

1. Check your firewall rules if your cluster needs to be accessed from outside a firewall\. For example, your client might be an Amazon Elastic Compute Cloud \(Amazon EC2\) instance or an external computer\. 

   For more information on firewall rules, see [Security group rules](AWSEC2/latest/UserGuide/security-group-rules.html) in the *Amazon EC2 User Guide for Linux Instances*\.

1. To access from an Amazon EC2 external client, add an ingress rule to the security group attached to your cluster that allows inbound traffic\. You add Amazon EC2 security group rules in the Amazon EC2 console\. For example, a CIDR/IP of 192\.0\.2\.0/24 allows clients in that IP address range to connect to your cluster\. Find out the correct CIDR/IP for your environment\.