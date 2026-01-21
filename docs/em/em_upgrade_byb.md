---
title: "Before You Begin"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_upgrade_byb.html"
last_updated: "1/20/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before starting the upgrade procedure, read and follow the recommendations below:

* To upgrade Veeam Backup Enterprise Manager to version 13.0.1, you must be running version 12.3.1 or later. To upgrade from earlier versions, contact [Veeam Customer Support](https://www.veeam.com/support.html).
* A machine on which you plan to install Enterprise Manager must meet the system requirements. For more information, see [System Requirements](system_requirements.md).
* A user account that you plan to use for upgrade must have sufficient permissions. For more information, see [Permissions](required_permissions.md).
* Backup infrastructure components communicate with each other over specific ports. These ports must be open. For more information, see [Ports](used_ports.md).
* Check the Known Issues section of the [Veeam Backup & Replication Release Notes](https://helpcenter.veeam.com/rn/veeam_backup_13_0_1_release_notes.html).
* With Enterprise Manager and connected backup servers, begin the backup infrastructure upgrade process with Enterprise Manager. Backup servers must be upgraded after that. When you use different versions of Veeam Backup Enterprise Manager and Veeam Backup & Replication, you may not be able to leverage all features of Veeam Backup Enterprise Manager. Moreover, data collection from backup servers of earlier versions takes more time, which can be critical if many backup servers are added to Enterprise Manager.

If you have a backup server installed on the same machine, upgrade it immediately after completing upgrade of the Enterprise Manager server. Otherwise, the Configuration Database Connection Settings utility will not work properly for Veeam Backup & Replication. For more information about the utility, see [Connecting Enterprise Manager to Another Configuration Database](dbconfig_utility.md).

* In Enterprise Manager, you cannot edit jobs that are managed by backup servers with earlier versions installed until you upgrade the backup servers. Additionally, you cannot create and edit jobs of such backup servers in [Veeam Self-Service Backup Portal for Cloud Director](em_working_with_vcd_vms.md) and [vSphere Self-Service Backup Portal](em_working_with_vsphere_portal.md). For example, if you upgrade Enterprise Manager to version 13.0, you will not be able to edit jobs managed by a backup server with version 12.3 until you upgrade the backup server to version 13.0.
* Local antivirus or antimalware software can interfere with Enterprise Manager upgrade. If you receive the Failed to create website 0x80070020 message, disable your local antivirus or antimalware software and start the upgrade process again. You can re-enable your antivirus software once the upgrade completes. For more information, see [this Veeam KB article](https://www.veeam.com/kb1992).
* .NET 3.5.1 WCF HTTP Activation Windows component prevents Enterprise Manager from functioning. Make sure there is no .NET 3.5.1 WCF HTTP Activation Windows component on the Veeam Backup Enterprise Manager server prior to the installation.


