---
title: "Filters"
slug: filters
sections: [Developer]
tags: [hooks, filters]
status: publish
order: 20
toc: true
---

These filters are applied by UpdateBee. Return the same type the docblock describes. Tab registration is expanded in the article Add an Admin Tab. The matching actions are in the article Actions.

## updatebee_email_log_cutoff_days

Filters the maximum number of days of logs included in a success or failure email. It runs for the scheduled send and for **Preview email**. The stored field still defaults to 7 days and is clamped to at least 1 before this filter.

```php
$cutoff_days = (int) apply_filters( 'updatebee_email_log_cutoff_days', $cutoff_days, $log_status );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$cutoff_days` | `int` | Number of days. |
| `$log_status` | `string` | `success` for success reports, `failure` for failure reports. |

Available-updates mail uses its own send and preview methods and does not apply this filter.

## updatebee_allow_log_insert

Filters whether the current log row may be stored. The default is `true`. `updatebee_pre_log_insert` still fires when this returns false. The insert, `updatebee_after_log_insert`, and the row inside the completion actions are skipped.

```php
add_filter( 'updatebee_allow_log_insert', '__return_false' );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$allow_insert` | `bool` | True to allow the insert. |

## updatebee_log_table_limit

Caps how many log rows a query returns. Two call sites pass different defaults. A filtered value below 1 is replaced with that call site's default.

| Call site | Default | What it limits |
| --- | --- | --- |
| `Logs::get_logs_by_status()` | `100` | Success and failure email queries. Failure reports request both `failure` and `fatal` rows. |
| `Table_Logs::get_logs()` | `500` | The recent-rows query used by the Logs screen, newest first. |

```php
$limit = absint( apply_filters( 'updatebee_log_table_limit', $default ) );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$limit` | `int` | Maximum rows. The default depends on the call site above. |

## updatebee_export_log_limit

Caps the CSV export from **Export Logs**. The default is `500`. A filtered value below 1 is replaced with `500`.

```php
$limit = absint( apply_filters( 'updatebee_export_log_limit', 500 ) );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$limit` | `int` | Maximum exported rows. |

## updatebee_migrate_eum_mapped_options

Filters Easy Updates Manager options after they have been mapped and before they are saved.

```php
return (array) apply_filters( 'updatebee_migrate_eum_mapped_options', $mapped, $source );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$mapped` | `array` | Mapped UpdateBee options. |
| `$source` | `array` | Normalized Easy Updates Manager options. |

## updatebee_migrate_cau_mapped_options

Filters Companion Auto Update options after they have been mapped and before they are saved.

```php
return (array) apply_filters( 'updatebee_migrate_cau_mapped_options', $mapped, $source );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$mapped` | `array` | Mapped UpdateBee options. |
| `$source` | `array` | Companion Auto Update rows, setting name to stored value. |

## updatebee_admin_tabs

Filters the settings tabs before they are printed. The default passed in is an empty array. Each built-in screen appends one tab. The array shape and a full example are in the article Add an Admin Tab.

```php
$tabs = apply_filters( 'updatebee_admin_tabs', $tabs );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$tabs` | `array` | List of tab arrays. Each item uses `get`, `action`, `url`, `label`, and `icon`. |

## updatebee_admin_sub_tabs

Filters sub-tabs for the current screen. The default is an empty array. UpdateBee's Upcoming and Cron Events subtabs are rendered by those screens' scripts. This filter is the PHP path for an extra sub-tab.

```php
$sub_tabs = apply_filters( 'updatebee_admin_sub_tabs', array(), $current_tab, $current_sub_tab );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$sub_tabs` | `array` | List of sub-tab arrays. |
| `$current_tab` | `string` or `null` | Current tab slug. |
| `$current_sub_tab` | `string` or `null` | Current sub-tab slug. |

## updatebee_manage_options_capabilities

Filters the capability required to see the UpdateBee menu. The default is `manage_options` on a single site and `manage_network` on Multisite.

```php
$capabilities = apply_filters( 'updatebee_manage_options_capabilities', $capabilities );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$capabilities` | `string` | Capability passed to `add_submenu_page()`. |

## updatebee_fatal_result_codes

Filters the `WP_Error` codes treated as a fatal update result. The defaults are `plugin_update_fatal_error_rollback_successful` and `plugin_update_fatal_error_rollback_failed`. A non-array return is ignored and the defaults are kept.

```php
$fatal_codes = apply_filters( 'updatebee_fatal_result_codes', $codes );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$codes` | `array` | Error codes. |

## updatebee_fatal_detection_urls

Filters the loopback URLs requested after a successful automatic plugin or theme update, when fatal detection is on. The defaults are the site front URL and the wp-admin URL. On Multisite the request runs on the main site. A non-array return is treated as an empty list.

```php
$urls = apply_filters( 'updatebee_fatal_detection_urls', $urls, $update_results );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$urls` | `array` | URLs to scrape. |
| `$update_results` | `array` | Automatic update results, keyed by type. |

## updatebee_fatal_email_recipients

Filters fatal-report recipients after the saved list is sanitized. Valid addresses from an array return replace the list. When the result is empty, UpdateBee uses the site admin email if that address is valid.

