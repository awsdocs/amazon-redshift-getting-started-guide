# Getting started querying your data lake<a name="data-lake"></a>

You can use Amazon Redshift Spectrum to query data in Amazon S3 files without having to load the data into Amazon Redshift tables\. You can query data in many formats, including Parquet, ORC, RCFile, TextFile, SequenceFile, RegexSerde, OpenCSV, and AVRO\. To define the structure of the files in Amazon S3, you create external schemas and tables\. Then, you use an external data catalog such as AWS Glue or your own Apache Hive metastore\. Changes to either type of data catalog are immediately available to any of your Amazon Redshift clusters\.

After your data is registered with an AWS Glue Data Catalog and enabled with AWS Lake Formation, you can query it by using Redshift Spectrum\. 

Redshift Spectrum resides on dedicated Amazon Redshift servers that are independent of your cluster\. Redshift Spectrum pushes many compute\-intensive tasks, such as predicate filtering and aggregation, to the Redshift Spectrum layer\. Redshift Spectrum also scales intelligently to take advantage of massively parallel processing\.

You can partition the external tables on one or more columns to optimize query performance through partition elimination\. You can query and join the external tables with Amazon Redshift tables\. You can access external tables from multiple Amazon Redshift clusters and query the Amazon S3 data from any cluster in the same AWS Region\. When you update Amazon S3 data files, the data is immediately available for queries from any of your Amazon Redshift clusters\. 

For more information about Redshift Spectrum, including how to work with Redshift Spectrum and data lakes, see [Getting started with Amazon Redshift Spectrum](https://docs.aws.amazon.com/redshift/latest/dg/c-getting-started-using-spectrum.html) in *Amazon Redshift Database Developer Guide*\.