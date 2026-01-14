---
title: "Kerberos Authentication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/kerberos_authentication.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Kerberos Authentication

In this article

Veeam Backup & Replication supports Kerberos authentication for all components of the backup infrastructure including Veeam Explorers, Veeam Agents, Veeam Plug-Ins, and Veeam Backup Enterprise Manager. You can build the backup infrastructure in the following environments:

* Kerberos authentication is the primary domain authentication protocol, NTLM is supported for compatibility. This configuration is used by default starting from Microsoft Windows 2000 Server.
* Kerberos is the only domain authentication protocol, NTLM is disabled (more secure).

|  |
| --- |
| Note |
| Kerberos authentication is supported only in Microsoft Active Directory-based environments. |

How Kerberos Works

Unlike NTLM, Kerberos uses Ticket Granting Tickets (TGT) issued by the Key Distribution Center (KDC). TGT files contain a session key, the key's expiration date, and a user's IP address. They are encrypted and have limited validity period (10 hours by default). This authentication mechanism protect users from man-in-the-middle (MITM) attacks.

Veeam Backup & Replication supports the standard Kerberos authentication scenario:

1. A client sends a request to the KDC, which is located on a domain controller and uses Microsoft Active Directory as the account database. The request contains user details and information about the Veeam service the client wants to access.
2. The KDC verifies the client's request and issues a TGT.
3. The client uses the TGT to send a request to the KDC Ticket Granting Service (TGS) and get a TGS ticket. The request also contains the Service Principal Name (SPN) of the service.
4. The client uses the TGS ticket to send a request to the server.
5. The server verifies the client's request and provides access to the service for a limited period specified in the Kerberos configuration.

For more information about Kerberos authentication, see [this Microsoft article](https://learn.microsoft.com/en-us/windows/win32/secauthn/basic-authentication-concepts).

Requirements and Limitations

Kerberos authentication has the following requirements and limitations:

* The client and the server must belong to the same domain, or a trust relationship must exist between domains.
* All backup infrastructure components must be added to the Veeam Backup & Replication console using FQDN.
* Veeam backup infrastructure servers must resolve FQDNs.
* FQDN must be used when connecting to the remote Veeam Backup & Replication console.
* The hostname length for all Windows-based backup infrastructure components and VM guest OSes must not exceed 15 characters.
* The maximum time difference between the client and the domain controller must be 5 minutes to protect the backup infrastructure from relay attacks.
* NFS is supported by Kerberos starting from version 4.1.
* For guest OS processing, consider the following:

+ Local accounts do not support Kerberos authentication. To authenticate with Microsoft Windows guest OS using Kerberos, specify an Active Directory account.
+ If you use networkless application-aware guest processing through VIX API/vSphere Web Services or PowerShell Direct, the guest OS must still have access to the domain controller. Otherwise, Kerberos authentication will not work.

For SPNs, consider the following aspects:

* Each Veeam service must have two SPNs registered with the Active Directory in the following formats:

+ {ServiceName}/{FQDN}, for example, VeeamBackupSvc/vbrserver01.tech.local
+ {ServiceName}/{NetBIOSName}, for example, VeeamBackupSvc/VBRSERVER01

* For the following services, SPNs are registered automatically each time they start:

+ Veeam Cloud Gateway Service (VeeamGateSvc)
+ Veeam CDP Proxy Service (VeeamCdpProxySvc)
+ Veeam Hyper-V Integration Service (VeeamHvIntegrationSvc)
+ Veeam Data Mover Service/Veeam Transport Service (VeeamTransportSvc)
+ Veeam WAN Accelerator Service (VeeamWANSvc)
+ Veeam vPower NFS Service (VeeamNFSSvc)
+ Veeam Backup VSS Integration Service (VeeamFilesysVssSvc)
+ Veeam Installer Service (VeeamDeploySvc)
+ Veeam Tape Service (VeeamTapeSvc)
+ Veeam Log Shipping Service (VeeamLogShipperSvc)
+ Veeam Guest Helper Service (VeeamGuestHelperSvc)

* If you want to register SPN manually, you can use the setspn tool. For more information about manual SPN registration, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections?view=sql-server-ver16#Manual). To disable automatic SPN registration, contact Veeam Customer Support.

Note that Veeam Platform Services (AWS, Azure, Google Cloud) and Veeam Explorer Recovery Service do not need to be registered as they do not have SPNs.

* To communicate with Hyper-V clusters, Veeam Backup & Replication uses the default SPN format for Veeam Hyper-V Integration Service: {HOST}/{FQDN} as there may be issues with registering SPN VeeamHvIntegrationSvc/{FQDN} for a cluster account.

* If you want to use another account for running a Veeam service, you must manually remove the existing SPN from the Active Directory beforehand. Otherwise, the SPN registration with the new account will fail.

|  |
| --- |
| Important |
| If you use persistent agents for guest OS processing and want to upgrade Veeam Backup & Replication to version 12, there may be issues with application-aware processing in a Kerberos-only environment. To mitigate risks, register SPNs for Guest Helper Service using the following format: {VeeamGuestHelperSvc}/{FQDN} and {VeeamGuestHelperSvc}/{NetBIOSName}. For more information, see [this Veeam KB article](https://www.veeam.com/kb4393). |

Configuring Kerberos Environments

If you use default Microsoft Windows configuration for Kerberos authentication with NTLM fallback, configure the Network security: LAN Manager Authentication Level security policy setting to send NTLMv2 responses only. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/network-security-lan-manager-authentication-level).

|  |
| --- |
| Note |
| Using NTLM increases the attack surface of your backup infrastructure. To build a more secure environment, disable NTLM and leave Kerberos the only domain authentication protocol. You can do this by enabling FIPS-compliance mode. For more information, see [FIPS Compliance](fips_compliance.md). |

To configure a Kerberos-only environment, perform the following steps:

1. Enable an NTLM audit. Start to collect and analyze NTLM audit events to determine which applications and services send NTLM requests. Reconfigure or update them to use Kerberos. If an application or service does not support Kerberos, replace it with an alternative one. For more information about auditing NTLM usage, see [this Microsoft article](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/jj865670%28v%3Dws.10%29).
2. Enable Kerberos extended logging mode. By default, Veeam Backup & Replication saves logs only for failed SPN registrations. It is recommended to collect information about all SPN registrations during initial Veeam Backup & Replication deployment and NTLM audit troubleshooting. To enable extended logging for SPNs used for Kerberos authentication between backup infrastructure components, see [this Veeam KB article](https://www.veeam.com/kb4392).
3. Restrict NTLM traffic. When all applications and services are configured to use Kerberos and there are no NTLM audit events, apply Network Security: Restrict NTLM Active Directory group policies to restrict NTLM traffic and authentication. You can also configure exclusions for specific hosts if they still require NTLM authentication to work properly. For more information about restricting NTLM usage, see [this Microsoft article](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/jj865676%28v%3Dws.10%29).

|  |
| --- |
| Note |
| To prevent Kerberos environments from Kerberoasting attacks, do the following:   * Make sure that you use strong encryption algorithms allowed for Kerberos. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/network-security-configure-encryption-types-allowed-for-kerberos). * Prevent Kerberos change password that uses RC4 secret keys. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/windows-server/security/kerberos/preventing-kerberos-change-password-that-uses-rc4-secret-keys). |

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
