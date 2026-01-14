---
title: "adfs_for_saml"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/adfs_for_saml.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---


In this article

Active Directory Federation Service (AD FS) is a hosted identity provider implemented as a feature in the Windows Server OS. It provides single sign-on capabilities for Active Directory (AD) users. If AD FS is used as the identity provider in the organization, to let AD users log in to the Veeam Backup Enterprise Manager website and vSphere Self-Service Backup Portal using the single sign-on service, an IT administrator must register the Veeam Backup Enterprise Manager website and vSphere Self-Service Backup Portal as service providers in AD FS.

To add a service provider in AD FS:

1. Obtain the service provider metadata exported from Veeam Backup Enterprise Manager. For more information, see [Configuring SAML Authentication Settings](veeam_backup_em_saml.md).
2. In AD FS, add a Relying Party Trust using the service provider metadata.
3. Edit the Claim Issuance Policy for the added Relying Party Trust to add an issuance transform rule with the following properties:

* Claim rule template = Transform an Incoming Claim

* Incoming claim type = UPN
* Outgoing claim type = NameID
* Outgoing name ID format = Persistent Identifier

1. [Optional] To provide single sign-on capabilities to AD groups, add to the Claim Issuance Policy an issuance transform rule with the following properties:

* Claim rule template = Send Group Membership as a Claim

* User's group = <Name>

where <Name> is a name of the AD group that includes users that will access the service provider.

When a user that belongs to the specified group attempts to access the service provider, the identity provider will issue an authentication assertion confirming that the user belongs to the group.

* Outgoing claim type = Group

Alternatively, if a different value is specified for the Group claim type option of advanced SAML settings in Enterprise Manager, the same value must be specified as the outgoing claim type in AD FS.

* Outgoing claim value = <Name>

where <Name> is a name of the group that will be returned to the service provider in authentication assertions.

This value can be different from the User's group value, for example, if you do not want the service provider to display AD group names. This value must be the same as the name of the account of the External Group type added in Enterprise Manager. For more information, see [Configuring Accounts and Roles](veeam_backup_em_roles.md) and [Adding Tenant Account](em_adding_tenant_accounts.md).

For example, you want to provide single sign-on capabilities to users that belong to the Backup AD group. In Enterprise Manager, you have the EnterpriseUsers account of the External Group type, and the default group claim type is specified in advanced SAML settings.

To allow these users to log in to Enterprise Manager with the single sign-on service, you must create an issuance transform rule with the following properties:

* Claim rule template = Send Group Membership as a Claim
* User's group = Backup
* Outgoing claim type = Group
* Outgoing claim value = EnterpriseUsers

Related Topics

* [SAML Authentication Support](em_saml.md)
* [Configuring SAML Authentication Settings](veeam_backup_em_saml.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
