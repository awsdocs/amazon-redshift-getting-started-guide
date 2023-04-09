# Connecting to Amazon Redshift provisioned clusters<a name="connection"></a>

To connect to Amazon Redshift clusters, from the **Clusters** page, expand **Connect to Amazon Redshift clusters** and do one of the following:
+ Use the query editor v2 to run queries on databases hosted by your Amazon Redshift cluster\. After creating your cluster, you can immediately run queries by using the query editor v2\.

  For more information, see [Querying a database using the Amazon Redshift query editor v2](https://docs.aws.amazon.com/redshift/latest/mgmt/query-editor-v2.html)\.
+ Connect to Amazon Redshift from your client tools using JDBC or ODBC drivers by copying the JDBC or ODBC driver URL\.

  To work with data in your cluster, you need JDBC or ODBC drivers for connectivity from your client computer or instance\. Code your applications to use JDBC or ODBC data access API operations, or use SQL client tools that support either JDBC or ODBC\.

  For more information on how to find your cluster connection string, see [Finding your cluster connection string](https://docs.aws.amazon.com/redshift/latest/mgmt/configuring-connections.html#connecting-drivers.html)\.
+ If your SQL client tool requires a driver, you can download an operating system\-specific driver to connect to Amazon Redshift from your client tools\.

  For more information on how to install the appropriate driver for your SQL client, see [Configuring a JDBC driver version 2\.0 connection](https://docs.aws.amazon.com/redshift/latest/mgmt/jdbc20-install.html)\.

  For more information on how to configure an ODBC connection, see [Configuring an ODBC connection](https://docs.aws.amazon.com/redshift/latest/mgmt/configure-odbc-connection.html)\.