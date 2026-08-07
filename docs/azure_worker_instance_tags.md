---
title: "Adding Worker Instance Tags"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_instance_tags.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Worker Instance Tags


For all worker instances that are launched in specific Azure subscriptions for the duration of backup, restore and retention processes, you can assign custom Azure tags, which may help you differentiate worker instances that have the same or similar names:

1. Switch to the Configuration page.

1. Navigate to Workers > Tags.
2. In the Name and Value fields, specify a key and a value for a new custom Azure tag, and then click Add. Note that you cannot add more than 50 custom Azure tags.

Consider the following limitations:

* The maximum length of the tag key is 128 characters.
* The maximum length of the tag value is 256 characters.
* The following characters are not supported: < > # % + & \ ? / .

For more information on tag limitations, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources#limitations).

1. Click Save.

|  |
| --- |
| Tip |
| You can use a number of runtime variables as tag values to allow the backup appliance to automatically fill in specific information for worker instances launched during data protection operations. However, for worker instances deployed during restore operations, retention tasks and configuration checks, the values of the %policyid% and %policyName% variables will be replaced with operation names. |

[![Adding Tags to Workers](images/azure_workers_tags.webp)](images/azure_workers_tags.webp "Adding Tags to Workers")

Page updated 2026-07-01

