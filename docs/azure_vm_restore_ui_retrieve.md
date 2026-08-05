---
title: "Step 5. Specify Retrieval Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_restore_ui_retrieve.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Retrieval Settings


[This step applies only if you have selected a restore point stored in an archive repository at the Virtual Machines step of the wizard]

At the Data retrieval step of the wizard, choose a retrieval mode and specify a period for which you want to keep the data available.

1. Click the link in the Retrieval mode section.

1. In the Retrieval settings window, for each processed Azure VM, do the following:

1. Select an Azure VM and click Edit.

1. In the Edit Retrieval Mode window, select the retrieval mode that the backup appliance will use to retrieve the archived data, and click Save. For more information on data retrieval modes, see [Retrieving Data From Archive](azure_retrieving_vm_data.md).

1. To save changes made to the data retrieval settings, click Apply.

[![Restoring Azure VM](images/azure_restore_vm_retrieve.webp)](images/azure_restore_vm_retrieve.webp "Restoring Azure VM")

1. Click Edit Availability Period in the Availability period section.

1. In the Availability period window, specify the number of days for which you want to keep the data available for restore operations. You can [manually extend the availability period](azure_retrieving_vm_data.md) later if required.

|  |
| --- |
| Tip |
| If you want to receive an email notification when data availability period is about to expire, select the Send notification email check box and choose when you want to be notified (that is, the number of hours remaining until data expiration). |

1. To save changes made to the availability period settings, click Apply.

[![Restoring Azure VM](images/azure_restore_vm_availability.webp)](images/azure_restore_vm_availability.webp "Restoring Azure VM")

Page updated 2026-05-07

