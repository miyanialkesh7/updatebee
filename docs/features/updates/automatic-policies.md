---
title: "Automatic Update Policies"
slug: automatic-update-policies
sections: [Features/Updates]
tags: [settings, core, plugins, themes, translations]
status: publish
order: 10
toc: true
---

The **Settings** tab, subtab **Automatic updates**, is the policy for WordPress itself and for every plugin, theme, and translation. Individual exceptions live on **Plugins**, **Themes**, and **Translations**. On a Multisite network this screen is the network policy. See the article UpdateBee on Multisite for the network admin path.

Open **Tools → Automatic Updates** on a single site, or **Settings → Automatic Updates** in the network admin, then stay on **Settings → Automatic updates**.

[placeholder - Settings tab, Automatic updates subtab, with the core, plugin, theme, and translation toggles]

The panel is headed **Automatic Updates**. **Enable All** turns on major and minor WordPress updates and automatic updates for plugins, themes, and translations. **Disable All** turns those automatic updates off and leaves plugins, themes, and translations on **Manual updates only**.

## Major and minor WordPress updates

**Major WordPress Updates** explains that major updates are when you go from 5.5 to 5.6. The toggle is **Enable major core updates**.

**Minor WordPress Updates** explains that minor updates are when you go from 5.5.1 to 5.5.2, and that these are usually security and maintenance patches. The toggle is **Enable minor core updates**.

A fresh install leaves major updates off and minor updates on. **Save Settings** stores either toggle.

## Plugin, theme, and translation toggles

Each group has one main toggle:

- **Enable plugin auto-updates**
- **Enable theme auto-updates**
- **Enable translation auto-updates**

Translations start with automatic updates on. Plugins and themes start with automatic updates off, which leaves them on **Manual only**.

**Configure** sits under each toggle. The menu changes with the toggle.

When automatic updates are on, **Auto-update options** offers:

- **Selected plugins**, **Selected themes**, or **Selected translations**, so only the items you enable on that tab update automatically.
- **Patches only** for plugins and themes. Translations have no patches-only choice.

When automatic updates are off, **When auto-updates are off** offers:

- **Manual updates only**, so WordPress still shows the offers and you install them yourself.
- **Disable all plugin updates**, **Disable all theme updates**, or **Disable all translation updates**, so that whole type is blocked.

Turning the main toggle off clears the selected and patches-only choices for that group. If the group was already fully disabled, it stays disabled. Otherwise it returns to **Manual updates only**.

## What the summary means

The text beside **Configure** is the current policy:

| Summary | Meaning |
| --- | --- |
| **All plugins**, **All themes**, or **All translations** | Automatic updates are on for the whole group. |
| **Selected plugins**, **Selected themes**, or **Selected translations** | Automatic updates are on only for the items you enable. |
| **Patches only** | Every plugin or theme that updates automatically is limited to patch releases. |
| **Selected · Patches** | Only the plugins or themes you enable update automatically, and those updates are limited to patch releases. |
| **Manual only** | Automatic updates are off. Offers stay available for you to install. |
| **Disabled** | Updates for that whole type are blocked. |

**Save Settings** stores the policy. **Discard Changes** drops unsaved edits. **Reset to Defaults** restores the form defaults. Per-item controls, including **Patches only** on a single row, are in the article Patches Only. Blocking one item while the type stays available is in the article Blocked Updates.
