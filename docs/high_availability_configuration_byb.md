---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_configuration_byb.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


To assemble an HA cluster, you must install Veeam Software Appliance on the Linux-based servers that you plan to use as HA nodes, configure your HA network environment, and enable the High Availability option for both Linux-based servers using [Veeam Host Management Web UI](hmc_access.md). If you use Kerberos authentication, you must create a .keytab file and import it to the primary node using the Veeam Host Management Web UI.

Configuring HA Nodes and HA Network Environment

To configure Linux-based servers that you plan to use as HA nodes and the HA network environment, do the following:

1. [Optional] [Deploy a Veeam Software Appliance](deployment_options.md) on a Linux-based server that you plan to use as a primary node of your HA cluster.
2. Deploy a Veeam Software Appliance on a Linux-based machine that you plan to use as a secondary node of your HA cluster.

|  |
| --- |
| Important |
| The machine you plan to use as a secondary node must have a fresh Veeam Software Appliance deployment with no existing backup data. If any backup data is present, it will be permanently deleted once you assemble the HA cluster. |

1. Assign static IP addresses to both Linux-based servers on your DNS server.
2. Reserve a static IP address for an HA cluster on your DNS server. This IP address will be used to connect to the HA cluster.

|  |
| --- |
| Important |
| If you use Kerberos authentication, you must reserve for the cluster a static IP address that can contact the Kerberos Key Distribution Center (KDC). |

1. Configure the HA cluster DNS name to resolve to the HA cluster IP address.
2. [For Kerberos authentication] Join both Linux-based servers to a domain where Kerberos authentication is configured. For more information, see [Managing Domain Settings](hmc_configure_domain.md).

Enabling High Availability

After you configure the HA nodes, submit a request to enable the High Availability option for both Linux-based servers. Note that if you have disassembled the HA cluster, you will need to resubmit the request.

To submit the request, do the following:

1. Log in to the [Veeam Host Management web UI](hmc_access.md).
2. In the management pane, click Backup Infrastructure.
3. In the High Availability section, click Submit Request.

+ If you did not configure the [Security Officer](deployment_linux_iso_install_security_officer.md) account during the Veeam Software Appliance installation, the request is approved automatically.
+ If you configured the Security Officer account, you must wait until the security officer approves your request. This approval expires in 8 hours; ensure that you assemble the cluster within this period.

1. [For Kerberos authentication] If you use the Kerberos environment, you must create a .keytab file and import it to the primary node using the [Veeam Host Management Web UI](hmc_access.md).

|  |
| --- |
| Important |
| Consider the following:   * If you do not upload the .keytab file, you will not be able to authenticate using the Kerberos protocol against your HA cluster. * You can connect to the primary node using Kerberos authentication only until the custom .keytab file is uploaded to the Veeam Host Manager console. After you upload the .keytab file, you will not be able to connect to the cluster nodes using Kerberos authentication until you assemble a cluster and connect to the cluster endpoint. The custom .keytab file generated as described in this guide contains Service Principal Names (SPNs) only for the cluster endpoint, not for individual cluster nodes. * When you [join Linux-based servers to a domain](hmc_configure_domain.md) where Kerberos authentication is configured, a default .keytab file is automatically generated. This file allows you to use Kerberos authentication, for example, when connecting to the backup server using the console. |

[![Before You Begin](images/hmc_web_high_availability.webp)](images/hmc_web_high_availability.webp)

Creating Keytab File

To create the .keytab file, do the following:

1. Create a computer account in your Active Directory in one of the following ways:

* Specifying the password in the interactive password prompt.

|  |
| --- |
| New-ADComputer -Name <computer account name> -AccountPassword (Read-Host "Enter your password" -AsSecureString) -KerberosEncryptionType AES256 -PasswordNeverExpires $true -ServicePrincipalNames HOST/<DNS cluster hostname>,HOST/<DNS cluster hostname>.<domain name> -Path "OU=<organizational unit name>,DC=<first label of the domain name>,DC=<second label of the domain name>" |

* Specifying the password directly in the script.

|  |
| --- |
| New-ADComputer -Name <computer account name> -AccountPassword (ConvertTo-SecureString "<computer account password>" -AsPlainText -Force) -KerberosEncryptionType AES256 -PasswordNeverExpires $true -ServicePrincipalNames HOST/<DNS cluster hostname>,HOST/<DNS cluster hostname>.<domain name> -Path "OU=<organizational unit name>,DC=<first label of the domain name>,DC=<second label of the domain name>" |

|  |
| --- |
| Note |
| Consider the following:   * The computer account name should be different from the name of the HA cluster. * Do not associate SPNs from multiple servers (such as the individual cluster nodes) with the computer account you want to create. * You may optionally assign the computer account to an organizational unit using the Path parameter. |

1. On your Windows Domain Controller (DC), generate the .keytab file using the ktpass utility. For more information on the parameters, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ktpass#parameters).

