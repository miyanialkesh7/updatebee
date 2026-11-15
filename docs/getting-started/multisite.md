---
title: "UpdateBee on Multisite"
slug: updatebee-on-multisite
sections: [Getting Started]
tags: [multisite, network]
status: publish
order: 30
toc: true
---

On a Multisite network, UpdateBee is a network plugin with one set of settings for the whole network. Activate it from the network admin. A site administrator inside one site of the network does not get a separate UpdateBee screen.

## Network activation

1. In the network admin, open **Plugins**.
2. Choose **Network Activate** for UpdateBee.

UpdateBee stores its settings as network options. A delay, a blocked plugin, a schedule, and a Slack webhook apply to the network, not to one site.

[placeholder - Network admin Plugins screen with Network Activate for UpdateBee]

## Where to open it

Go to the network admin and open **Settings → Automatic Updates**. The menu is registered for users who can `manage_network`.

[placeholder - Network admin Settings menu with Automatic Updates]

The same tabs are available as on a single site: **Settings**, **Plugins**, **Themes**, **Translations**, **Schedules**, **Emails**, **Logs**, **Tools**, and **Advanced**. Policies for plugins, themes, translations, and WordPress Core are the network policy.

## Network Admin toolbar

Users who can see the **Network Admin** toolbar menu get two shortcuts when that menu is present:

- **Updates** opens the network **Updates** screen for users who can `update_core`. UpdateBee places it directly under **Dashboard** in that menu.
- **Automatic Updates** opens UpdateBee for users who can `manage_network`.

[placeholder - Network Admin toolbar menu with Updates and Automatic Updates]

The optional admin bar menu on **Advanced** is separate. That menu can list UpdateBee's own tabs in the toolbar on wp-admin and on the front end. See the article Admin Bar Menu.

## Mail and logs

Email recipients and the Slack webhook are network settings. Logs are written for the network. Exporting settings from **Tools** downloads that network configuration. The Slack webhook is left out of the file. See the article Import and Export Settings.

> [!NOTE]
> Per-site plugin screens still show WordPress's own update controls. UpdateBee's automatic-update decisions are made in the network admin.
