---
title: "Configuring Users Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configuring_users_web.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Configuring Users Using Web UI


Adding Users

To add a user or user group:

1. From the top bar, select Configuration > Users & Roles.
2. Click Add.
3. In the Type field, select User or Group.
4. In the Name field, enter the name of a user or user group in the UPN format, for example, john.doe@tech.local.

To add a default domain security group, use the group@domain format, for example, Administrators@tech.local. For more information on all security groups, see this [Microsoft article](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups#default-active-directory-security-groups).

1. From the Role list, select the desired role.
2. Click OK.

To reduce the number of user sessions opened for a long time, you can set the idle timeout to automatically log off users. To do this:

1. Click Settings.
2. Activate the Auto logoff after <number> min of inactivity option and set the number of minutes.

For additional user verification, enable multi-factor authentication in the Settings section. For more information, see [Multi-Factor Authentication](mfa.md).

[![Configuring Users Using Web UI](images/users_roles_web.webp)](images/users_roles_web.webp)

Editing Users

To edit a user or user group:

1. From the top bar, select Configuration > Users & Roles.
2. Select a user or user group.
3. Click Edit.
4. In the Edit window, make necessary changes to the user or group.
5. Click OK.

Removing Users

To remove a user or user group:

1. From the top bar, select Configuration > Users & Roles.
2. Select a user or user group.
3. Click Remove.


