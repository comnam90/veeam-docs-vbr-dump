---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/linux_infrastructure_appliance_byb.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you install Veeam Infrastructure Appliance, consider the following:

* You can assign the following roles to a machine deployed with Veeam Infrastructure Appliance:

* [Virtualization Server and Host](setup_add_server.md)
* [Backup Proxy](proxies.md)

* [General-Purpose Backup Proxy](backup_proxy_general.md)
* [VMware Backup Proxy](backup_proxy.md)
* [CDP Proxy](cdp_proxy.md)

* [Cache Repository](cache_repo.md)
* [Backup Repository](backup_repository.md)

* [Linux Server](linux_server.md)
* [Hardened Repository](hardened_repository.md)
* [NFS Share](nfs_share.md)

* [Scale-Out Backup Repository Extent](backup_repository_sobr.md)

* [Guest Interaction Proxy](guest_interaction_proxy.md)
* [Gateway Server](gateway_server.md)
* [Mount Server](mount_server.md)
* [WAN Accelerator](wan_accelerator.md)

* The following roles cannot be assigned to a machine deployed with Veeam Infrastructure Appliance:

* [Tape Server](tape_server.md)
* [Off-Host Backup Proxy](offhost_backup_proxy.md)
* [Log Shipping Server](log_shipping_server.md)
* [NDMP Server](ndmp_servers.md)

* In addition to the standard [system requirements](system_requirements.md) for a backup infrastructure component, the machine where Veeam Infrastructure Appliance is installed must also meet the following requirements:

* [Hardened Repository only] Hardware RAID controllers must be used. Software RAID, Intel VMD VROC, and FakeRAID controllers are not supported.
* UEFI Secure Boot must be enabled.

* SSDs are strongly recommended for machines with the backup repository or hardened repository role assigned.
* Veeam Infrastructure Appliance installation and initial configuration support only the English US keyboard layout.
* When you install Veeam Infrastructure Appliance, the Rocky Linux operating system is installed with predefined settings, including volume partitioning and user account creation. After installation is complete, you need to proceed with the initial configuration of Veeam Infrastructure Appliance, which includes setting up default user accounts and basic system settings.

* You cannot install third-party software on a Veeam Infrastructure Appliance.

* VMware proxies deployed with Veeam Infrastructure Appliance support the following transport modes:

* Veeam Infrastructure Appliance  — Network, HotAdd, Direct NFS
* Veeam Infrastructure Appliance (with iSCSI and NVMe-TCP) — Network, HotAdd, Direct NFS, Backup from Storage Snapshot

* Veeam Infrastructure Appliance uses DISA and FIPS-compliant Linux policies. These policies cannot be changed.

* Veeam Infrastructure Appliance is tested against RHEL 9 DISA STIG using OpenSCAP. It is compliant with most xccdf\_org.ssgproject.content\_profile\_stig\_gui profile requirements except for the following ones:

* [V-258230](https://stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-02-27/finding/V-258230) — RHEL 9 must enable FIPS mode.
* [V-258241](https://www.stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-05-14/finding/V-258241) — RHEL 9 must implement a FIPS 140-3-compliant systemwide cryptographic policy.

|  |
| --- |
| Important |
| If you have infrastructure that does not support the TLS Extended Master Secret, Veeam Infrastructure Appliance will not be fully FIPS-compliant |

* [V-270180](https://stigviewer.com/stigs/red_hat_enterprise_linux_9/2024-12-04/finding/V-270180) — The RHEL 9 fapolicy module must be configured to employ a deny-all, permit-by-exception policy to allow the execution of authorized software programs.
* [V-257937](https://www.stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-05-14/finding/V-257937) — The RHEL 9 firewall must employ a deny-all, allow-by-exception policy for allowing connections to other systems.
* [V-258122](https://www.stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-05-14/finding/V-258122) — RHEL 9 must enable certificate based smart card authentication.


