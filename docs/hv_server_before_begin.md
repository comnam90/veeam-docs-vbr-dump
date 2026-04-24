---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hv_server_before_begin.html"
last_updated: "4/23/2026"
product_version: "13.0.1.2067"
---

# Before You Begin


Before you add a Microsoft Hyper-V server to the backup infrastructure, check the following prerequisites:

* Note that Linux-based Veeam Software Appliance does not support the SCVMM High Availability feature.
* Check permissions required to add the server. For more information, see [Permissions](required_permissions.md#rphost).
* Make sure that you do not add to the backup infrastructure Hyper-V hosts or clusters managed by an SCVMM server if this SCVMM server is already added to the backup infrastructure.
* Modern versions of Azure Local (formerly Azure Stack HCI) clusters have Windows Defender Application Control (WDAC) enabled and running in enforcement mode by default. You will need to deploy the latest supplemental WDAC policy on these clusters before adding them to VBR. For more details, see [this Veeam KB article](https://www.veeam.com/kb4456).

Only Hyper-V cluster or host roles are supported for Azure Local clusters or nodes in Veeam Backup & Replication. Assigning alternative roles (for example, backup repository, mount server, WAN accelerator) is not covered by the supplemental WDAC policies referenced in the KB article and is not supported.

* File and printer sharing must be enabled in network connection settings of the added Microsoft Hyper-V host. Otherwise, Veeam Backup & Replication will fail to deploy required components.
* Make sure that the NETBIOS name of the Microsoft Hyper-V Server is successfully resolved.
* The option to use Veeam Deployment Kit for certificate-based authentication is not available for Hyper-V clusters. Credential-based authentication is required for communication with the Hyper-V cluster objects. For more information, see [Using Veeam Deployment Kit](deployment_kit.md).
* [For Linux-based backup servers] Both the Hyper-V nodes and the backup server must be joined to the same Active Directory domain. If they are not joined to the same Active Directory domain, additional manual configuration of the krb5.conf file is required. For more information on the file configuration, see [this Veeam KB article](https://www.veeam.com/kb4841).
* Linux-based backup servers do not support Hyper-V workgroup clusters. This configuration is available only for Microsoft Windows-based backup servers.

* If you get the "Invalid Credentials" error when adding a Hyper-V host using a local account, see [this Veeam KB article](https://www.veeam.com/kb1914).
* Veeam Backup & Replication ignores the SCVMM maintenance mode on Hyper-V hosts and Hyper-V cluster nodes. That is, Veeam Backup & Replication continues all data protection activities and allows launching new ones.


