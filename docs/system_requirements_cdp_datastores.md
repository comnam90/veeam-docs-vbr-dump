---
title: "Veeam CDP Source and Target Datastores"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_cdp_datastores.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Veeam CDP Source and Target Datastores


The following source and target datastores are supported for Veeam CDP:

* NFS on file storage
* VMFS on block storage
* VMFS on internal ESXi storage
* VSAN

VSAN is supported for all hyper-converged infrastructure (HCI) appliances.

* vVol

vVol is supported for the following vendors: NetApp, HPE Nimble, Pure Storage and HPE 3PAR. For the list of tested vendor product lines, see [this Veeam KB article](https://www.veeam.com/kb4225).

Support for HCI appliances is pending validation by Veeam. The documentation will be updated based on the testing results. For the updates, see [CDP Requirements and Limitations](cdp_requirements.md).

|  |
| --- |
| Note |
| Consider the following:   * Cisco HyperFlex 4.5 (2a) and later can be used as a source or target only with VMware vSphere 7.0 U2 and later. With the previous versions of VMware vSphere, Cisco HyperFlex is not supported. * vVol and VSAN of each vendor have limits for the number of storage objects. Once the limit is reached, CDP starts to fail because creation of new objects cannot be completed. To restore the CDP process, remove some objects from VSAN/vVol. * CDP performance depends on your datastore characteristics. For better performance, check that your target datastore is able to process the I/O workload produced on the source datastore. |


