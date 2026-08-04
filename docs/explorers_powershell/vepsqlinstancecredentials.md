---
title: "VEPSQLInstanceCredentials"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqlinstancecredentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VEPSQLInstanceCredentials


Contains a credential record used connect to a PostgreSQL database.

VEPSQLInstanceCredentials

| Property | Type | Description |
| UseLinuxUserForPeerAuthentication | Bool | If True, PostgreSQL will use the current OS user to authenticate to a PostgreSQL database. |
| PeerAuthenticationUser | String? | Linux OS user that PostgreSQL will use to authenticate to a PostgreSQL database. |
| UserName | String? | Username used for SQL authentication to a PostgreSQL database. |

Related Commands

[New-VEPSQLInstanceCredentials](new-vepsqlinstancecredentials.md)

Page updated 2026-06-25

