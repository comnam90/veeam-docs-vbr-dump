---
title: "Granting Permissions to Users"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/granting_permissions_mssql.html"
last_updated: "12/3/2024"
product_version: "13.0.1.1071"
---

# Granting Permissions to Users

In this article

When you install Veeam Plug-In for Microsoft SQL Server, full access rights to the plug-in configuration file are automatically granted to all users. To protect sensitive information that is stored in the configuration file from unwanted access, we recommend limiting access to the configuration file to a dedicated group of users.

By default, theVeeam Plug-In configuration file (veeam\_config.xml) is located in the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL folder on the machine where Veeam Plug-In is installed.

Before You Begin

Before you create a user group that will have access to the plug-in configuration file, consider the following:

* To perform this procedure, the OS user account must have local administrator privileges.
* Add only trusted users to the group.
* After a user is added to the group, they must log out, then log in to the system again to activate the group permissions.

Granting Permissions to the Plug-In Configuration File

1. Create a new user group by running the following command:

|  |
| --- |
| net localgroup "<groupName>" /comment:"<description>" /add |

where:

* <groupName> — the name of the created group.
* <description> — the description of the group.

1. Add a user to the group with the following command:

|  |
| --- |
| net localgroup "<groupName>" "<userName>" /add |

where:

* <groupName> — the name of the created group.

* <userName> — the name of the account that will be granted access to the configuration file.

1. Create a new access control list (ACL) with Read and Write permissions using this set of commands:

|  |
| --- |
| $newACL = New-Object System.Security.AccessControl.FileSecurity #creates a dedicated ACL  $newACL.SetAccessRuleProtection($true,$false) #disables inheritance and deletes all inherited permissions  $newACL.AddAccessRule( (New-Object System.Security.AccessControl.FileSystemAccessRule("groupName","Read","Allow"))) # allows read  $newACL.AddAccessRule( (New-Object System.Security.AccessControl.FileSystemAccessRule("groupName","Write","Allow")))# allows write |

where:

* newACL — the name of the new access control list. You can give any name to this temporary variable.
* <groupName> — the name of the created group.

1. Assign ownership of the new ACL to the previously created user group by running the following command:

|  |
| --- |
| $newACL.SetOwner([System.Security.Principal.NTAccount]"groupName") #sets owner for the ACL |

where:

* newACL — the name of the new access control list.
* <groupName> — the name of the created group.

1. Apply the ACL to the plug-in configuration file using this command:

|  |
| --- |
| set-acl -Path:<configFilePath> -AclObject:$newACL #apply ACL to the plug-in configuration file |

where:

* <configFilePAth> — the path to the plug-in configuration file. The default path is %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\veeam\_config.xml.

* newACL — the name of the new access control list.

Page updated 12/3/2024

Page content applies to build 13.0.1.1071
