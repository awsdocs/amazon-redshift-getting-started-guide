# Step 2: Query sample data in Amazon Redshift query editor v2<a name="rs-serverless-console-query-sample-data"></a>

You can manage and query data using query editor v2\. The query editor v2 is a full feature web\-based SQL client tool to connect to your Amazon Redshift Serverless data\. To get set up to use the Amazon Redshift query editor v2, including which permissions are needed, see [Configuring your AWS account](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2-getting-started.html) in the *Amazon Redshift Management Guide*\.

Look for the **Query data** button to query data in your Amazon Redshift Serverless with query editor v2\. When you invoke query editor v2 from the Amazon Redshift Serverless console, a new browser tab opens with the query editor\. The query editor v2 connects from your client machine to the Amazon Redshift Serverless environment\.

1. On the list of resources, choose the **Serverless default** workgroup\. query editor v2 automatically connects to Amazon Redshift Serverless using temporary credentials\.

1. Under the Amazon Redshift Serverless default workgroup, expand the **sample\_data\_dev** database\. There are three sample schemas corresponding to three sample data sets that you can load onto the Amazon Redshift database\.

1. In this tutorial, choose the **tickit** schema to initiate the creation of the **sample\_data\_dev** database, the **tickit** schema, and the sample tables under the **tickit** schema\. Amazon Redshift Serverless also loads the **tickit** sales data in the sample tables\.

1. You can run the sample queries against the loaded sample data\.

For information about query editor v2, see [Querying a database using the Amazon Redshift query editor v2](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2.html) in the *Amazon Redshift Management Guide*\. 