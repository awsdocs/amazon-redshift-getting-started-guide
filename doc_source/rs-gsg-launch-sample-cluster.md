# Step 3: Launch a Sample Amazon Redshift Cluster<a name="rs-gsg-launch-sample-cluster"></a>

Now that you have the prerequisites completed, you can launch your Amazon Redshift cluster\.

**Important**  
*The cluster that you are about to launch is live \(and not running in a sandbox\)\. You incur the standard Amazon Redshift usage fees for the cluster until you delete it\.* If you complete the tutorial described here in one sitting and delete the cluster when you are finished, the total charges are minimal\. 

## To Launch an Amazon Redshift Cluster<a name="rs-gsg-how-to-launch-sample-cluster"></a>

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.
**Important**  
If you use IAM user credentials, ensure that the user has the necessary permissions to perform the cluster operations\. For more information, go to [Controlling Access to IAM Users](https://docs.aws.amazon.com/redshift/latest/mgmt/iam-redshift-user-mgmt.html) in the *Amazon Redshift Cluster Management Guide*\.

1. In the main menu, select the region in which you want to create the cluster\. For the purposes of this tutorial, select **US West \(Oregon\)**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-aws-region-selector.png)

1. On the Amazon Redshift Dashboard, choose **Quick launch cluster**\.

   The Amazon Redshift Dashboard looks similar to the following\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-10.png)

1. On the Cluster specifications page, enter the following values and then choose **Launch cluster**:
   + **Node type**: Choose **dc2\.large**\.
   + **Number of compute nodes**: Keep the default value of **2**\.
   + **Cluster identifier**: Accept the default value of **redshift\-cluster\-1**\.
   + **Master user name**: Keep the default value of **awsuser**\.
   + **Master user password** and **Confirm password**: Enter a password for the master user account\.
   + **Database port**: Accept the default value of **5439**\.
   + **Available IAM roles**: Choose **myRedshiftRole**\. 

   Quick Launch automatically creates a default database named **dev**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-10.png)
**Note**  
Quick Launch uses the default virtual private cloud \(VPC\) for your region\. If a default VPC doesn't exist, Quick Launch returns an error\. If you don't have a default VPC, you can use the standard Launch Cluster wizard to use a different VPC or use EC2 Classic without a VPC\. For more information, see [Creating a Cluster by Using Launch Cluster](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-clusters-console.html#create-cluster)\.

1. A confirmation page appears and the cluster takes a few minutes to finish\. Choose **Close** to return to the list of clusters\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-50.png)

1. On the Clusters page, choose the cluster that you just launched and review the **Cluster Status** information\. Make sure that the **Cluster Status** is **available** and the **Database Health** is **healthy** before you try to connect to the database later in this tutorial\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-cluster-status.png)