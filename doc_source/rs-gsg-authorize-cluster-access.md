# Step 4: Authorize access to the cluster<a name="rs-gsg-authorize-cluster-access"></a>

**Note**  
A new console is available for Amazon Redshift\. Choose either the **New console** or the **Original console** instructions based on the console that you are using\. The **New console** instructions are open by default\.

## New console<a name="authorize-cluster-sample"></a>

Later in this tutorial, you access your cluster from within a VPC\. However, if you use an SQL client from outside your firewall to access the cluster, you must grant inbound access\. 

You can skip this step if you plan to access the cluster with the Amazon Redshift query editor from within your VPC\.

**To check your firewall and grant inbound access to your cluster**

1. Check your firewall rules if your cluster needs to be accessed from outside a firewall\. For example, your client might be an Amazon EC2 instance or an external computer\. 

1. To access from an Amazon EC2 external client, add an ingress rule to the security group attached to your cluster that allows inbound traffic\. You add Amazon EC2 security group rules in the Amazon EC2 console\. For example, a CIDR/IP of 192\.0\.2\.0/24 allows clients in that IP address range to connect to your cluster\. You need to find out the correct CIDR/IP for your environment\.

## Original console<a name="rs-gsg-how-to-authorize-access-vpc-security-group"></a>

In the previous step, you launched your Amazon Redshift cluster\. Before you can connect to the cluster, you need to configure a security group to authorize access\.  

**To configure the VPC security group \(EC2\-VPC platform\)**

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose **examplecluster** to open it, and make sure that you are on the **Configuration** tab\.

1. Under **Cluster Properties**, for **VPC Security Groups**, choose your security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-vpc-security-group.png)

1. After your security group opens in the Amazon EC2 console, choose the **Inbound** tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-select.png)

1. Choose **Edit**, **Add Rule**, and enter the following, then choose **Save**: 
   + **Type**: **Custom TCP Rule**\.
   + **Protocol**: **TCP**\.
   + **Port Range**: Enter the same port number that you used when you launched the cluster\. The default port for Amazon Redshift is `5439`, but your port might be different\.
   + **Source**: Select **Custom**, then enter `0.0.0.0/0`\.
**Important**  
Using 0\.0\.0\.0/0 is not recommended for anything other than demonstration purposes because it allows access from any computer on the internet\. In a real environment, you create inbound rules based on your own network settings\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-authorize.png)