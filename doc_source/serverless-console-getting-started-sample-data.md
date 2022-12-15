# Step 1: Set up Amazon Redshift Serverless for the first time<a name="serverless-console-getting-started-sample-data"></a>

The first time you select the **Serverless dashboard**, you walk through the steps to set up Amazon Redshift Serverless\. Under **Get started with the serverless experience**, you can choose **Use default settings**\. Amazon Redshift Serverless then creates a default namespace and workgroup\. This configuration uses the default settings and becomes active when you associate the default workgroup to the default namespace\. In this section, you use the default settings, default workgroup, and default namespace\.

For more granular control of your setup, choose **Customize settings**\.

**To configure with default settings:**

1. Under **Configuration**, choose **Use default settings**\. Amazon Redshift Serverless creates a default namespace with a default workgroup associated to this namespace\. 

   The following settings under **Namespace** are set to default values\.
   + **Database name and password**
   + **Admin user credentials**
   + **Default IAM role**
   + **IAM roles** \- If you haven't created any IAM roles, choose **Associate IAM role** to create and associate an IAM role or roles with the namespace\. The IAM role you associate with your namespace must include a trust relationship with `redshift-serverless.amazonaws.com` and `redshift.amazonaws.com`\.

   The **Workgroup** is set to **default**\. Additionally, network settings are set to the **default VPC**, the **default** subnet, and the **default** cluster security group\.

1. Choose **Save configuration**\.

1. After setup completes, choose **Continue** to go to your **Serverless dashboard**\.

**To configure with customize settings:**

1. Under **Configuration**, choose **Customize settings**\. Configure the following settings\.
   + **Database name** – The name of the initial \(default\) database to create in the Amazon Redshift Serverless environment\. This database is owned by your account and created in the current AWS Region\. The name is `dev` and you can't change it\.
   + **Admin user credentials** – The user name and password of the administrator of the initial database\. This user has ownership permissions for the database\.
   + **Virtual private cloud \(VPC\)** – The name of the VPC where the database is created\. 
   + **VPC security groups** – These security groups define which subnets and IP ranges can be used in the VPC\. 
   + **Subnet** – The subnets in the VPC that is associated with the specified database\.
   + The AWS owned KMS key is used by default to encrypt your data\. Instead of using the AWS owned KMS key, you can **Customize encryption settings** to choose a **KMS key** you manage – The AWS KMS key is used to encrypt resources in Amazon Redshift Serverless\.
   + **Audit logging** – The audit log types you want to export\.
   + **Permissions** – The IAM role you associate with Amazon Redshift Serverless must include a trust relationship with `redshift-serverless.amazonaws.com` and `redshift.amazonaws.com`\.

   The **Workgroup** is set to **default**\. Additionally, network settings are set to the **default VPC**, the **default** subnet, and the **default** cluster security group\.

1. Choose **Save configuration**\.

1. After setup completes, choose **Continue** to go to your **Serverless dashboard**\.