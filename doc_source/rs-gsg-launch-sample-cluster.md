# Step 3: Launch a Sample Amazon Redshift Cluster<a name="rs-gsg-launch-sample-cluster"></a>

Now that you have the prerequisites completed, you can launch your Amazon Redshift cluster\.

**Important**  
 **The cluster that you are about to launch will be live \(and not running in a sandbox\)\. You will incur the standard Amazon Redshift usage fees for the cluster until you delete it\.** If you complete the tutorial described here in one sitting and delete the cluster when you are finished, the total charges will be minimal\. 

## To Launch an Amazon Redshift Cluster<a name="rs-gsg-how-to-launch-sample-cluster"></a>

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.
**Important**  
If you use IAM user credentials, ensure that the user has the necessary permissions to perform the cluster operations\. For more information, go to [Controlling Access to IAM Users](http://docs.aws.amazon.com/redshift/latest/mgmt/iam-redshift-user-mgmt.html) in the *Amazon Redshift Cluster Management Guide*\.

1. In the main menu, select the region in which you want to create the cluster\. For the purposes of this tutorial, select **US West \(Oregon\)**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-aws-region-selector.png)

1. On the Amazon Redshift Dashboard, choose **Launch Cluster**\.

   The Amazon Redshift Dashboard looks similar to the following:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-10.png)

1. On the Cluster Details page, enter the following values and then choose **Continue**:

   + **Cluster Identifier**: type `examplecluster`\.

   + **Database Name**: leave this box blank\. Amazon Redshift will create a default database named `dev`\.

   + **Database Port**: type the port number on which the database will accept connections\. You should have determined the port number in the prerequisite step of this tutorial\. You cannot change the port after launching the cluster, so make sure that you have an open port number in your firewall so that you can connect from SQL client tools to the database in the cluster\.

   + **Master User Name**: type `masteruser`\. You will use this username and password to connect to your database after the cluster is available\.

   + **Master User Password** and **Confirm Password**: type a password for the master user account\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-10.png)

1. On the Node Configuration page, select the following values and then choose **Continue**:

   + **Node Type**: **dc2\.large**

   + **Cluster Type**: **Single Node**  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-20.png)

1. On the Additional Configuration page, you will see different options depending on your AWS account, which determines the type of platform the cluster uses\. To keep things simple for this tutorial, you do not need to understand the distinction between these platforms, EC2\-Classic and EC2\-VPC\. You can use the information in [Additional Resources](rs-gsg-clean-up-tasks.md#rs-gsg-additional-resources) to locate the *Amazon Redshift Cluster Management Guide* and learn more after the tutorial\.

   **EC2\-VPC**

   If you have a default VPC in the region you’ve selected, you will use the EC2\-VPC platform to launch your cluster\. You screen will look similar to the following:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-30-defaultvpc.png)

   Use the following values if you are launching your cluster in the EC2\-VPC platform:

   + **Cluster Parameter Group**: select the default parameter group\.

   + **Encrypt Database**: **None**\.

   + **Choose a VPC**: **Default VPC \(vpc\-xxxxxxxx\)**

   + **Cluster Subnet Group**: **default**

   + **Publicly Accessible**: **Yes**

   + **Choose a Public IP Address**: **No**

   + **Enhanced VPC Routing**: **No**

   + **Availability Zone**: **No Preference**

   + **VPC Security Groups**: **default \(sg\-xxxxxxxx\)**

   + **Create CloudWatch Alarm**: **No**

   **EC2\-Classic**

   If you do not have a VPC, you will use the EC2\-Classic platform to launch your cluster\. Your screen will look similar to the following:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-30-classic.png)

   Use the following values if you are launching your cluster in the EC2\-Classic platform: 

   + **Cluster Parameter Group**: select the default parameter group\.

   + **Encrypt Database**: **None**\.

   + **Choose a VPC**: **Not in VPC**

   + **Availability Zone**: **No Preference**

   + **Cluster Security Groups**: **default**

   + **Create CloudWatch Alarm**: **No** 

1.  Associate an IAM role with the cluster\. 

   For **AvailableRoles**, choose **myRedshiftRole** and then choose **Continue**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-45.png)

1. On the Review page, review the selections that you’ve made and then choose **Launch Cluster**\.

   Your screen will look similar to the following:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-40.png)

1. A confirmation page appears and the cluster will take a few minutes to finish\. Choose **Close** to return to the list of clusters\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-wizard-50.png)

1. On the Clusters page, choose the cluster that you just launched and review the **Cluster Status** information\. Make sure that the **Cluster Status** is **available** and the **Database Health** is **healthy** before you try to connect to the database later in this tutorial\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-cluster-status.png)