---
title: "What UpdateBee Does"
slug: what-updatebee-does
sections: [Getting Started]
tags: [overview, backups]
status: publish
order: 10
toc: true
---

UpdateBee is the place to decide which WordPress updates may run on their own, when those checks happen, and how you hear about the result. It uses the WordPress update system. It schedules and filters automatic updates for WordPress itself, plugins, themes, and translations.

On a single site, open **Tools → Automatic Updates**. On a Multisite network, open the network admin and go to **Settings → Automatic Updates**. Network setup is covered in the article UpdateBee on Multisite.

[placeholder - Tools menu on a single site with Automatic Updates selected]

## What you can control

The **Settings** tab sets the broad policy: major and minor WordPress updates, and whether plugins, themes, and translations update automatically, only when you choose them, or not at all. The other tabs handle the exceptions.

- **Plugins**, **Themes**, and **Translations** set the rule for one item.
- **Schedules** sets when WordPress looks for Core, plugin, and theme updates.
- **Upcoming**, a subtab of **Settings**, lists plugin and theme releases that are waiting.
- **Logs** records each attempt.
- **Emails** and Slack send reports from that history.
- **Tools** can run allowed updates now, queue the next check, or refresh the list of available versions.
- **Advanced** holds the delay, untested-update block, Slack webhook, branding, admin bar, reset, and deactivate controls.

Everyday setups are collected in the article Common Use Cases.

## Command palette

From the WordPress admin, press **Command+K** on a Mac or **Ctrl+K** on Windows and search for UpdateBee commands. **Refresh updates** checks for new versions. **Force updates** runs the automatic updates that are already allowed. Both actions also appear on the **Tools** tab. See the article Force Updates, Refresh, and Cron.

[placeholder - WordPress command palette with Refresh updates and Force updates]

## Backups

Keep a backup before a major update, a rollback, or **Force Updates**. UpdateBee can return a WordPress.org plugin or theme to an older package that is still published, and it can record what changed. A rollback cannot undo every database change or compatibility problem, and the log is a history, not a copy of the site.

> [!WARNING]
> Take and test backups on a schedule. UpdateBee does not replace a backup plugin or your host's backups.

## Requirements

UpdateBee 1.0.0 requires WordPress 7.0 or later and PHP 8.2 or later. On Multisite it must be network-activated.
