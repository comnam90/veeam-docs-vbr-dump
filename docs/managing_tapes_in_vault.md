---
title: "Managing Tapes in Vault"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/managing_tapes_in_vault.html"
last_updated: "6/29/2023"
product_version: "13.0.1.1071"
---

# Managing Tapes in Vault


When you have tapes placed to vaults, you can move them to another vault or remove from vault. When you remove tapes from a vault, they are still available in the Offline list or in their media pool.

To move tapes to another vault:

1. Open the Tape Infrastructure view and select the Vaults node. Select the vault where the needed tapes are stored.
2. In the working area, right-click the tapes you want to move and select Move to Vault. Select the target vault.

To remove tape from vault:

1. Open the Tape Infrastructure view and select the Vaults node. Select the vault you need.
2. In the working area, right-click the tapes you want to remove and select Remove from Vault.

The tapes are removed from vault automatically in the following situations:

* A tape comes online. It will re-appear in the vault when it goes offline if it was not erased or overwritten.
* A tape is removed from catalog.
* A tape is marked as free.


