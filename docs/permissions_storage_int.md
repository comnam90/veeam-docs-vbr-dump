---
title: "Storage System Integration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_storage_int.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Storage System Integration


NetApp Data ONTAP/Lenovo Thinksystem DM/DG Permissions

The account used to connect to NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG storage system must have permissions described in this section. The commands are provided for the console, UI names may differ.

Required permissions depend on what you add to the storage infrastructure. If you add a whole cluster, use the permissions listed for the cluster. If you add a storage virtual machine (SVM), use the permissions listed for the SVM.

Cluster (VMware Integration)

Cluster (VMware Integration)

| Command/Directory | Access/Query Level |
| DEFAULT | readonly |
| cluster | readonly |
| metrocluster | readonly |
| vserver fcp | readonly |
| volume file | readonly |
| lun igroup | all |
| vserver iscsi | all |
| network | readonly |
| system node | readonly |
| security | readonly |
| security login | readonly |
| set | readonly |
| snapmirror | all |
| system | readonly |
| version | readonly |
| volume qtree | readonly |
| lun | all |
| vserver nfs | all |
| volume snapshot | all |
| volume | all |
| vserver | all |

SVM (VMware Integration)

SVM (VMware Integration)

| Command/Directory | Access/Query Level |
| DEFAULT | none |
| lun | all |
| lun igroup | all |
| network | readonly |
| security | readonly |
| security login | readonly |
| snapmirror | all |
| system | readonly |
| version | readonly |
| volume | all |
| volume file | readonly |
| volume qtree | all |
| volume snapshot | all |
| vserver | all |
| vserver fcp | all |
| vserver iscsi | all |
| vserver nfs | all |

Cluster (NAS Backup Integration)

Cluster (NAS Backup Integration)

| Command/Directory | Access/Query Level |
| DEFAULT | readonly |
| security | readonly |
| security login | readonly |
| volume snapshot | all |
| vserver | all |
| vserver nfs | all |

SVM (NAS Backup Integration)

SVM (NAS Backup Integration)

| Command/Directory | Access/Query Level |
| DEFAULT | none |
| lun | readonly |
| network | readonly |
| security | readonly |
| security login | readonly |
| snapmirror | readonly |
| version | readonly |
| volume | readonly |
| volume snapshot | all |
| vserver | all |

Cluster (Veeam Agent Integration)

Cluster (Veeam Agent Integration)

| Command/Directory | Access/Query Level |
| cluster | readonly |
| lun | all |
| metrocluster | readonly |
| network | readonly |
| system license | readonly |
| system node | readonly |
| version | readonly |
| volume | all |
| volume snapshot | all |
| vserver | all |

SVM (Veeam Agent Integration)

SVM (Veeam Agent Integration)

| Command/Directory | Access/Query Level |
| lun | all |
| network | readonly |
| version | readonly |
| volume | all |
| volume snapshot | all |
| vserver | all |

Universal Storage API Integrated Systems Permissions

The account used to connect to a Universal Storage API integrated system must be assigned a necessary role in the storage system console and have a set of necessary permissions.

* For DataCore, the account must have the following permissions:

* General
* Port
* Host
* Virtual disk
* Snapshot
* Physical disk

* For Dell PowerMax, the account must be assigned the Storage Administrator role.

* For Dell PowerStore, the account must be assigned one of the following roles:

* Administrator
* Storage Administrator
* Storage Operator

* For Fsas ETERNUS EP300, the account must be assigned the following roles:

* Storage Administrator (View Only)
* Storage Administrator (Provisioning)
* Storage Administrator (Local Copy)

* For Fsas ETERNUS AF and DX series, the account must be assigned the Software role.

* For Hitachi VSP/VSP One Block, the account must be assigned the following roles:

* Storage Administrator (View Only)
* Storage Administrator (Provisioning)
* Storage Administrator (Local Copy)

* For HPE XP, the account must be assigned the following roles:

* Storage Administrator (View Only)
* Storage Administrator (Provisioning)
* Storage Administrator (Local Copy)

* For NEC Storage M Series, the account must be assigned the Administrator role.

* For NEC Storage V Series, the account must be assigned the following roles:

* Storage Administrator (View Only)
* Storage Administrator (Provisioning)
* Storage Administrator (Local Copy)

* For NetApp SolidFire/HCI, the account must have the following permissions:

* Volumes
* Cluster Admins

* For Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile), the account must be assigned the Veeam Admin Role.

For privileges required to integrate the unstructured data backup feature with Dell PowerScale (formerly Isilon), see [Integration with Dell PowerScale](nas_filer_nas_device.md#dell_emc_isilon) in the Unstructured Data Backup section.

For storage systems not mentioned above, the account must have Administrator role.

Page updated 2026-07-21

