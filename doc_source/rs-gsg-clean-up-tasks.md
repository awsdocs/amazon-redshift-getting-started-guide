# Step 7: Find Additional Resources and Reset Your Environment<a name="rs-gsg-clean-up-tasks"></a>

When you have completed this tutorial, you can go to other Amazon Redshift resources to learn more about the concepts introduced in this guide or you can reset your environment to the previous state\. You might want to keep the sample cluster running if you intend to try tasks in other Amazon Redshift guides\. However, remember that **you will continue to be charged for your cluster as long as it is running**\. You should revoke access to the cluster and delete it when you no longer need it so that you stop incurring charges\.

## Where Do I Go From Here?<a name="rs-gsg-where-do-i-go"></a>

### Additional Resources<a name="rs-gsg-additional-resources"></a>

We recommend that you continue to learn more about the concepts introduced in this guide with the following resources: 

+ [Amazon Redshift Management Overview](http://docs.aws.amazon.com/redshift/latest/mgmt/overview.html): This topic provides an overview of Amazon Redshift\.

+ [Amazon Redshift Cluster Management Guide](http://docs.aws.amazon.com/redshift/latest/mgmt/): This guide builds upon this *Amazon Redshift Getting Started* and provides in\-depth information about the concepts and tasks for creating, managing, and monitoring clusters\.

+ [Amazon Redshift Database Developer Guide](http://docs.aws.amazon.com/redshift/latest/dg/): This guide builds upon this *Amazon Redshift Getting Started* by providing in\-depth information for database developers about designing, building, querying, and maintaining the databases that make up your data warehouse\.

### Resetting Your Environment<a name="rs-gsg-reset-environment"></a>

When you have completed this tutorial, you should reset your environment to the previous state by doing the following: 

+ Revoke access to the port and CIDR/IP address for which you authorized access:

  If you used the EC2\-VPC platform to launch your cluster, perform the steps in [To Revoke Access from the VPC Security Group](#rs-gsg-how-to-revoke-access-vpc-security-group)\.

  If you used the EC2\-Classic platform to launch your cluster, perform the steps in [To Revoke Access from the Cluster Security Group](#rs-gsg-how-to-revoke-access-cluster-security-group)\.

+ Delete your sample cluster\. **You will continue to incur charges for the Amazon Redshift service until you delete the cluster**\. Perform the steps in [To Delete the Sample Cluster](#rs-gsg-how-to-delete-sample-cluster)\.

#### To Revoke Access from the VPC Security Group<a name="rs-gsg-how-to-revoke-access-vpc-security-group"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose **examplecluster** to open it, and make sure you are on the **Configuration** tab\.

1. Under **Cluster Properties**, choose the vpc security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-vpc-security-group.png)

1. With the default security group selected, choose the **Inbound** tab and then choose **Edit**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-edit.png)

1. Delete the custom TCP/IP ingress rule that you created for your port and CIDR/IP address 0\.0\.0\.0/0\. Do not remove any other rules, such as the **All traffic** rule that was created for the security group by default\. Choose **Save**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-security-vpc-security-group-revoke.png)

#### To Revoke Access from the Cluster Security Group<a name="rs-gsg-how-to-revoke-access-cluster-security-group"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose examplecluster to open it, and make sure you are on the **Configuration** tab\.

1. Under **Cluster Properties**, for **Cluster Security Groups**, choose **default** to open the default security group\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-cluster-security-group.png)

1. On the **Security Groups** tab, in the cluster security group list, choose the default cluster security group \.

1. On the **Security Group Connections** tab, select the custom CIDR/IP ingress rule that you created for CIDR/IP address 0\.0\.0\.0/0 and choose **Revoke**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/security-group-rule-revoke.png)

#### To Delete the Sample Cluster<a name="rs-gsg-how-to-delete-sample-cluster"></a>

1. In the Amazon Redshift console, in the navigation pane, choose **Clusters**\.

1. Choose examplecluster to open it, and make sure you are on the **Configuration** tab\.

1. In the **Cluster** menu, choose **Delete**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-cluster-menu.png)

1. In the **Delete Cluster** window, for **Create snapshot**, choose **No** and then choose **Delete**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-cluster-delete-final-snapshot.png)

1. On the cluster details window, the **Cluster Status** will display that the cluster being deleted\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/rs-gsg-clusters-config-delete-status.png)