---
title: "Appendix. Restoring Synchronized Users (Hybrid Identity)"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_restore_sync_users.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Appendix. Restoring Synchronized Users (Hybrid Identity)


Veeam Backup for Microsoft Entra ID allows you to restore users synchronized with Microsoft Active Directory (hybrid identities). Unlike the synchronization software (for example, [Microsoft Entra Connect)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2), restore with Veeam Backup for Microsoft Entra ID preserves relations stored in the Entra ID: group memberships, assigned roles, used licenses and other relations.

Veeam Backup for Microsoft Entra ID restores properties and relations listed in [Supported Entra ID Item Properties](entra_id_properties.md). To restore other properties, you still need synchronization software and, in some cases, local Active Directory restore. This section describes possible scenarios and steps for restore.

User Removed from Entra ID Without Synchronization After

If a synchronized user was removed only from Entra ID, and there was no synchronization process after the removal, do the following:

1. Use Veeam Backup for Microsoft Entra ID to [restore an entire user](entra_id_tenant_restore_items_rp.md) to Entra ID. In the wizard, make sure that [restore of relations](entra_id_tenant_restore_options_mode.md) is enabled.

Veeam Backup for Microsoft Entra ID will restore a user with a new object ID.

1. Wait or launch synchronization with Active Directory, for example, using Microsoft Entra Connect.

After the synchronization, the relations restored using Veeam Backup for Microsoft Entra ID will be preserved, the properties will be overwritten, and lacking properties will be restored. The user will become the hybrid identity.

User Removed from Entra ID with Synchronization After

If a synchronized user was removed only from Entra ID, but the synchronization process has already restored this user, Veeam Backup for Microsoft Entra ID will not be able to map this user and restore the relationships. In this case, do the following:

1. Remove from Entra ID the user created after the synchronization.
2. Use Veeam Backup for Microsoft Entra ID to [restore an entire user](entra_id_tenant_restore_items_rp.md) to Entra ID. In the wizard, make sure that [restore of relations](entra_id_tenant_restore_options_mode.md) is enabled.

Veeam Backup for Microsoft Entra ID will restore a user with a new object ID.

1. Wait or launch synchronization with Active Directory, for example, using [Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2).

After the synchronization, the relations restored using Veeam Backup for Microsoft Entra ID will be preserved, the properties will be overwritten, and lacking properties will be restored. The user will become the hybrid identity.

User Removed from Entra ID and Active Directory

If a synchronized user was removed from Entra ID and Active Directory, do the following:

1. Use Veeam Backup for Microsoft Entra ID to [restore an entire user](entra_id_tenant_restore_items_rp.md) to Entra ID. In the wizard, make sure that [restore of relations](entra_id_tenant_restore_options_mode.md) is enabled.

Veeam Backup for Microsoft Entra ID will restore a user with a new object ID.

1. Use [application item restore](https://helpcenter.veeam.com/docs/backup/vsphere/restore_veeam_explorers.html?ver=120) or [Veeam Explorer for Microsoft Active Directory](https://helpcenter.veeam.com/docs/backup/explorers/vead_user_guide.html?ver=120) to restore the user locally in Active Directory.
2. Wait or launch synchronization with Active Directory, for example, using [Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2).

After the synchronization, the relations restored using Veeam Backup for Microsoft Entra ID will be preserved, the properties will be overwritten, and lacking properties will be restored. The user will become the hybrid identity.


