# Amazon Redshift concepts and data processing flow<a name="concepts-diagrams"></a>

In the following sections, you can find key concepts for Amazon Redshift and a description and diagram of the typical Amazon Redshift data processing flow:
+ [Amazon Redshift concepts](#concepts)
+ [Typical data processing flow for Amazon Redshift](#diagrams)

## Amazon Redshift concepts<a name="concepts"></a>

Following are some key Amazon Redshift concepts: 
+  **Cluster** – The core infrastructure component of an Amazon Redshift data warehouse is a cluster\.

  A *cluster* is composed of one or more compute nodes\. The *compute nodes* run the compiled code\. 

  If a cluster is provisioned with two or more compute nodes, an additional *leader node* coordinates the compute nodes\. The leader node handles external communication with applications, such as business intelligence tools and query editors\. Your client application interacts directly only with the leader node\. The compute nodes are transparent to external applications\. 
+  **Database** – A cluster contains one or more *databases*\. 

  User data is stored in one or more databases on the compute nodes\. Your SQL client communicates with the leader node, which in turn coordinates running queries with the compute nodes\. For details about compute nodes and leader nodes, see [Data warehouse system architecture](https://docs.aws.amazon.com/redshift/latest/dg/c_high_level_system_architecture.html)\. Within a database, user data is organized into one or more schemas\.

  Amazon Redshift is a relational database management system \(RDBMS\) and is compatible with other RDBMS applications\. It provides the same functionality as a typical RDBMS, including online transaction processing \(OLTP\) functions such as inserting and deleting data\. Amazon Redshift also is optimized for high\-performance batch analysis and reporting of datasets\.

Following, you can find a description of typical data processing flow in Amazon Redshift, along with descriptions of different parts of the flow\. For further information about Amazon Redshift system architecture, see [Data warehouse system architecture](https://docs.aws.amazon.com/redshift/latest/dg/c_high_level_system_architecture.html)\. 

## Typical data processing flow for Amazon Redshift<a name="diagrams"></a>

The following diagram illustrates a typical data processing flow in Amazon Redshift\.  

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/redshift/latest/gsg/images/architecture.png)

An Amazon Redshift *data warehouse* is an enterprise\-class relational database query and management system\. Amazon Redshift supports client connections with many types of applications, including business intelligence \(BI\), reporting, data, and analytics tools\. When you run analytic queries, you are retrieving, comparing, and evaluating large amounts of data in multiple\-stage operations to produce a final result\.

At the *data ingestion* layer, different types of data sources continuously upload structured, semistructured, or unstructured data to the data storage layer\. This data storage area serves as a staging area that stores data in different states of consumption readiness\. An example of storage might be an Amazon Simple Storage Service \(Amazon S3\) bucket\.  

At the optional *data processing* layer, the source data goes through preprocessing, validation, and transformation using extract, transform, load \(ETL\) or extract, load, transform \(ELT\) pipelines\. These raw datasets are then refined by using ETL operations\. An example of an ETL engine is AWS Glue\.

At the *data consumption* layer, data is loaded into your Amazon Redshift cluster, where you can run analytical workloads\. 

Data can also be consumed for analytical workloads as follows:
+ Use *datashares* to share live data across Amazon Redshift clusters for read purposes with relative security and ease\. You can share data at different levels, such as databases, schemas, tables, views \(including regular, late\-binding, and materialized views\), and SQL user\-defined functions \(UDFs\)\.

  For more information about data sharing, see [Getting started accessing data in other Amazon Redshift clusters](datasharing.md)\.
+ Use Amazon Redshift Spectrum to query data in Amazon S3 files without having to load the data into Amazon Redshift tables\. Amazon Redshift provides SQL capability designed for fast online analytical processing \(OLAP\) of very large datasets that are stored in both Amazon Redshift clusters and Amazon S3 data lakes\.

  For more information about Redshift Spectrum, see [Getting started querying your data lake](data-lake.md)\.
+ Join data from relational databases, such as Amazon Relational Database Service \(Amazon RDS\) and Amazon Aurora, or Amazon S3, with data in your Amazon Redshift database using a federated query\. You can use Amazon Redshift to query operational data directly \(without moving it\), apply transformations, and insert data into your Amazon Redshift tables\. 

  For more information about federated queries, see [Getting started querying data on remote data sources](federated-query.md)\.
+ Amazon Redshift machine learning \(ML\) creates models, using data you provided and metadata associated with data inputs\. These models capture patterns in the input data\. You can use these models to generate predictions for new input data\. Amazon Redshift works with Amazon SageMaker Autopilot to automatically get the best model and make the prediction function available in Amazon Redshift\.

  For more information about Amazon Redshift ML, see [Getting started training machine learning models with Amazon Redshift data](machine-learning.md)\.