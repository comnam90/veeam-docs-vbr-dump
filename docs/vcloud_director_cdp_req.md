---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_cdp_req.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Consider the following for CDP for VMware Cloud Director:

* As CDP for VMware Cloud Director is based on the CDP mechanism for VMware vSphere VMs, requirements and limitations are also actual. For more information, see [Requirements and Limitations for CDP](cdp_requirements.md).
* Check the supported Cloud Director versions in [Supported Platforms, Applications and Workloads](platform_support.md#cloud_dir).
* The version of target hosts must be 7.0 or later. Target hosts of version 6.5 and 6.7 are not supported.
* The Any storage policy is not supported.
* Most configurations require that you disable the VM discovery option in VMware Cloud Director global settings. For more information on where you can change the option, see [VMware Docs](https://docs.vmware.com/en/VMware-Cloud-Director/10.3/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-068B8D3E-11B4-4B67-A653-B374AFD98303.html#activating-vm-discovery-0).
* Fast provisioned VMs cannot be protected with CDP.
* The maximum number of VMs in a vApp that can be protected with CDP is 128.
* If you add a new organization VDC to the Cloud Director server after the I/O filter is installed on the existing VDCs, you need to install the I/O filter manually on the newly added VDC. To do that, open the [I/O Filter Management](vcd_cdp_io_filter_launch.md) wizard, make sure that check boxes are selected near the organization VDCs where the I/O filter must be present and finish the wizard.


