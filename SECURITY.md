<!-- iHelp247 WP Intermission - (c) ULXI - UnLimited eXchange, Inc. - published under the iHelp247 brand - https://ihelp247.com - GPL-2.0-or-later -->
# Security Policy

## Supported versions

Only the latest release receives security fixes. Update through the Plugins screen (GitHub-release updates are built in) or install the newest release zip.

## Reporting a vulnerability

Please **do not open a public issue** for security problems. Use GitHub's private vulnerability reporting on this repository (Security → Report a vulnerability), or email the maintainer via the contact on [ihelp247.com](https://ihelp247.com), or via the parent company [ULXI](https://ulxi.com). You should receive an acknowledgment within 72 hours. Coordinated disclosure: we ask for a reasonable window to ship a fix before public details.

## Design posture (what attackers find here)

- No data collection: no cookies, forms, analytics, or tracking; nothing phones home. The only outbound requests are the optional Google Fonts stylesheet (visitor browser, opt-in per site) and a 12-hour-cached GitHub API check for plugin updates (server-side, metadata only).
- All settings input passes WordPress sanitizers (`sanitize_text_field`, `wp_kses_post`, `esc_url_raw`, `absint`, `sanitize_hex_color`); raw HTML modes are gated behind the `unfiltered_html` capability.
- AJAX preview is nonce-protected and requires `manage_options`.
- Generated drop-ins (`maintenance.php`, `db-error.php`) are marker-guarded: the plugin never overwrites files it did not create, and removes only its own on deactivation/uninstall.
- Fail-open serving: a missing template can never white-screen a site.

## Maintenance cadence

Dependencies: none (no Composer/npm packages — nothing to supply-chain). The plugin is reviewed against each major WordPress and PHP release; "Tested up to" in readme.txt reflects the last verified version.
