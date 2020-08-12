# Step 7: Find additional resources and reset your environment<a name="rs-gsg-clean-up-tasks"></a>

When you have completed this tutorial, you can go to other Amazon Redshift resources to learn more about the concepts introduced in this guide\. You can also reset your environment to the previous state\. You might want to keep the sample cluster running if you intend to try tasks in other Amazon Redshift guides\. However, remember that *you continue to be charged for your cluster as long as it is running*\. To stop incurring charges, revoke access to the cluster and delete it when you no longer need it\.

## Where do I go from here?<a name="rs-gsg-where-do-i-go"></a>

### Additional resources<a name="rs-gsg-additional-resources"></a>

We recommend that you continue to learn more about the concepts introduced in this guide with the following resources: 
+ [Amazon Redshift management overview](https://docs.aws.amazon.com/redshift/latest/mgmt/overview.html): This topic provides an overview of Amazon Redshift\.
+ [Amazon Redshift Cluster Management Guide](https://docs.aws.amazon.com/redshift/latest/mgmt/): This guide builds upon this *Amazon Redshift Getting Started* and provides in\-depth information about the concepts and tasks for creating, managing, and monitoring clusters\.
+ [Amazon Redshift Database Developer Guide](https://docs.aws.amazon.com/redshift/latest/dg/): This guide builds upon this *Amazon Redshift Getting Started* by providing in\-depth information for database developers about designing, building, querying, and maintaining the databases that make up your data warehouse\.

### Resetting your environment<a name="rs-gsg-reset-environment"></a>

**Note**  
A new console is available for Amazon Redshift\. Choose either the **New console** or the **Original console** instructions based on the console that you are using\. The **New console** instructions are open by default\.

#### New console<a name="delete-cluster-sample"></a>

When you have completed this tutorial, reset your environment to the previous state by deleting your sample cluster\. *You continue to incur charges for the Amazon Redshift service until you delete the cluster*\.

**To delete a cluster**

1. Sign in to the AWS Management Console and open the Amazon Redshift console at [https://console\.aws\.amazon\.com/redshift/](https://console.aws.amazon.com/redshift/)\.

1. On the navigation menu, choose **CLUSTERS** to display your list of clusters\. 

1. Choose the **examplecluster** cluster\. For **Actions**, choose **Delete**\. The **Delete cluster** page appears\. 

1. Confirm the cluster to be deleted, then choose **Delete cluster**\. 

On the cluster list page, the cluster status is updated as the cluster is deleted\. 

#### Original console<a name="delete-cluster-sample-originalconsole"></a>

When you have completed this tutorial, you should reset your environment to the previous state by doing the following: 
+ Revoke access to the port and CIDR/IP address for which you authorized access:

  If you used the EC2\-VPC platform to launch your cluster, perform the steps in [To revoke access from the VPC security group](#rs-gsg-how-to-revoke-access-vpc-security-group)\.
+ Delete your sample cluster\. *You continue to incur charges for the Amazon Redshift service until you delete the cluster*\. Perform the steps in [To delete the sample cluster](#rs-gsg-how-to-delete-sample-cluster)\.

##### To revoke access from the VPC security group<a name="rs-gsg-how-to-revoke-access-vpc-security-group"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose **examplecluster** to open it, and make sure that you are on the **Configuration** tab\.

1. Under **Cluster Properties**, choose the VPC security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-vpc-security-group.png)

1. With the default security group selected, choose the **Inbound** tab and then choose **Edit**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-edit.png)

1. Delete the custom TCP/IP ingress rule that you created for your port and CIDR/IP address 0\.0\.0\.0/0\. Do not remove any other rules, such as the **All traffic** rule that was created for the security group by default\. Choose **Save**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-revoke.png)

##### To delete the sample cluster<a name="rs-gsg-how-to-delete-sample-cluster"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose **examplecluster** to open it, and make sure that you are on the **Configuration** tab\.

1. In the **Cluster** menu, choose **Delete**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-cluster-menu.png)

1. In the **Delete Cluster** window, for **Create snapshot**, choose **No** and then choose **Delete**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-cluster-delete-final-snapshot.png)

1. On the cluster details window, the **Cluster Status** displays that the cluster is being deleted\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-delete-status.png)