---
title: "Translation Updates"
slug: translation-updates
sections: [Features/Updates]
tags: [translations, locales]
status: publish
order: 90
toc: true
---

Each language is its own row because WordPress decides translation auto-updates one language at a time. UpdateBee follows that and stores an allow list and a block list by locale, such as `da_DK`.

The group policy is still on **Settings → Automatic updates**, under **Enable translation auto-updates** and **Configure**. This screen is where you choose the locales. See the article Automatic Update Policies.

## What the list contains

Open **Translations**. UpdateBee lists every locale from the WordPress.org translation catalog. Each row is keyed by its locale and shows:

- **Translation name**, the English name
- **Locale**, such as `da_DK`
- **Localized name**, the native name
- **Status**

Search uses **Search translations**.

## Screen modes

A notice at the top matches the **Settings** policy:

- **Automatic updates are enabled for all translations.**
- **Automatic updates are enabled, but only for the translations that are manually enabled.**
- **All updates are blocked. You will no longer receive any translation updates and may be a security risk.**
- **Automatic updates are disabled for all translations.**

The first notice is the all-enabled mode. The second is the custom mode, from **Selected translations** on **Settings**. The third is the fully blocked mode. The fourth is automatic updates off, which leaves translation offers available for a manual install.

## Enable or block one locale

In the custom mode, **Enable automatic updates** and **Disable automatic updates** apply to the selected locales. Those actions are available for locales that are not blocked.

**Block updates** and **Unblock updates** apply to one locale or to the selection. They stay available while translation updates are not fully blocked. A blocked locale is hidden from the WordPress updater along with other blocked offers. See the article Blocked Updates.

Translations have no **Patches only** control. There is no patches-only checkbox under **Configure** for translations, and the row has no patches toggle.
