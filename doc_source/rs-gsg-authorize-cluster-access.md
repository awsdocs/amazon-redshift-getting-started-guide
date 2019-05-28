# Step 4: Authorize Access to the Cluster<a name="rs-gsg-authorize-cluster-access"></a>

In the previous step, you launched your Amazon Redshift cluster\. Before you can connect to the cluster, you need to configure a security group to authorize access\. If you launched your cluster in the EC2\-VPC platform, follow the steps in [To Configure the VPC Security Group \(EC2\-VPC Platform\)](#rs-gsg-how-to-authorize-access-vpc-security-group)\.

## To Configure the VPC Security Group \(EC2\-VPC Platform\)<a name="rs-gsg-how-to-authorize-access-vpc-security-group"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose `examplecluster` to open it, and make sure that you are on the **Configuration** tab\.

1. Under **Cluster Properties**, for **VPC Security Groups**, choose your security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-vpc-security-group.png)

1. After your security group opens in the Amazon EC2 console, choose the **Inbound** tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-select.png)

1. Choose **Edit**, **Add Rule**, and enter the following, then choose **Save**: 
   + **Type**: **Custom TCP Rule**\.
   + **Protocol**: **TCP**\.
   + **Port Range**: type the same port number that you used when you launched the cluster\. The default port for Amazon Redshift is `5439`, but your port might be different\.
   + **Source**: select **Custom**, then type `0.0.0.0/0`\.
**Important**  
Using 0\.0\.0\.0/0 is not recommended for anything other than demonstration purposes because it allows access from any computer on the internet\. In a real environment, you would create inbound rules based on your own network settings\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-authorize.png)