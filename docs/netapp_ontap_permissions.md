---
title: "NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/netapp_ontap_permissions.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG Permissions


The account used to connect to NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG storage system must have permissions described in this section. The commands are provided for the console, UI names may differ.

CDOT (VMware Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
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

Only as SVM (VMware Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
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

CDOT (NAS Backup Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| DEFAULT | readonly |
| security | readonly |
| security login | readonly |
| volume snapshot | all |
| vserver | all |
| vserver nfs | all |

Only as SVM (NAS Backup Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
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

CDOT (Veeam Agent Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
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

Only as SVM (Veeam Agent Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| lun | all |
| network | readonly |
| version | readonly |
| volume | all |
| volume snapshot | all |
| vserver | all |


