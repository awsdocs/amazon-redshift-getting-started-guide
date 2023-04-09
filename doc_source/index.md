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
+ [Amazon Redshift Serverless](new-user-serverless.md)
+ [Querying data sources outside your Amazon Redshift database](data-querying.md)
   + [Querying your data lake](data-lake.md)
   + [Querying data on remote data sources](federated-query.md)
   + [Accessing data in other Amazon Redshift clusters](datasharing.md)
   + [Training machine learning models with Amazon Redshift data](machine-learning.md)
+ [Amazon Redshift provisioned clusters](new-user.md)
   + [Amazon Redshift provisioned clusters console](console.md)
   + [Connecting to Amazon Redshift provisioned clusters](connection.md)
   + [Amazon Redshift clusters and data loading](data-loading.md)
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
   + [Common database tasks](database-tasks.md)
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
+ [Amazon Redshift conceptual overview](getting-started.md)
+ [Additional resources](additional-resources.md)
+ [Document history](document-history.md)