# Step 4: Authorize Access to the Cluster<a name="rs-gsg-authorize-cluster-access"></a>

In the previous step, you launched your Amazon Redshift cluster\. Before you can connect to the cluster, you need to configure a security group to authorize access: 
+ If you launched your cluster in the EC2\-VPC platform, follow the steps in [To Configure the VPC Security Group \(EC2\-VPC Platform\)](#rs-gsg-how-to-authorize-access-vpc-security-group)\.
+ If you launched your cluster in the EC2\-Classic platform, follow the steps in [To Configure the Amazon Redshift Security Group](#rs-gsg-how-to-authorize-access-cluster-security-group)\.

**Note**  
You only need to configure one of these two types of security groups\. Follow the steps that correspond to the platform in which you launched your cluster\.

## To Configure the VPC Security Group \(EC2\-VPC Platform\)<a name="rs-gsg-how-to-authorize-access-vpc-security-group"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose `examplecluster` to open it, and make sure you are on the **Configuration** tab\.

1. Under **Cluster Properties**, for **VPC Security Groups**, choose your security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-vpc-security-group.png)

1. After your security group opens in the Amazon EC2 console, choose the **Inbound** tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-select.png)

1. Choose **Edit**, and enter the following, then choose **Save**: 
   + **Type**: **Custom TCP Rule**\.
   + **Protocol**: **TCP**\.
   + **Port Range**: type the same port number that you used when you launched the cluster\. The default port for Amazon Redshift is `5439`, but your port might be different\.
   + **Source**: select **Custom IP**, then type `0.0.0.0/0`\.
**Important**  
Using 0\.0\.0\.0/0 is not recommended for anything other than demonstration purposes because it allows access from any computer on the internet\. In a real environment, you would create inbound rules based on your own network settings\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-authorize.png)

## To Configure the Amazon Redshift Security Group<a name="rs-gsg-how-to-authorize-access-cluster-security-group"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose `examplecluster` to open it, and make sure you are on the **Configuration** tab\.

1. Under **Cluster Properties**, for **Cluster Security Groups**, choose **default** to open the default security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-cluster-security-group.png)

1. On the **Security Groups** tab, in the cluster security group list, choose the cluster security group whose rules you want to manage\.

1. On the **Security Group Connections** tab, choose **Add Connection Type**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/security-group-modify-10.png)

1. In the **Connection Type** box, choose **CIDR/IP**\.

    In **CIDR/IP to Authorize**, type `0.0.0.0/0` and choose **Authorize**\. 
**Important**  
Using 0\.0\.0\.0/0 is not recommended for anything other than demonstration purposes because it allows access from any computer on the Internet\. In a real environment, you would create inbound rules based on your own network settings\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/security-group-modify-20.png)