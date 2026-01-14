---
title: "General Security Considerations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/general_security_considerations.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---

# General Security Considerations

In this article

General security considerations include best practices which help you to harden backup infrastructure, build a more secure environment, and mitigate risks of being compromised. Ensure that your backup infrastructure meet the common recommendations described in this section. For more information about hardening specific backup infrastructure components, see [Securing Backup Infrastructure](securing_backup_infrastructure.md).

Network

To secure the communication channel for backup traffic, consider the following recommendations:

* Create network segmentation policies to define network boundaries, control traffic between subnets and limit access to security-sensitive backup infrastructure components.
* Make sure that only ports used by backup infrastructure components are opened. For more information, see [Ports](used_ports.md).
* Use an isolated network to transport data between backup infrastructure components — backup server, backup proxies, repositories and so on.

* Disable outdated network protocols:

* SSL 2.0 and 3.0 as they have well-known security vulnerabilities and are not NIST-approved. For more information, see [NIST guidelines](https://csrc.nist.gov/publications/detail/sp/800-52/rev-2/final).

* TLS 1.0 and 1.1 if they are not needed. For more information, see [NIST guidelines](https://csrc.nist.gov/publications/detail/sp/800-52/rev-2/final).

* LLMNR and NetBIOS broadcast protocols to prevent spoofing and man-in-the-middle (MITM) attacks.

* SMB 1.0 protocol as it has a number of serious security vulnerabilities including remote code execution. For more information, see [this Microsoft article](https://techcommunity.microsoft.com/t5/storage-at-microsoft/stop-using-smb1/ba-p/425858).

User Roles and Permissions

Administrator privileges on the machine where a backup server or a backup proxy is deployed allow users to access other backup infrastructure components. If an attacker gains such permissions, they can erase most of the production data, backups, and replicas, as well as compromise other systems in your environment. To mitigate risks, use the principle of the least privilege. Provide the minimal required permissions needed for the accounts to operate correctly. For more information, see [Permissions](required_permissions.md).

If you deploy backup infrastructure components from Veeam Software Appliance or Veeam Infrastructure Appliance, set up a Security Officer account during the initial configuration. This account provides an additional security layer to protect your infrastructure against malicious system administration. For more information, see [Configure Security Officer Account](deployment_linux_iso_install_security_officer.md).

File System

Do not add paths writable by untrusted users to the PATH environment variable. This recommendation applies to Microsoft Windows-based and Linux-based backup infrastructure components as well as protected virtual and physical machines. A potential attacker may exploit this vulnerability to execute malware or access sensitive data. For more information, see [this CWE article](https://cwe.mitre.org/data/definitions/426.html).

Security Audit

Perform regular security audits to assess your backup infrastructure against security criteria and understand if it is compliant with best practices, industry standards, and federal regulations.

To reduce the risk of exploiting vulnerabilities by attackers, follow these recommendations:

* Regularly install the latest security updates and patches on the backup server and backup infrastructure components.
* Develop an update management strategy to prevent a negative impact on the production environment.

|  |
| --- |
| Tip: |
| You can subscribe to Veeam security advisories published in the [Veeam Knowledge Base](https://www.veeam.com/knowledge-base.html) to stay up to date with the latest security updates. |

Microsoft Windows Server

To secure Microsoft Windows-based components in your backup infrastructure, consider the following recommendations:

* Use operating system versions with Long Term Servicing Channel (LTSC). For these versions, Microsoft provides extended support including regular security updates. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/windows-server/get-started/extended-security-updates-overview).
* Regularly install the latest operating system and security updates for Microsoft Windows. To prevent a negative impact on the production environment, develop an update management strategy.

* Turn on Microsoft Defender Firewall with Advanced Security. Set up rules for inbound and outbound connections according to your infrastructure and Microsoft best practices. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/best-practices-configuring).

* Disable remote services if they are not needed:

* Remote Desktop Service
* Remote Registry service
* Remote PowerShell
* Windows Remote Management service

|  |
| --- |
| Note |
| Specific backup components require additional configuration described in section [Securing Backup Infrastructure](securing_backup_infrastructure.md#backup_server). |

Linux Server

To ensure that your backup server and other backup infrastructure components are compliant with DISA STIG and FIPS security standards, use the following deployment options:

* Veeam Software Appliance — To deploy a Veeam Backup & Replication server or Veeam Backup Enterprise Manager server.
* Veeam Infrastructure Appliance — To deploy Linux-based backup infrastructure components including a [hardened repository](hardened_repository.md).

These bundles include customized and preconfigured Rocky Linux distribution, as well as required Veeam components. For more information, see [Deployment Options](deployment_options.md).

To secure manually configured Linux-based backup infrastructure components, consider the following recommendations:

* Use operating system versions with long-term support (LTS). LTS versions of popular community-based and commercial Linux distributions have extended support including regular security updates.
* Regularly install the latest operating system and security updates for Linux distributions. To prevent a negative impact on the production environment, develop an update management strategy.
* For the SSH tunnel, use a strong and proven encryption algorithm with sufficient key length. For more information, see [Supported Cipher Suites and Protocols](cipher_suites_protocols.md). Make sure that private keys are kept in a highly secure place and cannot be uncovered by a third-party.
* Avoid using password authentication to connect to remote servers over SSH. Using key-based SSH authentication is generally considered more secure than using password authentication and helps avert man-in-the-middle (MITM) attacks. The private key is not passed to the server and cannot be captured even if a user connects to a fake server and accepts a bad fingerprint.

Related Topics

[Security & Compliance Analyzer](best_practices_analyzer.md)

Page updated 11/27/2025

Page content applies to build 13.0.1.1071
