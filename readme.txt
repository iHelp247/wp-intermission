=== iHelp247 WP Intermission ===
Contributors: ihelp247, ulxi
Donate link: https://square.link/u/NSPL6UTY
Tags: maintenance mode, coming soon, 503, under construction, countdown
Requires at least: 6.0
Tested up to: 6.9
Requires PHP: 7.4
Stable tag: 1.5.3
License: GPL-2.0-or-later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Maintenance and coming-soon pages for WordPress, easy by default and powerful when needed: Designer with true-scale device preview, countdown with launch action, 503/200 control, coverage for core updates and DB failures. Collects nothing.

== Description ==

iHelp247 WP Intermission is published by iHelp247 — by ULXI (UnLimited eXchange, Inc.). iHelp247 publishes tools, paying it forward to support the open-source community. Support: https://ihelp247.com/

An intermission for your WordPress website: one checkbox puts the site backstage, visitors get a polished page — with a countdown, if you like, until the curtain goes back up. Easy by default, powerful when you need it, blocking nobody: a friendly Designer with live device preview opens on fresh install and gets a non-technical user to a beautiful page in two minutes, while template mode, full-HTML mode, filters, and a file override keep every door open for developers.

One checkbox under Settings → WP Intermission. When enabled, visitors get your maintenance page; users who can edit content see the live site, with a red MAINTENANCE ON admin-bar badge. wp-admin, login, AJAX, and cron are never blocked.

Three page sources: Designer — simple fields (background, logo, title, subtitle, text, colors, sizes, fonts, disclaimer) with a live preview pane, no code needed; a styled template whose content you edit with the WordPress editor (Visual/Code tabs, Media Library); or Full custom HTML — paste a complete document per site and it is served exactly as written. Choose 503 + Retry-After for short maintenance or 200 OK for extended maintenance/coming-soon. A {ihelp-wp-countdown} token renders a live countdown to a date you set, with an optional end action that takes the site live at T-0. Optional coverage generates wp-content/maintenance.php (shown while WordPress itself updates) and wp-content/db-error.php (shown when the database is unreachable).

Fonts: system stack (zero external calls), a Google Font by name, or a self-hosted .woff2 for licensed custom fonts. The page as shipped collects nothing — no cookies, forms, analytics, or tracking.

Tokens supported everywhere: {ihelp-wp-countdown}, {{ASSETS_URL}}, {{SITE_NAME}}, {{YEAR}}. Developers can additionally override the bundled template via wp-content/wp-intermission/template.html.

The served page carries a small "intermission by iHelp247" link in the corner; a checkbox on the settings page removes it. Free either way — the link just helps others find the plugin.

== Frequently Asked Questions ==

= Does the countdown turn the site live by itself? =
Only if you enable the end action. By default the countdown is display-only.

= Another tool says it manages maintenance (control panel, host portal) =
Some tools install their own wp-content/maintenance.php and keep it there permanently, toggling only the hidden .maintenance flag. This plugin detects foreign files and does not overwrite them by default — use one owner per site. If you can't remove the other tool, a Force overwrite option is available, but treat it as unreliable: the file is only checked and replaced when you save this plugin's settings — it is not monitored, and the other tool can put its own copy back at any time.

= Does this plugin collect any data? =
No. No cookies, no analytics, nothing phones home. With the system or self-hosted font option there are no external requests at all.

= How do I remove the iHelp247 link on the page? =
Tick the checkbox at the bottom of the settings page. It's free and stays free — no upsell attached.

== Screenshots ==

1. Settings screen — mode selection, response code, countdown, coverage options.
2. Designer mode with live preview pane.
3. The served maintenance page with countdown.
4. Admin-bar badge with live countdown while maintenance is on.

== Installation ==

1. Upload the plugin zip via Plugins → Add New → Upload Plugin, and activate.
2. Open Settings → WP Intermission. Designer mode greets you with a working page and a live device preview — adjust background, text, and fonts to taste.
3. Tick Enabled, press Save Changes, and check the result in a private/incognito window (logged-in editors always see the live site).
4. Power users: switch Page source to the styled template or full custom HTML; developers can override the template at wp-content/wp-intermission/template.html.

== Changelog ==

= 1.5.3 =
* Support row: wired in the live checkout link (one button — any amount, one-time or monthly, chosen at checkout), added a Support link (ihelp247.com/support), and matched the language to the checkout page. No functional changes to the served page or settings behavior.

= 1.5.2 =
* Documentation and language pass across the plugin, readmes, and user guide to match the published project narrative. Introduced a separate WordPress.org submission build (identical plugin, with the GitHub self-update mechanism removed, as directory rules require). No functional changes to the served page, settings, or behavior.

= 1.5.1 =
* Initial public release. Designer with true-scale device preview (monitor/laptop/phone), styled-template and full-HTML page sources, 503/200 response control, countdown with at-zero actions (display / hide / take the site live), core-update and database-failure drop-in coverage with foreign-file protection plus an opt-in Force overwrite, per-element font system (system stacks / Google Fonts / self-hosted woff2), GitHub-powered updates through the standard Plugins screen, and a no-collection privacy posture. Earlier version numbers were internal development builds.