```php
$filtered = apply_filters( 'updatebee_fatal_email_recipients', $emails );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$emails` | `array` | Recipient list. |

## updatebee_options_defaults

Filters the option defaults merged under saved settings. Defaults include update policies, log retention, the Slack URL, the delay, upgrade-notice keywords, fatal detection (`true`), branding, and the admin bar toggles (`admin_bar_enabled` false, show-admin and show-frontend true).

```php
return (array) apply_filters( 'updatebee_options_defaults', $defaults );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$defaults` | `array` | Option key to default value. |

## updatebee_options_save_pre

Filters the full options array immediately before it is written. `Options::update_options()` applies it on each successful save branch: updating one existing key from an array payload, replacing the whole array, or assigning an array onto an existing key.

```php
$cached_options = apply_filters( 'updatebee_options_save_pre', $cached_options, $key, $options, $force );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$cached_options` | `array` | Options about to be saved. |
| `$key` | `string` | Option key being updated, or an empty string for a full-array save. |
| `$options` | `mixed` | Incoming options. |
| `$force` | `bool` | Whether the save reloaded options from the database first. |

## updatebee_plugin_name

Filters the display name. The default is `UpdateBee`. Saved branding replaces that default when the name field is filled in. Emails, Slack, and the settings header use this value.

```php
return (string) apply_filters( 'updatebee_plugin_name', $plugin_name );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$plugin_name` | `string` | Plugin name. |

## updatebee_plugin_menu_name

Filters the wp-admin submenu label and the admin-bar label. The default is `Automatic Updates`. The branding name field filters `updatebee_plugin_name` and leaves this menu label in place.

```php
return (string) apply_filters( 'updatebee_plugin_menu_name', $menu_name );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$menu_name` | `string` | Menu name. |

## updatebee_plugin_menu_title

Filters the settings page title passed to `add_submenu_page()`. The default is the current plugin name from `updatebee_plugin_name`, so a branded name is used here.

```php
return (string) apply_filters( 'updatebee_plugin_menu_title', $plugin_title );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$plugin_title` | `string` | Page title. |

## updatebee_slack_message

Filters the Slack payload for the Logs completion summary before it is posted. An empty or non-array return cancels the post. The switch is **Enable Slack notifications**, and a webhook must already be saved.

```php
$message = apply_filters( 'updatebee_slack_message', $message, $rows, $offer );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$message` | `array` | Block Kit payload. |
| `$rows` | `array` | Normalized log rows. |
| `$offer` | `string` | `automatic` or `manual`. |

## updatebee_slack_fatal_message

Filters the Slack payload for a fatal alert before it is posted. An empty or non-array return cancels the post. Fatal reports and **Notify Slack when a fatal error is detected** must be on, and a webhook must be saved.

```php
$message = apply_filters( 'updatebee_slack_fatal_message', $message, $rows );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$message` | `array` | Block Kit payload. |
| `$rows` | `array` | Normalized fatal rows. |

## updatebee_slack_available_updates_message

Filters the Slack payload for the available-updates report before it is posted. An empty or non-array return cancels the post. **Notify Slack when this report runs** must be on, and a webhook must be saved.

```php
$message = apply_filters( 'updatebee_slack_available_updates_message', $message, $rows );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$message` | `array` | Block Kit payload. |
| `$rows` | `array` | Normalized pending-update rows. |

## updatebee_composer_installed_files

Filters the absolute paths of Composer `installed.json` files UpdateBee reads when it decides that Composer owns a plugin or theme. A plugin's own `composer.json` is not a manifest. A non-array return is ignored.

```php
$filtered = apply_filters( 'updatebee_composer_installed_files', $files );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$files` | `array` | Absolute paths to `installed.json` files. |

## updatebee_force_updates_disable_lock

Filters whether **Force Updates** deletes the `auto_updater.lock` option before `wp_maybe_auto_update()` runs. The default is `true`, which deletes the lock. Return `false` to leave the lock in place.

```php
$disable_lock = apply_filters( 'updatebee_force_updates_disable_lock', true, $updater_lock );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$disable_lock` | `bool` | True deletes the lock. The default is true. |
| `$updater_lock` | `string` | Current `auto_updater.lock` value, when one exists. |

## updatebee_normalized_call_stack_args

Filters the normalized debug backtrace before it is serialized into a log row's stack trace. The value is the array returned by UpdateBee's backtrace normalizer. Return an array.

```php
$normalized = apply_filters( 'updatebee_normalized_call_stack_args', $normalized );
```

| Argument | Type | Description |
| --- | --- | --- |
| `$normalized` | `array` | Normalized stack frames. |

## WordPress filters UpdateBee relies on

These are WordPress core filters. UpdateBee hooks them for a feature, and they are not UpdateBee hooks:

- `auto_update_translation` runs once per language item. The Translations screen stores allow and block lists by locale, and UpdateBee's callback reads those lists.
- `all_plugins` supplies the Plugins screen row that branding replaces, and the installed-plugin list UpdateBee reads.
- `all_themes` supplies the installed-theme list UpdateBee reads.
- `https_local_ssl_verify` is applied to the fatal-detection loopback request.
