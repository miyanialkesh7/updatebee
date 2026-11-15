---
title: "Add an Admin Tab"
slug: add-an-admin-tab
sections: [Developer]
tags: [admin, tabs, hooks]
status: publish
order: 30
toc: true
---

`updatebee_admin_tabs` builds the row of screens on the UpdateBee settings page. `Settings_Page` starts with an empty list, passes it through the filter, and prints one link per item. The active item is rendered by calling `do_action()` with that item's `action` value.

The built-in screens follow one class shape. `includes/Admin/Templates/Emails.php` is the pattern: the constructor registers the filter and the output action, `add_emails_tab()` appends the tab, and `output_emails_content()` prints the screen only when its slug is active.

Hook arguments for the filter and the output action are listed in the articles Filters and Actions.

## Tab array

Each tab is an associative array:

| Key | Role |
| --- | --- |
| `get` | URL slug. `Settings_Page` compares it with the `tab` query argument. The Emails screen uses `emails`. The Settings screen uses `dashboard`, and Schedules uses `cron`. |
| `action` | Hook fired for the active tab. Emails uses `updatebee_output_emails`. Use a unique `updatebee_output_*` name for a custom screen. |
| `url` | Link href. `Functions::get_settings_url( $slug )` builds the single-site or network URL. |
| `label` | Visible tab label. |
| `icon` | SVG sprite id, such as `icon-email`. An empty string prints the label alone. |

Built-in callbacks use priorities 1 through 9, from Settings through Advanced. Pass a later priority to append a tab, or an earlier one to place it among the existing screens.

The output callback receives the current tab slug and the current sub-tab slug. Return immediately when the tab slug is not yours. `Settings_Page` passes both arguments, so the callback is registered with two accepted arguments.

## Register a screen

```php
add_filter( 'updatebee_admin_tabs', 'example_add_updatebee_tab', 20 );
add_action( 'updatebee_output_example', 'example_render_updatebee_tab', 10, 2 );

/**
 * Append a custom UpdateBee tab.
 *
 * @param array<int, array<string, string>> $tabs Registered tabs.
 * @return array<int, array<string, string>>
 */
function example_add_updatebee_tab( array $tabs ): array {
	$tabs[] = array(
		'get'    => 'example',
		'action' => 'updatebee_output_example',
		'url'    => \UpdateBee\Functions::get_settings_url( 'example' ),
		'label'  => __( 'Example', 'example-plugin' ),
		'icon'   => '',
	);

	return $tabs;
}

/**
 * Print the custom tab.
 *
 * @param string      $tab     Active tab slug.
 * @param string|null $sub_tab Active sub-tab slug.
 */
function example_render_updatebee_tab( string $tab, $sub_tab = '' ): void {
	if ( 'example' !== $tab ) {
		return;
	}

	echo '<p>' . esc_html__( 'Example screen.', 'example-plugin' ) . '</p>';
	unset( $sub_tab );
}
```

## Sub-tabs

`updatebee_admin_sub_tabs` receives the sub-tab list, the current tab slug, and the current sub-tab slug. Append items only for the parent slug you own. Each item needs `get`, `url`, and `label`. Build the URL with `Functions::get_settings_url( $tab, $sub_tab )`.

When sub-tabs exist, `Settings_Page` prints them and fires `updatebee_admin_sub_tab_{tab}_{subtab}` for the active one. Both slugs are passed through `sanitize_title()`, and the action receives the active sub-tab slug.

```php
add_filter( 'updatebee_admin_sub_tabs', 'example_add_updatebee_sub_tab', 10, 3 );

/**
 * Add a sub-tab under the Example screen.
 *
 * @param array<int, array<string, string>> $sub_tabs        Registered sub-tabs.
 * @param string|null                       $current_tab     Current tab slug.
 * @param string|null                       $current_sub_tab Current sub-tab slug.
 * @return array<int, array<string, string>>
 */
function example_add_updatebee_sub_tab( array $sub_tabs, $current_tab, $current_sub_tab ): array {
	unset( $current_sub_tab );

	if ( 'example' !== $current_tab ) {
		return $sub_tabs;
	}

	$sub_tabs[] = array(
		'get'   => 'details',
		'url'   => \UpdateBee\Functions::get_settings_url( 'example', 'details' ),
		'label' => __( 'Details', 'example-plugin' ),
	);

	return $sub_tabs;
}

add_action( 'updatebee_admin_sub_tab_example_details', 'example_render_updatebee_sub_tab' );

/**
 * Print the Details sub-tab.
 *
 * @param string $current_sub_tab Active sub-tab slug.
 */
function example_render_updatebee_sub_tab( string $current_sub_tab ): void {
	echo '<p>' . esc_html( $current_sub_tab ) . '</p>';
}
```

The Settings **Upcoming** subtab and the Schedules **Schedule** and **Cron Events** subtabs are drawn by those screens. They do not go through `updatebee_admin_sub_tabs`.
