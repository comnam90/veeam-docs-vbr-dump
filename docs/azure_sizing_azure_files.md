---
title: "Azure Files"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_azure_files.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Azure Files


You can adjust several configuration settings to improve the restore process by editing the configuration file /etc/veeam/azurebackup/Config.ini.

When you perform an FLR operation, Veeam Backup for Microsoft Azure processes simultaneously 25 folders and 25 files by default, regardless of the item size. To optimize the restore performance, you can edit the configuration file /etc/veeam/azurebackup/Config.ini to modify the number of items to be processed. Higher values can be especially useful when restoring files to the original location, as the speed of this restore type can far exceed the speed of restoring items to a new location.

|  |
| --- |
| [FileShareFlrOptions] DirectoryRestoreConcurrency=25 FileRestoreConcurrency=25 |

There are also other factors that may affect the restore performance:

* The amount of CPU and RAM resources consumed by Veeam Backup for Microsoft Azure.
* The size of files if they are being restored to a new location. Larger files can increase the number of requests to Azure operations as this can trigger [throttling issues](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/request-limits-and-throttling).
* The [subscription limits and quotas](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits) of Azure storage accounts.

|  |
| --- |
| Important |
| If you encounter a throttling issue, modifying the values in the configuration file will not resolve it. In this case, it is recommended that you contact [Veeam](azure_support_information.md) or Microsoft support for assistance. |

Page updated 2024-09-05

