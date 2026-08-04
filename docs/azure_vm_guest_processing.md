---
title: "Step 4. Specify Guest Processing Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_guest_processing.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify Guest Processing Settings


If you want to back up Azure VMs that are currently running, you can configure guest processing settings at the Guest Processing step of the wizard. These settings allow you to specify what actions the backup appliance will perform when communicating with the guest OSes.

Particularly, you can specify the following guest processing settings:

* [Application-aware processing](azure_application_aware_processing.md)

Application-aware processing is a Veeam technology that is based on Volume Shadow Copy Service (VSS), a Microsoft solution responsible for quiescing applications on Azure VMs and creating a consistent view of application data. For more information on VSS, see [Microsoft Docs](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc785914%28v%3Dws.10%29?redirectedfrom=MSDN).

You can enable application-aware processing for Windows-based Azure VMs running VSS-aware applications to ensure that the applications will be able to recover successfully, without data loss.

* [Guest scripting](azure_custom_script.md)

Guest scripting allows the backup appliance to run custom scripts on processed Azure VMs before and after backup operations.

For example, you can instruct the backup appliance to execute a pre-snapshot script on an Azure VM to quiesce its applications — this will allow the appliance to create a transactionally consistent snapshot while no write operations occur on the virtual disks of the VM. After the snapshot is created, a post-snapshot script can start the applications again.

Limitations and Requirements

When creating transactionally consistent backups, Veeam Backup for Microsoft Azure uses the Azure Queue Storage service to stop and start applications running on the processed Windows-based Azure VMs. To ensure proper communication of the backup appliance and the guest OSes, all Windows-based Azure VMs for which you plan to enable guest processing must have the 443 network port opened.

In case firewall rules configured for the Azure VMs do not allow outbound access using the 443 port, you must allow HTTPS traffic over 443 port for <FQDN>.blob.core.windows.net and <FQDN>.queue.core.windows.net, where <FQDN> is the name of the storage account used by the Veeam backup service.

Page updated 2026-07-01

