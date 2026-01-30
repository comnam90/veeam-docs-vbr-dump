---
title: "Restore-VEADItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-veaditem.html"
last_updated: "9/16/2025"
product_version: "13.0.1.1071"
---

# Restore-VEADItem


Short Description

Restores backed-up Active Directory objects and containers.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore backed-up Active Directory objects.

|  |
| --- |
| Restore-VEADItem -Item <VEADItem[]> -Server <String> -Credential <PSCredential> [-UseSSL] [-RestoreChangedObjects] [-RestoreDeletedObjects] [-ChangePasswordAtLogon] [-MergeAttributes] [-NewPassword <SecureString>] [-GcServer <String>] [-TargetContainer <VEADADContainer>] [-AccountState <VEADAccountState>] [-PasswordRestoreAction <VEADPasswordRestoreAction>] [<CommonParameters>] |

* Restore a backed-up Active Directory container.

|  |
| --- |
| Restore-VEADItem -Container <VEADContainer> -Server <String> -Credential <PSCredential> [-UseSSL] [-RestoreChangedObjects] [-RestoreDeletedObjects] [-ChangePasswordAtLogon] [-MergeAttributes] [-NewPassword <SecureString>] [-GcServer <String>] [-TargetContainer <VEADADContainer>] [-AccountState <VEADAccountState>] [-PasswordRestoreAction <VEADPasswordRestoreAction>] [<CommonParameters>] |

Detailed Description

This cmdlet restores backed-up Active Directory objects and containers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | For restore of Active Directory objects.  Specifies an array of Active Directory objects. The cmdlet will restore these objects. | Accepts the [VEADItem](veaditem.md)[] object. To get this object, run the [Get-VEADItem](get-veaditem.md) cmdlet. | True | Named | True (ByValue) |
| Container | For restore of Active Directory containers.  Specifies an Active Directory container. The cmdlet will restore that container. | Accepts the [VEADContainer](veadcontainer.md) object. To get this object, run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. | True | Named | True (ByValue) |
| Server | Specifies DNS name or IP address of the target server. The cmdlet will restore Active Directory objects and containers to this server. | String | True | Named | False |
| Credential | Specifies credential records that Veeam Explorer for Microsoft Active Directory will use to connect to the LDAP server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |
| RestoreChangedObjects | Defines whether changed Active Directory objects will be restored.  If you provide this parameter, Veeam Explorer for Microsoft Active Directory will restore backed-up Active Directory objects. If the object is deleted, the cmdlet will skip this object.  Note: To run the cmdlet, you must provide either this or the RestoreDeletedObjects parameter. | SwitchParameter | False | Named | False |
| RestoreDeletedObjects | Defines whether deleted Active Directory objects will be restored.  If you provide this parameter, Veeam Explorer for Microsoft Active Directory will restore deleted Active Directory objects. If the object is not deleted, the cmdlet will skip this object.  Note: To run the cmdlet, you must provide either this or the RestoreChangedObjects parameter. | SwitchParameter | False | Named | False |
| UseSSL | Defines whether Veeam Explorer for Microsoft Active Directory will establish a secure SSL connection to the target server.  If you provide this parameter, Veeam Explorer for Microsoft Active Directory will connect over SSL to the target server. Otherwise, Veeam Explorer for Microsoft Active Directory will connect to the target server using a non-secure connection. | SwitchParameter | False | Named | False |
| GcServer | Specifies a Global Catalog server FQDN or IP address. Veeam Explorer for Microsoft Active Directory will use this server to look for the linked attributes of the objects in the AD domain tree.  If you do not provide this parameter, Veeam Explorer for Microsoft Active Directory will try to detect the Global Catalog server automatically. | String | False | Named | False |
| MergeAttributes | Defines whether multi-valued attributes of Active Directory objects will be merged.  If you provide this parameter, Veeam Explorer for Microsoft Active Directory will merge existing multi-valued attributes of Active Directory objects with multi-valued attributes from a backup file. Otherwise, the production multi-valued attributes will be replaced with multi-valued attributes from a backup file. | SwitchParameter | False | Named | False |
| PasswordRestoreAction | Specifies options for restoring user passwords. You can specify one of the following options:   * OriginalPassword - to restore Active Directory objects with original user passwords. * NoPassword - to restore Active Directory objects without restoring user passwords. * NewPassword - to restore Active Directory objects with new passwords for users.   Note: For the NewPassword option, you must specify a new password with the NewPassword parameter. | VEADPasswordRestoreAction | False | Named | False |
| ChangePasswordAtLogon | For the PasswordRestoreAction parameter.  Defines whether users must restore the password after the restore completes. If you provide this parameter, users must change the password at next logon. | SwitchParameter | False | Named | False |
| NewPassword | For the PasswordRestoreAction parameter.  Specifies new passwords for users. Veeam Explorer for Microsoft Active Directory will restore Active Directory objects with this password. | Securestring | False | Named | False |
| TargetContainer | For restore to a different container.  Specifies the target container. Veeam Explorer for Microsoft Active Directory will restore objects and containers to this container. | Accepts the [VEADADContainer](veadadcontainer.md) object. To get this object, run the [Get-VEADADContainer](get-veadadcontainer.md) cmdlet. | False | Named | False |
| AccountState | Specifies a state of an Active Directory account. You can specify one of the following states:   * SameAsInBackup - to keep an Active Directory account state the same as in a backup. * Enabled - to restore an Active Directory account with the enabled state. * Disabled - to restore an Active Directory account with the disabled state. | VEADAccountState | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

