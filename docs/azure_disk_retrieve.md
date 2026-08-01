---
title: "Step 5. Specify Retrieval Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_disk_retrieve.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Retrieval Settings


[This step applies only if you have selected a restore point stored in an archive repository at the Restore Point step of the wizard]

At the Data retrieval step of the wizard, choose a retrieval mode and specify a period for which you want to keep the data available.

1. In the Retrieval Mode section, select the retrieval mode that the backup appliance will use to retrieve the archived data. For more information on data retrieval modes, see [Retrieving Data From Archive](azure_retrieving_vm_data.md).

1. In the Availability Period section, specify the number of days for which you want to keep the data available for restore operations. You can [manually extend the availability period](azure_retrieving_vm_data.md) later if required.

|  |
| --- |
| Tip |
| If you want to receive an email notification when data availability period is about to expire, select the Send notification email check box and choose when you want to be notified (that is, the number of hours remaining until data expiration). |

[![Performing Disk Restore](images/azure_restoring_disk_retrieve.webp)](images/azure_restoring_disk_retrieve.webp "Performing Disk Restore")

Page updated 2026-07-01

