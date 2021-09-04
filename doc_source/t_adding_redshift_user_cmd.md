# Task 2: Create a user<a name="t_adding_redshift_user_cmd"></a>

By default, only the admin user that you created when you launched the cluster has access to the initial database in the cluster\. To grant other users access, create one or more accounts\. Database user accounts are global across all the databases in a cluster, and not per individual databases\.

Use the CREATE USER command to create a new user\. When you create a new user, you specify the name of the new user and a password\. We recommend that you specify a password for the user\. It must have 8–64 characters, and it must include at least one uppercase letter, one lowercase letter, and one numeral\.

For example, to create a user named **GUEST** with password **ABCd4321**, run the following command\.

```
CREATE USER GUEST PASSWORD 'ABCd4321';
```

To connect to the `SALESDB` database as the `GUEST` user, use the same password when you created the user, such as `ABCd4321`\.

For information about other command options, see [CREATE USER](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_USER.html) in the *Amazon Redshift Database Developer Guide*\.