|  |
| --- |
| ktpass -princ <computer account name>$@DOMAIN.LOCAL -mapuser DOMAIN\<computer account name>$ -crypto AES256-SHA1 -ptype KRB5\_NT\_PRINCIPAL -pass <computer account password> -setPass -setUpn -out custom.keytab |

|  |
| --- |
| Important |
| We recommend that you specify the following values for these parameters:   * For the /crypto parameter — specify the AES256-SHA1 value to use the AES256-CTS-HMAC-SHA1-96 encryption type. * For the /ptype parameter — specify the KRB5\_NT\_PRINCIPAL value to use the general principal type. |

1. [Optional] Check the computer account details and its SPNs.

|  |
| --- |
| Get-ADComputer <computer account name>$ -Properties msDS-SupportedEncryptionTypes,passwordNeverExpires setspn -L <computer account name> |

1. Verify the .keytab file before uploading it to the Veeam Host Management console.

1. Verify the contents of the .keytab file on the Windows DC using the ktpass utility. The file should contain the correct SPNs.

|  |
| --- |
| ktpass /in custom.keytab |

1. Verify that the .keytab file can be used to get a Kerberos ticket-granting ticket (TGT) for the specified SPNs.

|  |
| --- |
| kinit.exe -k -t krb.keytab {cluster SPN} |

1. Upload the keytab using the Veeam Host Management console. After that you can verify it with the following commands.

1. Verify the contents of the .keytab file.

|  |
| --- |
| klist –k /etc/veeam/auth/krb.keytab |

1. Check if the .keytab file can be used to get a Kerberos TGT for the specified SPNs.

|  |
| --- |
| kinit -k -t /etc/veeam/auth/krb.keytab {cluster SPN} |

Creating Keytab File Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 1. Creating Computer Account Using Interactive Prompt

|  |  |
| --- | --- |
| This example shows how to create a computer account using interactive prompt.  |  | | --- | | $password = Read-Host "Enter a Password" -AsSecureString  New-ADComputer -Name "my-ha-cluster-acc" -AccountPassword $password -KerberosEncryptionType AES256 -PasswordNeverExpires $true -ServicePrincipalNames tech.local |  Specify the following:   1. Run the [Read-Host](https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Save the result to the $password variable. 2. Run the [New-ADComputer](https://learn.microsoft.com/en-us/powershell/module/activedirectory/new-adcomputer?view=windowsserver2025-ps) cmdlet. Specify the necessary parameters. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 2. Generating Keytab File

|  |  |
| --- | --- |
| This command generates the .keytab file.  |  | | --- | | ktpass -princ my-ha-cluster-acc$@DOMAIN.LOCAL -mapuser DOMAIN\my-ha-cluster-acc$ -crypto AES256-SHA1 -ptype KRB5\_NT\_PRINCIPAL -pass $password -setPass -setUpn -out custom.keytab |  Specify the following parameters:   * Specify the Kerberos principal name for which the .keytab file is generated. Provide the princ parameter value in the my-ha-cluster-acc$@DOMAIN.LOCAL format. Note: This parameter is case-sensitive. * Specify the Kerberos principal to associate with a user or computer account. Provide the mapuser parameter value in the DOMAIN\my-ha-cluster-acc$ format. * Specify the encryption type key that is generated in the .keytab file. Set the AES256-SHA1 value for the crypto parameter. * Specify the principal type. Set the KRB5\_NT\_PRINCIPAL value for the ptype parameter. * Specify the computer account password that you have created at Step 1. Note: Use the asterisk sign (\*) to prompt for a password. * Set the ktpass command to use the password specified in the pass on the user account in Active Directory. Provide the setPass parameter.  * Set the UPN on the account to match the SPN. Provide the setUpn parameter.  * Specify the name of the .keytab file that you want to generate. Set the custom .keytab value for the out parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 3. Verifying Computer Account Information

|  |  |
| --- | --- |
| This command verifies computer account information.  |  | | --- | | Get-ADComputer my-ha-cluster-acc$ -Properties msDS-SupportedEncryptionTypes,passwordNeverExpires | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 4. Verifying Keytab File Before Uploading it to Veeam Host Management Console

|  |  |  |
| --- | --- | --- |
| 1. This command verifies the contents of the .keytab file on the Windows DC using the ktpass utility. The file should contain the correct SPNs.   |  | | --- | | ktpass /in custom.keytab |   1. This command verifies that the .keytab file can be used to get a Kerberos ticket-granting ticket (TGT) for the specified SPNs.   |  | | --- | | kinit.exe -k -t krb.keytab {cluster SPN} | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 5. Verifying Keytab File after Uploading it to Veeam Host Management Console

|  |  |  |
| --- | --- | --- |
| 1. This command verifies the contents of the .keytab file.   |  | | --- | | klist –k /etc/veeam/auth/krb.keytab |   1. This command verifies if the .keytab file can be used to get a Kerberos TGT for the specified SPNs.   |  | | --- | | kinit -k -t /etc/veeam/auth/krb.keytab {cluster SPN} | |


