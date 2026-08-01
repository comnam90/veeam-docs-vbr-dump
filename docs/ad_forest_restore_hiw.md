---
title: "How Active Directory Forest Restore Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ad_forest_restore_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Active Directory Forest Restore Works


Microsoft Active Directory forest restore relies on forest metadata that the guest agent collects during backup.

The collected metadata describes the forest and includes the following information:

* The forest topology: all domains, their parent-child relationships, and the forest root.
* The domain controllers in each domain.
* The FSMO role holders, both forest-wide (Schema Master and Domain Naming Master) and domain-wide (RID Master, PDC Emulator and Infrastructure Master).
* The domain controller capabilities: global catalog, DNS role and read-only (RODC) status.
* The Active Directory schema version.
* Network interface settings.

Veeam Backup & Replication stores this metadata in the backup metadata file and in the configuration database, and uses it to plan and orchestrate the recovery.

How Domain Controllers are Restored

Veeam Backup & Replication restores the domain controller of the root domain first and then the domain controllers of the child domains. A child domain is restored only after its parent domain. In this version, Veeam Backup & Replication restores one domain controller per domain, and this domain controller receives all FSMO roles.

To restore each domain controller, Veeam Backup & Replication performs the following steps:

1. Restores the entire domain controller VM to the target platform and applies the network and re-IP settings. At this stage, the VM is not powered on.
2. Deploys the Veeam Active Directory Forest Recovery Agent into the restored VM while its disks are mounted offline on the default Windows mount server.
3. Powers on the domain controller. The domain controller starts in Directory Services Restore Mode (DSRM), performs a non-authoritative Active Directory Domain Services restore and reboots into normal mode.
4. Performs an authoritative SYSVOL restore.
5. Transfers the FSMO roles to the restored domain controller. For the forest root domain controller, it transfers both the forest-wide and the domain-wide roles; for each child domain controller, it transfers the domain-wide roles.
6. Installs the DNS Server role and configures DNS.
7. Removes the metadata of the domain controllers that are not restored from the directory.
8. Raises and invalidates the RID pool to prevent duplicate security identifiers (SIDs).
9. Resets the domain controller machine account password.
10. Removes the global catalog from the domain controller.
11. Configures the Windows Time service on the domain controller.

After all domain controllers are restored, Veeam Backup & Replication verifies forest replication health and re-enables the global catalog on the restored domain controllers.

You may also need to complete additional actions manually. For more information, see [Post-Restore Actions](restore_ad_forest_post_restore.md).

Communication with Domain Controllers

Veeam Backup & Replication communicates with each domain controller through a guest helper, so forest recovery does not require network access to your production environment.

* For domain controllers that run as VMware vSphere VMs, the guest helper connects through VMware guest interaction and web services.
* For domain controllers that run as Microsoft Hyper-V VMs, the guest helper connects through PowerShell Direct.

The Veeam Active Directory Forest Recovery Agent that Veeam Backup & Replication deploys on each restored domain controller carries out all Active Directory operations. The guest helper proxies every command sent from the backup server to the agent.

Page updated 2026-07-28

