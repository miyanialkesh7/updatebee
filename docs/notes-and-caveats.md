---
title: "Notes and Caveats"
slug: notes-and-caveats
kb_exclude: true
status: draft
---

Authoring notes for the UpdateBee knowledge base Markdown in this folder. This file is excluded from import.

## Frontmatter

Each article starts and ends its frontmatter with `---` on its own line. Leave out `products`. Knowledge Base Pro creates sections from `sections` and matches existing terms by slug, so keep the section names in these files exactly as written.

A file with no frontmatter is skipped. Set the repository mapping **Folder Path** to `docs/` so the import stays inside this folder.

## Headlines

The article headline comes from `title`. Do not repeat that title as a `#` heading in the body. Start with a lead paragraph, then `##` sections. A matching top-level heading is what made the headline appear twice after earlier imports.

## Screenshots

Where a screenshot should be added later, put this marker on its own line:

```text
[placeholder - Advanced tab with the Slack webhook URL field]
```

Describe the screen inside the brackets. Leave the marker as plain text. Do not turn it into a Markdown image or a `featured_image` path, or the importer will try to download a file. Developer hook articles do not use these markers.

## Links and alerts

Do not use Markdown links. The importer does not translate them well. Refer to other articles by title in plain text, for example: see the article Set Up a Slack Webhook. Name an external reference in prose the same way. Do not write a bracketed label followed by a parenthesized address, and do not paste a bare address as a link.

GitHub alerts (`[!NOTE]`, `[!TIP]`, `[!WARNING]`, `[!IMPORTANT]`, `[!CAUTION]`) are supported.
