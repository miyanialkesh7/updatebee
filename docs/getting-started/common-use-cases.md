---
title: "Common Use Cases"
slug: common-use-cases
sections: [Getting Started]
tags: [updates, delay, patches, rollback, logs]
status: publish
order: 20
toc: true
---

These are the setups most sites need after UpdateBee is active. Each one names the screen to open. The named article has the full behavior of that control.

Open UpdateBee from **Tools → Automatic Updates** on a single site, or from **Settings → Automatic Updates** in the network admin. See the article UpdateBee on Multisite when the site is a network.

## Hold new releases and let a security fix through

New plugin and theme releases sometimes need a follow-up patch. On **Advanced**, set **Delay Automatic Updates** to the number of days to wait. Use **0** when you want no wait.

If an upgrade notice contains a keyword you choose, that release can skip the delay. Open **Upgrade Notice Keywords** on the same tab, turn the list on, and keep one keyword per line. The default list includes `security`, `CSRF`, `XSS`, `CVE`, and `SSRF`, and the keyword check stays off until you enable it.

[placeholder - Advanced tab showing Delay Automatic Updates and Upgrade Notice Keywords]

The full rules, including a per-item delay and skipping the delay for one **Force Updates** run, are in the article Delay Updates.

> [!WARNING]
> While a release is delayed, the site keeps the older version, including when that older version has a security issue the notice did not match.

## Take patch releases only

On **Plugins** or **Themes**, turn on **Patches only** for an item whose minor fixes you want and whose larger releases you want to install yourself. The same choice is in the **Configure** menu on **Settings** for every plugin or every theme. Turning patches only on also allows automatic updates for that item.

[placeholder - Plugins row with the Patches only action]

Version-controlled packages cannot use patches only. Details are in the article Patches Only.

## Skip one bad version

When one release breaks a checkout or another screen, skip that version and leave automatic updates on for the next one. On **Plugins** or **Themes**, or on **Settings → Upcoming**, choose **Skip this version**. **Schedule update** puts that version back on the schedule.

See the article Skip a Version.

## Block one item, or turn a whole type off

**Block updates** on a plugin, theme, or translation hides that offer and keeps it from installing. The item disappears from **Upcoming**, because a blocked item cannot be installed and listing it would look like an update is available.

To stop every plugin, theme, or translation update, turn automatic updates off on **Settings** and choose **Disable all plugin updates**, **Disable all theme updates**, or **Disable all translation updates** from **Configure**. **Manual updates only** leaves the offers visible so you can install them yourself.

See the articles Blocked Updates and Automatic Update Policies.

## Leave version-controlled packages alone

A plugin or theme installed with Composer, Git, Subversion, or Mercurial is labeled **Version controlled** on **Plugins** and **Themes**. UpdateBee leaves automatic updates off, does not offer **Patches only**, and does not offer **Rollback**. **Upcoming** uses the same label. Update those packages with the tool that installed them.

[placeholder - Plugins row with the Version controlled badge]

See the article Version-Controlled Plugins and Themes.

## See what is about to install

Open **Settings** and choose the **Upcoming** subtab. The table lists pending plugin and theme releases, the version you have, the version on offer, and the next automatic install time. From a row you can skip that version, block the item, or choose **Update now** when the package can be installed.

[placeholder - Settings Upcoming subtab with a pending plugin row and its actions]

See the article Upcoming Updates.

## See what already ran

Open **Logs**. Filter by **Success**, **Failure**, **Fatal**, **Blocked**, **Skipped**, or **Delayed**, then open a row for the versions and notes. Export or clear the table from the same screen. Email and Slack reports read this history, so clearing it removes the source of those reports.

[placeholder - Logs screen with status filters and an open log detail]

See the article Logs.

## Run updates now, queue a check, or refresh the list

On **Tools**, three cards do different jobs:

- **Force Updates** installs Core, plugin, theme, and translation updates that are already allowed to update automatically. Confirm the run, and take a backup first. When a delay is set, you can skip it for this run.
- **Trigger the Update Cron** schedules the plugin, theme, and Core version checks for the next cron pass. The card states that this does not install updates.
- **Force Refresh Updates** clears the WordPress update cache and checks WordPress.org again. The command palette calls this **Refresh updates**.

[placeholder - Tools tab with Force Updates, Trigger the Update Cron, and Force Refresh Updates]

See the article Force Updates, Refresh, and Cron.
