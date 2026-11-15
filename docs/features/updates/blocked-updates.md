---
title: "Blocked Updates"
slug: blocked-updates
sections: [Features/Updates]
tags: [blocked, plugins, themes, translations]
status: publish
order: 70
toc: true
---

Blocking hides one plugin, theme, or translation offer and keeps it from installing. Disabling a whole type is a different control on **Settings → Automatic updates**: **Disable all plugin updates**, **Disable all theme updates**, or **Disable all translation updates**. That group policy is in the article Automatic Update Policies.

A blocked offer is removed from the WordPress updater, so the usual Updates screen no longer lists it. UpdateBee's own screens can still show that the item is blocked.

## Block one plugin or theme

On **Plugins**, the row toggle is **Block All Updates**. The bulk actions are **Block Selected Plugins** and **Unblock Selected Plugins**.

On **Themes**, the bulk actions are **Block Selected Themes** and **Unblock Selected Themes**, with the same idea on the row.

While that type is fully disabled on **Settings**, the block actions are unavailable because the whole type is already blocked.

A blocked plugin or theme is left off **Upcoming**. It cannot be installed, and listing it would look like an update is available. If plugin updates or theme updates are fully disabled, that type contributes no upcoming rows. See the article Upcoming Updates.

## Block one translation

On **Translations**, the row and bulk actions are **Block updates** and **Unblock updates**. Each language is its own row, so a block applies to that locale. How the list is built is in the article Translation Updates.

**Block updates** stays available while the type itself is not fully disabled. When **Settings** is set to **Disable all translation updates**, the screen says all updates are blocked.

## What you still see

**Logs** can record a blocked attempt with the status **Blocked**. **Upcoming** omits blocked plugins and themes. Manual install from the WordPress updater is hidden for a blocked offer, because the offer is filtered out of the update list.
