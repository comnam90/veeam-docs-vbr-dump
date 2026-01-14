---
title: "Step 3. Specify Object Storage Account"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/amazon_repository_account.html"
last_updated: "10/23/2024"
product_version: "13.0.1.1071"
---

# Step 3. Specify Object Storage Account

In this article

At the Account step of the wizard, specify the connection settings:

1. From the Credentials drop-down list, select user credentials to access your Amazon S3 object storage.

If you already have a credentials record that was configured in advance, select it from the drop-down list. Otherwise, click Add and provide your access and secret keys, as described in section [Access Keys for AWS Users](cloud_credentials_aws.md). You can also click the Manage cloud accounts link to add, edit or remove a credentials record.

The user account must have permissions listed in section [Permissions](required_permissions.md#rpasos).

1. From the AWS region drop-down list, select the AWS region where the Amazon S3 bucket is located.
2. Next to the Connection mode field, click Choose and specify how Veeam Backup & Replication will transfer data to the object storage repository:

* Direct — select this option if you want to instantly move data of processed VMs or file shares to object storage repositories. Before you select this option, check the following [Considerations and Limitations](object_storage_repository_cal.md#directmode).

* Through gateway server — select this option if you want Veeam Backup & Replication to use gateway servers to transfer data from processed machines or file shares to object storage repositories. From the Name list, select gateway servers that you want to use for data transfer operations.

By default, the role of a gateway server is assigned to the Veeam Backup & Replication server. You can choose any Microsoft Windows or Linux server that is added to your backup infrastructure and has internet connection. Note that you must add the server to the backup infrastructure beforehand. Before you add the server, check the following [Considerations and Limitations](object_storage_repository_cal.md). For more information on how to add a server, see [Virtualization Servers and Hosts](setup_add_server.md).

![Step 3. Specify Object Storage Account](images/s3_add_account.webp "Specify S3 Object Storage Account")

Page updated 10/23/2024

Page content applies to build 13.0.1.1071
