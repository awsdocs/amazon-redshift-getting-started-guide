# Step 2: Create an IAM Role<a name="rs-gsg-create-an-iam-role"></a>

For any operation that accesses data on another AWS resource, your cluster needs permission to access the resource and the data on the resource on your behalf\. An example is using a COPY command to load data from Amazon S3\. You provide those permissions by using AWS Identity and Access Management \(IAM\)\. You do so either through an IAM role that is attached to your cluster or by providing the AWS access key for an IAM user that has the necessary permissions\. 

To best protect your sensitive data and safeguard your AWS access credentials, we recommend creating an IAM role and attaching it to your cluster\. For more information about providing access permissions, see [Permissions to Access Other AWS Resources](https://docs.aws.amazon.com/redshift/latest/dg/copy-usage_notes-access-permissions.html)\.

In this step, you create a new IAM role that enables Amazon Redshift to load data from Amazon S3 buckets\. In the next step, you attach the role to your cluster\.

## **To Create an IAM Role for ** Amazon Redshift<a name="rs-gsg-how-to-create-an-iam-role"></a>

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\.

1. Choose **Create role**\.

1. In the **AWS Service** group, choose **Redshift\.** 

1. Under **Select your use case**, choose **Redshift \- Customizable** then choose **Next: Permissions**\.

1. On the **Attach permissions policies** page, choose **AmazonS3ReadOnlyAccess**, and then choose **Next: Tags**\.

1. Tags are optional, we will be skipping this. Choose **Next: Review**\.

1. For **Role name**, type a name for your role\. For this tutorial, type `myRedshiftRole`\. 

1. Review the information, and then choose **Create Role**\.

1. Choose the role name of the role you just created\.

1. Copy the **Role ARN** to your clipboard—this value is the Amazon Resource Name \(ARN\) for the role that you just created\. You use that value when you use the COPY command to load data in [Step 6: Load Sample Data from Amazon S3](rs-gsg-create-sample-db.md)\.

Now that you have created the new role, your next step is to attach it to your cluster\. You can attach the role when you launch a new cluster or you can attach it to an existing cluster\. In the next step, you'll attach the role to a new cluster\.
