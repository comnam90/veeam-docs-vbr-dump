---
title: "VETTeamSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vetteamsettings.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VETTeamSettings


Contains all settings for a Microsoft Teams team.

| Property | Type | Description |
| --- | --- | --- |
| AllowExternalSenders | Bool | If True, people external to the organization can send messages to the group. |
| AutoSubscribeNewMembers | Bool | If True, new members added to the group will be auto-subscribed to receive email notifications. |
| MemberSettings | [VETTeamMemberSettings](vetteammembersettings.md) | Team member settings. |
| GuestSettings | [VETTeamGuestSettings](vetteamguestsettings.md) | Guest user settings. |
| MessagingSettings | [VETTeamMessagingSettings](vetteammessagingsettings.md) | Messaging settings. |
| FunSettings | [VETTeamFunSettings](vetteamfunsettings.md) | Fun settings, related to stickers and memes. |


