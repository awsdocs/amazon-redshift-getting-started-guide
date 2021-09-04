# Task 8: Clean up your resources<a name="cm-dev-t-clean-up-resources"></a>

If you deployed a cluster to complete this exercise, when you are finished with the exercise delete the cluster\. Deleting the cluster stops it accruing charges to your AWS account\.

To delete the cluster, follow the steps in [Deleting a cluster](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-clusters-console.html#delete-cluster) in the *Amazon Redshift Cluster Management Guide*\.

If you want to keep the cluster, keep the sample data for reference\. Most of the examples in this guide use the tables that you create in this exercise\. The size of the data won't have any significant effect on your available storage\.

If you want to keep the cluster, but want to clean up the sample data, run the following command to drop the `SALESDB` database\.

```
DROP DATABASE SALESDB;
```

If you didn't create a `SALESDB` database, or if you don't want to drop the database, run the following commands to drop just the tables\.

```
DROP TABLE DEMO;
DROP TABLE users;
DROP TABLE venue;
DROP TABLE category;
DROP TABLE date;
DROP TABLE event;
DROP TABLE listing;
DROP TABLE sales;
```