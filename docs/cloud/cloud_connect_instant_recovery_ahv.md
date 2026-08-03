---
title: "Performing Instant Recovery of Workloads to Nutanix AHV"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_instant_recovery_ahv.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Instant Recovery of Workloads to Nutanix AHV


You can immediately restore virtual or physical machines into a Nutanix AHV cluster by running it directly from a compressed and deduplicated backup file.

|  |
| --- |
| Note |
| This section describes only basic steps that you must take to perform instant recovery to Nutanix AHV. To get a detailed description of all prerequisites and settings of the instant recovery process, see the [Performing Instant Recovery of Workloads to Nutanix AHV](https://helpcenter.veeam.com/docs/vbr/userguide/ahv_instant_recovery_ahv.html?ver=13) section in the Veeam Backup & Replication User Guide. |

To restore one or several VMs from the backup:

1. Open the Home view.
2. Select the Backups node in the inventory pane. Expand the backup job in the working area, right-click the necessary VM in the backup job and select Instant recovery.
3. At the Machines step of the wizard, select the necessary restore point in the list, click Point on the right and select the necessary restore point.
4. At the Restore Mode step of the wizard, choose whether you want to restore the selected VM to the original or to a custom location.
5. At the Cluster step of the wizard, choose the cluster to which the recovered VM will belong. In the Prism Central deployment, you can also choose whether you want the recovered VM to be assigned the same categories as the original VM.
6. At the Storage Container step of the wizard, choose the storage container where virtual disks of the recovered VM will be stored.
7. At the Name step of the wizard, you can specify a new name for the recovered VM.
8. At the Network step of the wizard, choose a network to which the recovered VM will be connected. If you do not want to connect the VM to any virtual network, select the VM and click Disconnect.
9. At the Reason step of the wizard, specify the reason for restoring the VM.
10. At the Summary step of the wizard, select the Power on target VM after restoring check box if necessary.
11. Click Finish.

After the VM has been recovered, you can choose whether you want to migrate the VM to the production environment or cancel the recovery operation. When migrating VMs, Veeam Plug-in for Nutanix AHV transfers VM disk data to the production storage that you have selected as a destination for the recovered VM.

Page updated 2026-07-29

