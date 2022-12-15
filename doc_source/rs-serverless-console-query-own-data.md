# Step 2: Query your own data in Amazon Redshift query editor v2<a name="rs-serverless-console-query-own-data"></a>

You can query data from different data sources in Amazon Redshift Serverless\. Following is a list of data sources you can query data from:
+ To query data in Amazon S3, you can load data into an existing Amazon Redshift table from Amazon S3 using query editor v2\. For more information, see [Loading data from Amazon S3](https://docs.aws.amazon.com/redshift/latest/dg/tutorial-loading-data.html) in the *Amazon Redshift Database Developer Guide*\.
+ To query data in AWS Glue catalogues that represent databases in your Amazon S3\-based data lakes, you can create an external schema to query your data lake without loading any data into Amazon Redshift Serverless\. For more information, see [Querying a data lake](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2-querying-data-lake.html) in the *Amazon Redshift Management Guide*\.
+ To query data in your data stores using federated queries, you can create an external schema from an Amazon RDS PostgresSQL or MySQL database\.

  For information on how to get started using federated queries to PostgreSQL, see [Getting started with using federated queries to PostgreSQL](https://docs.aws.amazon.com/redshift/latest/dg/getting-started-federated.html)\.

  For more information on how to get started with using federated queries to MySQL, see [Getting started with using federated queries to MySQL](https://docs.aws.amazon.com/redshift/latest/dg/getting-started-federated-mysql.html)\. 

  For information on how to create an external schema in query editor v2, see [Creating the external schema](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2-querying-data-lake.html.)\.