Restoring Objects

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Active Directory Object to Server

|  |  |
| --- | --- |
| This example shows how to restore an Active Directory object to the ADSrv2045 server.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  $ADitem = Get-VEADItem -Container $container[3] -LDAPQuery "(cn=SalesMailboxe8e8782f639e4a24898b93c325d8ed9d)"  $creds = Get-Credential  Restore-VEADItem -Item $ADitem -Server "ADSrv2045" -Credential $creds -RestoreChangedObjects |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable. 3. Run the [Get-VEADItem](get-veaditem.md) cmdlet. Set the $container variable as the Container parameter value and select the necessary container. Specify the LDAPQuery parameter value. Save the result to the $ADitem variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Enter credentials that will be used for authenticating to the LDAP server. Save the result to the $creds variable. 5. Run the Restore-VEADItem cmdlet. Specify the following settings:  * Set the $ADitem variable as the Item parameter value. * Specify the Server parameter value. * Set the $creds variable as the Credential parameter value. * Provide the RestoreChangedObjects parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Active Directory Object to Different Container

|  |  |
| --- | --- |
| This example shows how to restore an Active Directory object to a different container. The Active Directory object will be restored with the following options:   * User passwords will be changed with a new password. * Users must change their password at next logon. * Active Directory accounts will be enabled after restore completes.   |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  $ADitem = Get-VEADItem -Container $container[3] -Id "2687bd4b-1028-47e7-b720-6bf065179452"  $containercreds = Get-Credential  $targetcontainer = Get-VEADADContainer -Server 172.16.8.223 -Credential $containercreds  $newpassword = Read-Host -Prompt "Enter your password" -AsSecureString  Restore-VEADItem -Item $ADitem -TargetContainer $targetcontainer[2] -NewPassword $newpassword -ChangePasswordAtLogon -PasswordRestoreAction NewPassword -AccountState Enabled -RestoreDeletedObjects -Server "172.16.8.223" -Credential $containercreds -RestoreChangedObjects |  Perform the following steps:   1. Get the Active Directory object:  1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable. 3. Run the [Get-VEADItem](get-veaditem.md) cmdlet. Set the $container variable as the Container parameter value and select the necessary container. Specify the Id parameter value. Save the result to the $ADitem variable.  1. Get the target Active Directory container:  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $containercreds variable. 2. Run the [Get-VEADADContainer](get-veadadcontainer.md) cmdlet. Specify the Server parameter value. Set the $containercreds variable as the Credential parameter value. Save the result to the $targetcontainer variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet with the Prompt and AsSecureString parameters. Save the result to the $newpassword variable. 2. Run the Restore-VEADItem cmdlet. Specify the following settings:  * Set the $ADitem variable as the Item parameter value. * Set the $targetcontainer variable as the TargetContainer parameter value and select the necessary container. * Set the $newpassword variable as the NewPassword parameter value. * Provide the ChangePasswordAtLogon parameter. * Set the NewPassword property as the PasswordRestoreAction parameter value. * Set the Enabled property as the AccountState parameter value.  * Provide the RestoreDeletedObjects parameter. * Specify the Server parameter value. * Set the $containercreds variable as the Credential parameter value. * Provide the RestoreChangedObjects parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Active Directory Object with Custom Restore Options

