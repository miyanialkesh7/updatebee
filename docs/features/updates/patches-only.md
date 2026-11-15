---
title: "Patches Only"
slug: patches-only
sections: [Features/Updates]
tags: [plugins, themes, patches]
status: publish
order: 20
toc: true
---

**Patches only** lets a plugin or theme install smaller releases on its own and leaves larger releases for you. A patch keeps the first two version numbers and changes a later number, such as 1.2.3 to 1.2.4. A jump such as 1.2.3 to 1.3.0 is left for a manual install. Translations have no patches-only mode.

The group-wide switch is on **Settings → Automatic updates**. The per-item switch is on **Plugins** and **Themes**. The policy screen is described in the article Automatic Update Policies.

## Turn it on for every plugin or theme

On **Settings → Automatic updates**, turn on **Enable plugin auto-updates** or **Enable theme auto-updates**. Open **Configure** and check **Patches only** under **Auto-update options**.

The summary beside **Configure** reads **Patches only**, or **Selected · Patches** when **Selected plugins** or **Selected themes** is also checked. While the main automatic-update toggle is off, **Patches only** is cleared and the menu offers **Manual updates only** or a full disable instead.

## Turn it on for one item

On **Plugins** or **Themes**, each row has a **Patches Only** toggle. The help text says it limits automatic updates for that item to patch releases. The bulk action is **Enable Patches Only**.

[placeholder - Plugins row with the Patches Only toggle and the Enable Patches Only bulk action]

Turning **Patches Only** on also turns automatic updates on for that item. Turning automatic updates off for the item clears patches only.

**Patches Only** is available while automatic updates are allowed for that type. If the **Settings** policy has automatic updates off, or the item is blocked, the toggle stays unavailable.

## What still installs

A matching upgrade notice can still install a release that is larger than a patch. That list is **Upgrade Notice Keywords** on **Advanced**, and it stays off until you enable it. See the article Delay Updates.

Version-controlled packages cannot be set to patches only. The row is labeled **Version controlled**, and both the toggle and the bulk action leave those packages unchanged. See the article Version-Controlled Plugins and Themes.

A release that is not a patch is recorded in **Logs** as skipped, with a note such as **Update is not a patch update**.
