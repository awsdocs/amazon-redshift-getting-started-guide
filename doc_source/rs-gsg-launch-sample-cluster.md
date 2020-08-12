# Step 3: Create a sample Amazon Redshift cluster<a name="rs-gsg-launch-sample-cluster"></a>

Now that you have the prerequisites completed, you can launch your Amazon Redshift cluster\.

**Important**  
*The cluster that you are about to create is live \(and not running in a sandbox\)\. You incur the standard Amazon Redshift usage fees for the cluster until you delete it\.* If you complete the tutorial described here in one sitting and delete the cluster when you are finished, the total charges are minimal\. 

**Note**  
A new console is available for Amazon Redshift\. Choose either the **New console** or the **Original console** instructions based on the console that you are using\. The **New console** instructions are open by default\.

## New console<a name="create-cluster-sample"></a>

**To create an Amazon Redshift cluster**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.
**Important**  
If you use IAM user credentials, ensure that you have the necessary permissions to perform the cluster operations\. For more information, see [Controlling access to IAM users](https://docs.aws.amazon.com/redshift/latest/mgmt/iam-redshift-user-mgmt.html) in the *Amazon Redshift Cluster Management Guide*\.

1. At top right, choose the AWS Region in which you want to create the cluster\. 

1. On the navigation menu, choose **CLUSTERS**, then choose **Create cluster**\. The **Create cluster** page appears\.

1. In the **Cluster configuration** section, specify values for **Cluster identifier**, **Node type**, and **Nodes**\. 
   + **Cluster identifier**: Enter **examplecluster** for this tutorial\. This identifier must be unique\. The identifier must be from 1–63 characters using valid characters as a \- z \(lowercase only\) and \- \(hyphen\)\. 
   + Choose one of the following methods to size your cluster:
**Note**  
The following step describes an Amazon Redshift console that is running in an AWS Region that supports RA3 node types\. For a list of AWS Regions that support RA3 node types, see [Overview of RA3 node types](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html#rs-ra3-node-types) in the *Amazon Redshift Cluster Management Guide*\. 
     + If your AWS Region supports RA3 node types, choose either **Production** or **Free trial** to answer the question **What are you planning to use this cluster for?** 

       If your organization is eligible, you might be able to create a cluster under the Amazon Redshift free trial program\. To do this, choose **Free trial** to create a configuration with the dc2\.large node type\. For more information about choosing a free trial, see [Amazon Redshift free trial](http://aws.amazon.com/redshift/free-trial/)\. 
     + If you don't know how large to size your cluster, choose **Help me choose**\. Doing this starts a sizing calculator that asks you questions about the size and query characteristics of the data that you plan to store in your data warehouse\. 

       If you know the required size of your cluster \(that is, the node type and number of nodes\), choose **I'll choose**\. Then choose the **Node type** and number of **Nodes** to size your cluster for the proof of concept\.

     Choose **Node type**: **dc2\.large** with **Nodes**: **2** for this tutorial\.

1. In the **Database configurations** section, specify values for **Database name \(optional\)**, **Database port \(optional\)**, **Master user name**, and **Master user password**\. This tutorial uses these values: 
   + **Database name \(optional\)**: Enter **dev**\.
   + **Database port \(optional\)**: Enter **5439**\.
   + **Master user name**: Enter **awsuser**\.
   + **Master user password**: Enter a value for the password\.

1. Optionally, in the **Cluster permissions** section, for **Available IAM roles** choose the IAM role that you previously created, **myRedshiftRole**\. Then choose **Add IAM role**\. 

1. Optionally, in the **Additional configurations** section, turn off **Use defaults** to modify **Network and security**, **Database configurations**, **Maintenance**, **Monitoring**, and **Backup** settings\.

1. Choose **Create cluster**\. 

## Original console<a name="rs-gsg-how-to-launch-sample-cluster"></a>

**To launch an Amazon Redshift cluster**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.
**Important**  
If you use IAM user credentials, ensure that the user has the necessary permissions to perform the cluster operations\. For more information, see [Controlling access to IAM users](https://docs.aws.amazon.com/redshift/latest/mgmt/iam-redshift-user-mgmt.html) in the *Amazon Redshift Cluster Management Guide*\.

1. In the main menu, select the AWS Region in which you want to create the cluster\. For the purposes of this tutorial, select **US West \(Oregon\)**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-aws-region-selector.png)

1. On the Amazon Redshift Dashboard, choose **Quick launch cluster**\.

   The Amazon Redshift Dashboard looks similar to the following\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-launch-cluster-10.png)

1. On the **Cluster specifications** page, enter the following values and then choose **Launch cluster**:
   + **Node type**: Choose **dc2\.large**\.
   + **Number of compute nodes**: Keep the default value of **2**\.
   + **Cluster identifier**: Enter the value **examplecluster**\.
   + **Master user name**: Keep the default value of **awsuser**\.
   + **Master user password** and **Confirm password**: Enter a password for the master user account\.
   + **Database port**: Accept the default value of **5439**\.
   + **Available IAM roles**: Choose **myRedshiftRole**\. 

   Quick launch automatically creates a default database named **dev**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/gsg-launch-parameters.png)
**Note**  
Quick launch uses the default virtual private cloud \(VPC\) for your AWS Region\. If a default VPC doesn't exist, Quick launch returns an error\. If you don't have a default VPC, you can use the standard Launch Cluster wizard to use a different VPC\. For more information, see [Creating a cluster by using launch cluster](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-clusters-console.html#create-cluster)\.

1. A confirmation page appears and the cluster takes a few minutes to finish\. Choose **Close** to return to the list of clusters\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/gsg-cluster-launching.png)

1. On the **Clusters** page, choose the cluster that you just launched and review the **Cluster Status** information\. Make sure that the **Cluster Status** is **available** and the **Database Health** is **healthy** before you try to connect to the database later in this tutorial\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/gsg-cluster-list.png)

1. On the **Clusters** page, choose the cluster that you just launched, choose the **Cluster** button, then **Modify cluster**\. Choose the **VPC security groups** to associate with this cluster, then choose **Modify** to make the association\. Make sure that the **Cluster Properties** displays the **VPC security groups** you chose before continuing to the next step\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/gsg-modify-cluster.png)