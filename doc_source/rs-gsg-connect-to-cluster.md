# Step 3: Grant access to one of the query editors and run queries<a name="rs-gsg-connect-to-cluster"></a>

 To query databases hosted by your Amazon Redshift cluster, you have two options:

1. Connect to your cluster and run queries on the AWS Management Console with one of the query editors\. 

   If you use one of the query editors, you don't have to download and set up an SQL client application\. 

1. Connect to your cluster through an SQL client tool, such as SQL Workbench/J\. For more information about using SQL Workbench/J, see [Connect to your cluster by using SQL Workbench/J](https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html) in the *Amazon Redshift Management Guide\.* 

Using one of the Amazon Redshift query editors is the easiest way to run queries on databases hosted by your Amazon Redshift cluster\. After creating your cluster, you can immediately run queries using the Amazon Redshift console\. For details about considerations when using the Amazon Redshift query editor, see [Querying a database using the query editor](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor.html) in the *Amazon Redshift Management Guide\.*

## Granting access to the query editor v2<a name="gsg-query-cluster-configure-v2"></a>

The first time an administrator configures query editor v2 for your AWS account, they choose the AWS KMS key that is used to encrypt query editor v2 resources\. By default, an AWS owned key is used to encrypt resources\. Or an administrator can use a customer managed key by choosing the Amazon Resource Name \(ARN\) for the key in the configuration page\. After you configure an account, AWS KMS encryption settings can't be changed\. For more information, see [Configuring your AWS account](https://docs.aws.amazon.com/redshift/latest/mgmt/copy-parameters-credentials.html)\.

To access the query editor v2, you need permission\. An administrator can attach one of the following AWS\-managed policies to the IAM role or user to grant permissions\. These AWS\-managed policies are written with different options that control how tagging resources allows sharing of queries\. You can use the IAM console \([https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\) to attach IAM policies\. 

You can also create your own policy based on the permissions allowed and denied in the provided managed policies\. If you use the IAM console policy editor to create your own policy, choose **SQL Workbench** as the service for which you create the policy in the visual editor\. The query editor v2 uses the service name AWS SQL Workbench in the visual editor and IAM Policy Simulator\.  

For more information, see [Accessing the query editor v2](query-editor-v2-configure.html)\.

## Using the query editor v2<a name="gsg-using-query-editor-v2"></a>

To use the query editor v2 to query a database, see [Working with query editor v2](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2-using.html)\.

## Granting access to the query editor<a name="gsg-query-cluster-configure"></a>

To use the Amazon Redshift query editor, you need permission\. To set access, attach the `AmazonRedshiftQueryEditor` and `AmazonRedshiftReadOnlyAccess` IAM policies to an IAM role, then assign that role to the user that you use to access your cluster\.

**To attach the required IAM policies for the query editor**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Roles**\.

1. Choose the user that needs access to the query editor\.

1. Choose **Add permissions**\.

1. Choose **Attach existing policies directly**\.

1. For **Policy names**, \.

1. Choose **Next: Review**\.

1. Choose **Add permissions**\.

To create an IAM role to permit your Amazon Redshift cluster to communicate with other AWS services on your behalf, take the following steps\. The values used in this section are examples, you can choose values based on your needs\.<a name="create-iam-role-for-aws-services"></a>

**To create an IAM role to allow Amazon Redshift to access AWS services**

1. Open the [IAM console](https://console.aws.amazon.com/iam/home?#home)\.

1. In the navigation pane, choose **Roles**\.

1. Choose **Create role**\.

1. Choose **AWS service**, and then choose **Redshift**\.

1. Under **Select your use case**, choose **Redshift \- Customizable** and then choose **Next: Permissions**\. The **Attach permissions policy** page appears\.

1.  Add the **AmazonRedshiftQueryEditor** and **AmazonRedshiftReadOnlyAccess** permissions\.

   Choose **Next: Tags**\.

1. The **Add tags** page appears\. You can optionally add tags\. Choose **Next: Review**\.

1. For **Role name**, type a name for your role, for example **RedshiftQueryEditorAccess**\. Choose ****Create role****\.

1. The new role is available to all users on clusters that use the role\. To restrict access to only specific users on specific clusters, or to clusters in specific regions, edit the trust relationship for the role\. For more information, see [ Restricting access to IAM roles](https://docs.aws.amazon.com/redshift/latest/mgmt/authorizing-redshift-service.html#authorizing-redshift-service-database-users) in the *Amazon Redshift Management Guide*\. 

1. Associate the role with your cluster\. You can associate an IAM role with a cluster when you create the cluster, or you add the role to an existing cluster\. For more information, see [ Associating IAM roles with clusters](https://docs.aws.amazon.com/redshift/latest/mgmt/copy-unload-iam-role.html#copy-unload-iam-role-associating-with-clusters) in the *Amazon Redshift Management Guide*\. 
**Note**  
To restrict access to specific data, use an IAM role that grants the least privileges required\.

## Using the query editor<a name="gsg-using-query-editor"></a>

To use the query editor to query a database, see [Querying a database using the query editor](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor.html)\.