---
title: "Actions"
slug: actions
sections: [Developer]
tags: [hooks, actions, logs]
status: publish
order: 10
toc: true
---

UpdateBee fires these actions from the logging flow and from the settings screen. Callbacks receive the arguments below. A short example is included where the timing matters.

Adding a screen with `updatebee_admin_tabs` is in the article Add an Admin Tab. Filters are in the article Filters.

## updatebee_automatic_updates_complete

Fires after an automatic update run has been written to the log.

```php
do_action( 'updatebee_automatic_updates_complete', $updates );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$updates` | `array` | Log rows collected during the request. |

Each row includes `name`, `slug`, `user_id`, `from_version`, `to_version`, `update_offer`, `update_type`, `update_status`, `date`, and `raw`. A fatal row also includes `fatal_message`, `detail_url`, and `detail_label`.

Rows rejected by `updatebee_allow_log_insert` are absent from this array. Email, Slack, and fatal reports listen here.

## updatebee_manual_updates_complete

Fires on shutdown after manual updates logged in the request have finished. It is skipped during an automatic run, and when the request logged nothing.

```php
do_action( 'updatebee_manual_updates_complete', $updates );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$updates` | `array` | Log rows from this request. The shape matches `updatebee_automatic_updates_complete`. |

The Logs Slack summary listens to this action for manual updates.

## updatebee_pre_log_insert

Fires immediately before a row is written, including when `updatebee_allow_log_insert` returns false. Returning false from that filter skips the database insert and skips `updatebee_after_log_insert`. This action still runs.

```php
do_action(
    'updatebee_pre_log_insert',
    $name,
    $slug,
    $user_id,
    $prev_version,
    $current_version,
    $update_offer,
    $update_type,
    $status,
    $notes
);
```

| Argument | Type | Description |
| --- | --- | --- |
| `$name` | `string` | Upgrade name. |
| `$slug` | `string` | Slug for the update. |
| `$user_id` | `int` | User responsible for the upgrade. Automatic runs use `0`. |
| `$prev_version` | `string` | Previous version. |
| `$current_version` | `string` | Version after the attempt. |
| `$update_offer` | `string` | `manual` or `automatic`. |
| `$update_type` | `string` | `plugin`, `theme`, `translation`, or `core`. |
| `$status` | `string` | `success`, `failure`, `blocked`, `skipped`, `delayed`, `install`, `deactivate`, `delete`, `rollback`, `update`, or `fatal`. |
| `$notes` | `string` | Raw upgrade notes, with URLs stripped. |

## updatebee_after_log_insert

Fires after the log row has been inserted.

```php
do_action(
    'updatebee_after_log_insert',
    $name,
    $slug,
    $user_id,
    $prev_version,
    $current_version,
    $update_type,
    $status,
    $notes
);
```

The arguments match `updatebee_pre_log_insert` except `$update_offer`, which this action does not pass. `$update_type` follows `$current_version`.

## Tab output actions

`Settings_Page` renders the active tab by calling `do_action()` with the `action` value from `updatebee_admin_tabs`. The hook name is whatever that tab registered. Built-in screens use:

- `updatebee_output_dashboard`
- `updatebee_output_plugins`
- `updatebee_output_themes`
- `updatebee_output_translations`
- `updatebee_output_cron`
- `updatebee_output_emails`
- `updatebee_output_logs`
- `updatebee_output_tools`
- `updatebee_output_advanced`

```php
do_action( $tab_action, $current_tab, $current_sub_tab );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$current_tab` | `string` | Active tab slug, such as `emails`. |
| `$current_sub_tab` | `string` or `null` | Active sub-tab slug, or null when the request has none. |

A custom tab should use its own `updatebee_output_*` name and check that the first argument is its slug before printing markup. The registration pattern is in the article Add an Admin Tab.

When `updatebee_admin_sub_tabs` supplies sub-tabs for the current screen, the active sub-tab also fires a dynamic action:

```php
do_action( 'updatebee_admin_sub_tab_' . $tab . '_' . $sub_tab, $current_sub_tab );
```

`$tab` and `$sub_tab` are passed through `sanitize_title()`. The only argument is the active sub-tab slug. The Upcoming list and the Schedule / Cron Events views are drawn inside the Settings and Schedules screens, so those controls do not each register a PHP sub-tab action.