|  |  |
| --- | --- |
| This example shows how to restore an Active Directory object with the following restore options:   * Deleted objects will be restored. * Changed objects will be restored. * Existing multi-valued attributes will be merged with multi-valued attributes from a backup file.   |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  $ADitem = Get-VEADItem -Container $container[3] -LDAPQuery "(cn=SalesMailboxe8e8782f639e4a24898b93c325d8ed9d)"  $credentials = Get-Credential  Restore-VEADItem -Item $ADitem -Server "ADSrv2045" -Credential $credentials -RestoreChangedObjects -RestoreDeletedObjects -MergeAttributes |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable. 3. Run the [Get-VEADItem](get-veaditem.md) cmdlet. Set the $container variable as the Container parameter value and select the necessary container. Specify the LDAPQuery parameter value. Save the result to the $ADitem variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $credentials variable. 5. Run the Restore-VEADItem cmdlet. Specify the following settings:  * Specify the Server parameter value.  * Set the $credentials variable as the Credential parameter value.  * Provide the RestoreChangedObjects parameter. * Provide the RestoreDeletedObjects parameter. * Provide the MergeAttributes parameter. |

Restoring containers

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Active Directory Container to Different Server

|  |  |
| --- | --- |
| This example shows how to restore an Active Directory container to a different server.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  $container = Get-VEADContainer -Container $parentcontainer[8]  $credentials = Get-Credential  Restore-VEADItem -Container $container[3] -Server "dldc.dim.local" -Credential $credentials -UseSSL -GcServer "DLCD.dim.local" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $parentcontainer variable as the Container parameter value. Specify the ordinal number of the parent container. Save the result to the $container variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $credentials variable. 5. Run the Restore-VEADItem cmdlet. Specify the following settings:  * Set the $container variable as the Container parameter value and select the necessary container.  * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. * Provide the SSL parameter. * Specify the GcServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Restoring Active Directory Container to Different Container

|  |  |
| --- | --- |
| This example shows how to restore an Active Directory container to a different container. The Active Directory container will be restored with the following options:   * User passwords will be changed with a new password. * Users must change their password at next logon. * Active Directory accounts will be enabled after restore completes.   |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  $containercreds = Get-Credential  $targetcontainer = Get-VEADADContainer -Server 172.16.8.223 -Credential $containercred  $newpassword = Read-Host -Prompt "Enter your password" -AsSecureString  Restore-VEADItem -Container $container[3] -Server "172.16.8.223" -Credential $containercreds -TargetContainer $targetcontainer[2] -NewPassword $newpassword -ChangePasswordAtLogon -PasswordRestoreAction NewPassword -RestoreDeletedObjects -AccountState Enabled |  Perform the following steps:   1. Get the Active Directory object:  1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable.  1. Get the target Active Directory container:  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $containercred variable. 2. Run the [Get-VEADADContainer](get-veadadcontainer.md) cmdlet. Specify the Server parameter value. Set the $containercred variable as the Credential parameter value. Save the result to the $targetcontainer variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet with the Prompt and AsSecureString parameters. Save the result to the $newpassword variable. 2. Run the Restore-VEADItem cmdlet. Specify the following settings:  * Set the $container variable as the Container parameter value and select the necessary container.  * Set the $targetcontainer variable as the TargetContainer parameter value and select the necessary target container. * Set the $newpassword variable as the NewPassword parameter value. * Provide the ChangePasswordAtLogon parameter. * Set the NewPassword property as the PasswordRestoreAction parameter value. * Set the Enabled property as the AccountState parameter value. * Provide the RestoreDeletedObjects parameter. * Set the $containercreds as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Restoring Active Directory Container with Custom Restore Options

|  |  |
| --- | --- |
| This example shows how to restore an Active Directory object with the following restore options:   * Deleted objects will be restored. * Changed objects will be restored. * Existing multi-valued attributes will be merged with multi-valued attributes from a backup file.   |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  $credentials = Get-Credential  Restore-VEADItem -Container $container[3] -Server "dldc.dim.local" -Credential $credentials -RestoreChangedObjects -RestoreDeletedObjects -MergeAttributes |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $credentials variable. 4. Run the Restore-VEADItem cmdlet. Specify the following settings:  * Set the $container variable as the Container parameter value and select the necessary container. * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. * Provide the RestoreChangedObjects parameter. * Provide the RestoreDeletedObjects parameter. * Provide the MergeAttributes parameter. |

Related Commands

* [Get-VEADRestoreSession](get-veadrestoresession.md)
* [Get-VEADDomain](get-veaddomain.md)
* [Get-VEADContainer](get-veadcontainer.md)


