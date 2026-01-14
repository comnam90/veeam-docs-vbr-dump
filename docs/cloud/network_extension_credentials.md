---
title: "network_extension_credentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/network_extension_credentials.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication connects to the network extension appliance using service credentials — credentials for the root account on the Linux-based network extension appliance VM. You can use these credentials to log on to the network extension appliance VM. This may be useful if you need to configure the network extension appliance manually, for example, for troubleshooting reasons.

It is strongly recommended that you change the password for the root account before subscribing tenants to hardware plans and deploying network extension appliances. You can change the password in the service credentials record using the Credentials Manager.

|  |
| --- |
| Important |
| Do not change the password for the service credentials record after you deploy the network extension appliance. If you change the password, all network extension appliances that are already deployed on cloud hosts will become inoperative and need to be redeployed. To learn more, see [Redeploying Network Extension Appliance](redeploy_appliance.md). |

To specify a password for the root account of the network extension appliance VM:

1. From the main menu, select Credentials and Passwords > Datacenter Credentials.
2. Select the Provider-side network extension appliance credentials record and click Edit.
3. Veeam Backup & Replication will display a warning notifying that you will need to redeploy existent network extension appliances after you change the password. Click Yes to confirm your intention.
4. In the Password field, enter a password for the root account. To view the entered password, click and hold the eye icon on the right of the Password field.

The specified password will be assigned to the root account of every network extension appliance VM that will be deployed on the SP side.

1. In the Description field, if necessary, change the default description for the edited credentials record.
2. Click OK to save the specified password.

|  |
| --- |
| Note |
| It is also recommended that tenants change the password for the root account of the tenant-side network extension appliance before connecting to the SP. To learn more, see [Managing Credentials](cloud_connect_tenant_appliance_credentials.md). |

![Managing Network Extension Appliance Credentials](images/creds_network_appliance.webp)

Page updated 1/30/2024

Page content applies to build 13.0.1.1071
