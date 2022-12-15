# Amazon Redshift Getting Started Guide

-----
*****Copyright &copy; Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in
connection with any product or service that is not Amazon's,
in any manner that is likely to cause confusion among customers,
or in any manner that disparages or discredits Amazon. All other
trademarks not owned by Amazon are the property of their respective
owners, who may or may not be affiliated with, connected to, or
sponsored by Amazon.

-----
## Contents
+ [Getting started with Amazon Redshift](getting-started.md)
   + [Prerequisites](prerequisites.md)
   + [Amazon Redshift concepts and data processing flow](concepts-diagrams.md)
+ [Getting started with Amazon Redshift basics](new-user.md)
   + [Getting started with the Amazon Redshift console](console.md)
   + [Connecting to Amazon Redshift](connection.md)
   + [Getting started with Amazon Redshift clusters and data loading](data-loading.md)
      + [Using a sample dataset](sample-data-load.md)
         + [Step 1: Create a sample Amazon Redshift cluster](rs-gsg-sample-data-load-create-cluster.md)
         + [Step 2: Try example queries using the query editors](rs-gsg-sample-data-load-query.md)
      + [Bringing your own data to Amazon Redshift](bring-own-data.md)
         + [Step 1: Create a sample Amazon Redshift cluster](rs-gsg-launch-sample-cluster.md)
         + [Step 2: Configure inbound rules for SQL clients](rs-gsg-authorize-cluster-access.md)
         + [Step 3: Grant access to one of the query editors and run queries](rs-gsg-connect-to-cluster.md)
         + [Step 4: Load data from Amazon S3 to Amazon Redshift](rs-gsg-create-sample-db.md)
         + [Step 5: Try example queries using the query editor](rs-gsg-try-query.md)
         + [Step 6: Reset your environment](rs-gsg-clean-up-tasks.md)
   + [Getting started with common database tasks](database-tasks.md)
      + [Task 1: Create a database](t_creating_database.md)
      + [Task 2: Create a user](t_adding_redshift_user_cmd.md)
      + [Task 3: Create a schema](t_creating_schema.md)
      + [Task 4: Create a table](t_creating_table.md)
         + [Insert data rows into a table](t_inserting_data_into_table.md)
         + [Select data from a table](t_selecting_data.md)
      + [Task 5: Load sample data](cm-dev-t-load-sample-data.md)
      + [Task 6: Query the system tables](t_querying_redshift_system_tables.md)
         + [Determine the process ID of a running query](determine_pid.md)
      + [Task 7: Cancel a query](cancel_query.md)
      + [Task 8: Clean up your resources](cm-dev-t-clean-up-resources.md)
+ [Getting started with Amazon Redshift Serverless basics](new-user-serverless.md)
   + [Getting started with the Amazon Redshift Serverless console](serverless-console.md)
   + [Connecting to Amazon Redshift Serverless](connecting-to-serverless.md)
   + [Getting started with Amazon Redshift Serverless and data loading](serverless-first-time-setup.md)
      + [Using a sample dataset](serverless-sample-data-load.md)
         + [Step 1: Set up Amazon Redshift Serverless for the first time](serverless-console-getting-started-sample-data.md)
         + [Step 2: Query sample data in Amazon Redshift query editor v2](rs-serverless-console-query-sample-data.md)
      + [Bringing your own data to Amazon Redshift Serverless](serverless-bring-own-data.md)
         + [Step 1: Set up Amazon Redshift Serverless for the first time](serverless-console-getting-started-own-data.md)
         + [Step 2: Query your own data in Amazon Redshift query editor v2](rs-serverless-console-query-own-data.md)
+ [Getting started with querying data sources outside your Amazon Redshift database](data-querying.md)
   + [Getting started querying your data lake](data-lake.md)
   + [Getting started querying data on remote data sources](federated-query.md)
   + [Getting started accessing data in other Amazon Redshift clusters](datasharing.md)
   + [Getting started training machine learning models with Amazon Redshift data](machine-learning.md)
+ [Additional resources](additional-resources.md)
+ [Document history](document-history.md)