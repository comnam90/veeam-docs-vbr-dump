---
title: "Granting User Permissions on Microsoft Windows Machines"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_permissions_to_users_win.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Granting User Permissions on Microsoft Windows Machines


By default, the Veeam Plug-In configuration file (veeam\_config.xml) is located in the %PROGRAMFILES%\Veeam\VeeamPluginforDB2 folder on the machine where Veeam Plug-In is installed. On Microsoft Windows machines, you can set up access to the plug-in configuration file using the graphic user interface or Windows PowerShell.

Granting Permissions in Graphic User Interface

1. Create a new user group:

1. Launch Computer Management and expand the System Tools > Local Users and Groups node.
2. Right-click the Groups node and select New Group.
3. Specify group properties and save the group.

1. Add users to the group.
2. In the configuration file properties, remove all permissions for other user groups.

|  |
| --- |
| Note |
| Some permissions can be inherited. To be able to remove such permissions, on the Security tab of the file Properties window, select Advanced, then click Disable Inheritance. |

1. Limit the permissions for the configuration file to allow the Read and Write access only to the members of the group.

Granting Permissions Using Windows PowerShell

1. Create a new user group by running the following command:

|  |
| --- |
| net localgroup "<groupName>" /comment:"<description>" /add |

where:

* <groupName> is the name of the created group.
* <description> is the description of the group.

1. Add a user to the group with the following command:

|  |
| --- |
| net localgroup "<groupName>" "<userName>" /add |

where:

* <groupName> is the name of the created group.
* <userName> is the name of the account that will be granted access to the configuration file.

1. Create a new access control list (ACL) with Read and Write permissions using this set of commands:

|  |
| --- |
| $newACL = New-Object System.Security.AccessControl.FileSecurity #creates a dedicated ACL $newACL.SetAccessRuleProtection($true,$false) #disables inheritance and deletes all inherited permissions $newACL.AddAccessRule( (New-Object System.Security.AccessControl.FileSystemAccessRule("groupName","Read","Allow"))) # allows read $newACL.AddAccessRule( (New-Object System.Security.AccessControl.FileSystemAccessRule("groupName","Write","Allow")))# allows write |

where:

* newACL is the name of the new access control list. You can give any name to this temporary variable.
* <groupName> is the name of the created group.

1. Assign ownership of the new ACL to the previously created user group by running the following command:

|  |
| --- |
| $newACL.SetOwner([System.Security.Principal.NTAccount]"groupName") #sets owner for the ACL |

1. Apply the ACL to the plug-in configuration file using this command:

|  |
| --- |
| Set-Acl -Path:<configFilePath> -AclObject:$newACL #apply ACL to the plug-in configuration file |

where:

* <configFilePath> is the path to the plug-in configuration file. The default path is %PROGRAMFILES%\Veeam\VeeamPluginforDB2\veeam\_config.xml.
* newACL is the name of the new access control list.

Page updated 2026-07-08

