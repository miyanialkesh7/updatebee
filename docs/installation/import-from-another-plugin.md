---
title: "Import from Another Plugin"
slug: import-from-another-plugin
sections: [Installation]
tags: [migration, easy-updates-manager, companion-auto-update]
status: publish
order: 20
toc: true
---

UpdateBee can copy settings from Easy Updates Manager or Companion Auto Update when that plugin's saved data is still on the site. The cards sit on the **Tools** tab. A JSON file from another UpdateBee site is a separate path, covered in the article Import and Export Settings.

Open **Tools → Automatic Updates** on a single site, or **Settings → Automatic Updates** in the network admin. Then open **Tools**.

## When a card is shown

A migration card appears when UpdateBee finds that plugin's settings and the card has not been hidden. Easy Updates Manager is read from its saved options. Companion Auto Update is read from its settings table. After you hide a card, it stays off the **Tools** screen until you restore it.

[placeholder - Tools tab with Migrate from Easy Updates Manager and Migrate from Companion Auto Update]

## Migrate from Easy Updates Manager

The card is titled **Migrate from Easy Updates Manager**. Its description says it imports core, plugin, theme, and translation settings from Easy Updates Manager, and that overlapping UpdateBee settings will be replaced.

1. Select **Run Migration**.
2. Confirm **Run migration**. The confirmation says this will overwrite overlapping UpdateBee settings with values from Easy Updates Manager.

**Hide importer** opens **Hide importer?** After you hide the card, Easy Updates Manager settings can be imported again after you reset UpdateBee's import options.

## Migrate from Companion Auto Update

The card is titled **Migrate from Companion Auto Update**. Its description says it imports core, plugin, theme, and translation settings from Companion Auto Update, that overlapping UpdateBee settings will be replaced, and that you should deactivate Companion Auto Update afterward so its update filters do not override UpdateBee.

1. Select **Run Migration**.
2. Confirm **Run migration**. The confirmation says this will overwrite overlapping UpdateBee settings with values from Companion Auto Update.
3. Deactivate Companion Auto Update after the migration.

**Hide importer** uses the same **Hide importer?** confirmation. After you hide the card, Companion Auto Update settings can be imported again after you reset UpdateBee's import options.

## Show a hidden card again

On **Advanced**, open **Reset Options** and check **Reset importers**. The checkbox says it restores hidden importer cards on the Tools screen and that this does not reset UpdateBee settings. The rest of that drawer is in the article Reset and Deactivate.

## Copy settings between UpdateBee sites

**Import and Export Settings** on **Tools** downloads this site's settings as JSON or replaces them from a file. That transfer leaves the Slack webhook alone. The steps are in the article Import and Export Settings.
