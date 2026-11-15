---
title: "Install and Activate"
slug: install-and-activate
sections: [Installation]
tags: [installation, activation, multisite]
status: publish
order: 10
toc: true
---

UpdateBee 1.0.0 needs WordPress 7.0 or later and PHP 8.2 or later. After it is active, the settings screen is **Tools → Automatic Updates** on a single site. On a Multisite network the screen is in the network admin. Network behavior is in the article UpdateBee on Multisite.

## Install the plugin

1. In wp-admin, open **Plugins → Add New Plugin** and install UpdateBee, or upload the `updatebee` folder to `wp-content/plugins/`.
2. The plugin header marks it as a network plugin. On a single site, choose **Activate**. On Multisite, open the network admin **Plugins** screen and choose **Network Activate**.

[placeholder - Plugins screen with Activate on a single site, or Network Activate in the network admin]

A site inside a Multisite network does not get its own UpdateBee screen. One network activation covers the network.

## Open UpdateBee

On a single site, open **Tools → Automatic Updates**. The menu is available to users who can `manage_options`.

On Multisite, open the network admin and go to **Settings → Automatic Updates**. The menu is available to users who can `manage_network`. The article UpdateBee on Multisite covers network options, the Network Admin toolbar shortcuts, and why a site administrator inside one site does not see a separate screen.

[placeholder - Tools menu on a single site with Automatic Updates selected]

The screen opens on **Settings**. The other tabs are **Plugins**, **Themes**, **Translations**, **Schedules**, **Emails**, **Logs**, **Tools**, and **Advanced**.
