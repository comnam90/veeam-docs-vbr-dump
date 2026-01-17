---
title: "VETTeam"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vetteam.html"
last_updated: "7/15/2025"
product_version: "13.0.1.1071"
---

# VETTeam


Contains details about a Microsoft Teams team.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Team ID. |
| DisplayName | String | Team display name. |
| Description | String | Team description. |
| GroupEmail | String | Team email address. |
| Alias | String | Team alias. |
| Privacy | Visibility | Team visibility settings. Possible values:   * Public * Private |
| IsArchived | Bool | If True, the team is archived. |
| Settings | [VETTeamSettings](vetteamsettings.md) | Team settings. |

Related Commands

[Get-VETTeam](get-vetteam.md)


