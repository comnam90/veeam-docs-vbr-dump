---
title: "Step 3. Specify Object Storage Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/amazon_se_repository_account.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Step 3. Specify Object Storage Account


At the Account step of the wizard, specify the connection settings:

1. In the Service point field, specify a service point address of your AWS Snowball Edge device and define a port.

To get information on the IP address that must be used as a service point, see the [AWS Snowball Edge Developer Guide](https://docs.aws.amazon.com/snowball/latest/developer-guide/unlockdevice.html).

To get information on the port you must specify, see the [AWS Snowball Edge Developer Guide](https://docs.aws.amazon.com/snowball/latest/developer-guide/port-requirements.html). By default, the 8443 port is used.

1. In the Region field, type "snow".

1. From the Credentials drop-down list, select user credentials to access your AWS Snowball Edge storage.

If you already have a credentials record that was configured in advance, select it from the drop-down list. Otherwise, click Add and provide your access and secret keys, as described in section [Access Keys for AWS Users](cloud_credentials_aws.md). You can also click the Manage cloud accounts link to add, edit or remove a credentials record.

1. Next to the Connection mode field, click Choose and specify how Veeam Backup & Replication will transfer data to the object storage repository:

* Direct — select this option if you want to instantly move data of processed VMs or file shares to object storage repositories. Before you select this option, check the following [Considerations and Limitations](object_storage_repository_cal.md#directmode).

* Through gateway server — select this option if you want Veeam Backup & Replication to use gateway servers to transfer data from processed machines or file shares to object storage repositories. From the Name list, select gateway servers that you want to use for data transfer operations.

|  |
| --- |
| Note |
| The gateway server should have direct connection to AWS service endpoints. HTTP(S) proxy servers are not supported. For more information, see [Ports](used_ports.md#archive_tier). |

By default, the role of a gateway server is assigned to the Veeam Backup & Replication server. You can choose any Microsoft Windows or Linux server that is added to your backup infrastructure and has internet connection. Note that you must add the server to the backup infrastructure beforehand. Before you add the server, check the following [Considerations and Limitations](object_storage_repository_cal.md). For more information on how to add a server, see [Virtualization Servers and Hosts](setup_add_server.md).

![Step 3. Specify Object Storage Account](images/amazon_se_servicepoint.webp)


