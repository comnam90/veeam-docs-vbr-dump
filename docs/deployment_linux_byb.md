---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_linux_byb.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you install Veeam Software Appliance, review known issues and limitations described in [release notes](https://helpcenter.veeam.com/rn/veeam_backup_13_release_notes.html#known-issues-and-limitations). Also, consider the following:

* Veeam Software Appliance must be installed on a dedicated empty machine that meets the system requirements. For more information, see [System Requirements](system_requirements.md).
* Essentials license holders can only deploy Veeam Software Appliance on any [hypervisor supported by Veeam](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html?ver=13) and on [Veeam Ready — Appliance](https://www.veeam.com/partners/alliance-partner-technical-programs.html) certified hardware.

* Backup infrastructure components communicate over specific network ports. These ports must be open. For more information, see [Ports](used_ports.md).

* Veeam Software Appliance installation and initial configuration support only the English US keyboard layout.
* When you install Veeam Software Appliance, the Rocky Linux operating system, Veeam Backup & Replication and other Veeam Software Appliance components are installed with predefined settings, including volume partitioning and user account creation. After installation is complete, you need to proceed with the initial configuration of Veeam Software Appliance, which includes setting up host users, and configuring server time and network settings.

* You cannot add additional storage devices to a Veeam Software Appliance after it has been deployed.

* You cannot install third-party software on a Veeam Software Appliance.

* [VMware only] Veeam Software Appliance only supports the Network transport mode.
* [Microsoft Hyper-V only] Linux-based Veeam Software Appliance does not support the SCVMM High Availability feature.

* Define where the Veeam Backup & Replication server will be located. Depending on what kind of protection are you planning to use, the Veeam Backup & Replication server should be located on the source site or the Disaster Recovery site.

* When replication or CDP is used: If you plan to use replication or Continuous Data Protection (CDP), the Veeam Backup & Replication server should be deployed in the disaster recovery site. In case of source side failures, Veeam Backup & Replication will be available for failover operations. The source backup infrastructure can be managed with the same Veeam Backup & Replication server with the help of backup proxies deployed on the source site.
* When only backup features are used: If you plan to use Veeam Backup & Replication for backup jobs only, the backup server should be placed in the production site.

* Veeam Software Appliance uses DISA and FIPS-compliant Linux policies. These policies cannot be changed.
* Veeam Software Appliance is compliant with most SCAP Security Guide DISA STIG for RHEL 9 requirements except for the following ones:

* [V-258230](https://stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-02-27/finding/V-257816) — RHEL 9 must enable FIPS mode.

* [V-258241](https://www.stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-05-14/finding/V-258241) — RHEL 9 must implement a FIPS 140-3-compliant systemwide cryptographic policy.

|  |
| --- |
| Important |
| If you have infrastructure that does not support the TLS Extended Master Secret, Veeam Software Appliance will not be fully FIPS-compliant |

* [V-270180](https://stigviewer.com/stigs/red_hat_enterprise_linux_9/2024-12-04/finding/V-270180) — The RHEL 9 fapolicy module must be configured to employ a deny-all, permit-by-exception policy to allow the execution of authorized software programs.
* [V-257937](https://www.stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-05-14/finding/V-257937) — The RHEL 9 firewall must employ a deny-all, allow-by-exception policy for allowing connections to other systems.
* [V-258122](https://www.stigviewer.com/stigs/red_hat_enterprise_linux_9/2025-05-14/finding/V-258122) — RHEL 9 must enable certificate based smart card authentication.


