---
title: "Using Veeam Deployment Kit"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_kit.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Using Veeam Deployment Kit


The Veeam Deployment Kit is a package that enables certificate-based authentication for the backup infrastructure configuration. When the Deployment Kit is installed on a target server, Veeam Backup & Replication can authenticate using certificates instead of traditional user name and password credentials. The Deployment Kit can be used to connect to remote [Microsoft Windows servers](windows_server_credentials.md) and to [Veeam Agent computers](agents_deploy_deployer.md) that you plan to add to a protection group.

The Deployment Kit installation is a prerequisite to use persistent agent components on protected Microsoft Windows VMs. For more information, see [Persistent Agent Components](persistent_agent_components.md).

Deployment Kit Usage Scenarios

Use the Deployment Kit in the following scenarios:

* Kerberos is disabled or unavailable

Use the Deployment Kit if your environment does not support NTLM or Kerberos authentication.

* Enhanced security

Certificate-based authentication offers a more secure alternative to user name and password authentication.

* Passwordless authentication

When the Deployment Kit is installed and configured on the target server, Veeam Backup & Replication connects using certificates. No user name or password are required for authentication.

Deployment Kit Availability

* Pre-installed by default:

The Deployment Kit is pre-installed with all JeOS (Just enough Operating System) infrastructure components. If you deploy a JeOS-based Veeam component, you only need to pair it with Veeam Backup & Replication. No additional installation is required.

* Manual installation required:

For the following components, you can manually install the Deployment Kit:

* Microsoft Windows managed servers
* Hyper-V hosts
* Microsoft Windows-based and Linux-based Veeam Agent computers
* Guest Interaction proxies
* Protected Microsoft Windows VMs (for persistent guest agent installation)

|  |
| --- |
| Note |
| The Deployment Kit cannot be used to connect to remote Linux servers that are not deployed from the Veeam JeOS ISO file. When adding such servers to the backup infrastructure, you must use the SSH credentials option at the [Access](linux_server_ssh.md) step of the New Linux Server wizard. |

How to Use the Veeam Deployment Kit

1. Create the Veeam Deployment Kit:

1. Open the Backup Infrastructure view.
2. In the [inventory pane](vbr_ui.md), right-click the Managed Servers node and select Create Veeam deployment kit. Alternatively, you can click Create Veeam Deployment Kit on the ribbon.
3. Specify the path where you can export the Veeam Deployment Kit and click OK.

1. Prepare for installation:

The Deployment Kit typically includes:

* Necessary binaries and supporting files
* Authentication certificates
* A sample service configuration script (InstallDeploymentKit.BAT) for automated installation

1. [For Microsoft Windows managed servers and protected Microsoft Windows VMs] Install the Deployment Kit on the target remote host:

* Automated installation (recommended):

1. Copy the entire Deployment Kit folder to the target remote host.
2. Run the provided InstallDeploymentKit.BAT script to automatically install the kit and configure all required components.

* Manual installation:

1. Obtain the Deployment Kit files from the Windows subfolder on your Veeam Backup & Replication console and copy them to the target remote host.
2. Install the OpenSSL package and the Veeam Installer service package on the target server.
3. Copy the certificates from the Deployment Kit folder to the remote host.
4. Install the certificates by running:

|  |
| --- |
| C:\Windows\Veeam\Backup\VeeamDeploymentSvc.exe --install-server-certificate /path/to/server-cert.pem --key /path/to/server-key.pem  C:\Windows\Veeam\Backup\VeeamDeploymentSvc.exe --install-certificate /path/to/client-cert.pem |

1. Restart the Veeam Installer service (VeeamDeploySvc) to apply the changes.

1. [For Veeam Agent computers] Follow the instructions provided in [Deploying Veeam Agent Using Veeam Deployment Kit](agents_deploy_deployer.md).

Usage Notes

When the Deployment Kit is installed and certificates are configured, select Connect using certificate-based authentication when adding the server to your backup infrastructure.

No user name or password are required; authentication is handled automatically using the installed certificates.

Related Topics

* [Adding Microsoft Hyper-V Servers](add_hyperv_server.md)
* [Adding Microsoft Windows Servers](add_windows_server.md)
* [Guest Interaction Proxies](guest_interaction_proxy.md)


