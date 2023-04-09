# Accessing data in other Amazon Redshift clusters<a name="datasharing"></a>

Using Amazon Redshift data sharing, you can share live data with high security and greater ease across Amazon Redshift clusters or AWS accounts for read purposes\. You can have instant, granular, and high\-performance access to data across Amazon Redshift clusters without manually copying or moving it\. Your users can see the most up\-to\-date and consistent information as it's updated in Amazon Redshift clusters\. You can share data at different levels, such as databases, schemas, tables, views \(including regular, late\-binding, and materialized views\), and SQL user\-defined functions \(UDFs\)\. 

Amazon Redshift data sharing is especially useful for these use cases:
+ Centralizing business\-critical workloads – Use a central extract, transform, and load \(ETL\) cluster that shares data with multiple business intelligence \(BI\) or analytic clusters\. This approach provides read workload isolation and chargeback for individual workloads\.
+ Sharing data between environments – Share data among development, test, and production environments\. You can improve team agility by sharing data at different levels of granularity\.

For more information about data sharing, see [Getting started data sharing](https://docs.aws.amazon.com/redshift/latest/dg/getting-started-datashare.html) in the *Amazon Redshift Database Developer Guide*\.