<!-- iHelp247 WP Intermission - (c) ULXI - UnLimited eXchange, Inc. - published under the iHelp247 brand - https://ihelp247.com - GPL-2.0-or-later -->
# iHelp247 WP Intermission

*An iHelp247 by [ULXI, UnLimited eXchange, Inc.](https://ulxi.com) project. iHelp247 publishes tools, paying it forward to support the open-source community. Support: [ihelp247.com](https://ihelp247.com).*

**Easy by default, powerful when you need it, blocking nobody.** That's the design principle: a friendly Designer with live device preview opens on fresh install and gets a non-technical user to a beautiful page in two minutes — while template mode, full-HTML mode, filters, and a file override keep every door open for developers.

An **intermission** for your WordPress website: one checkbox puts the site backstage, visitors get a polished page — with a countdown, if you like, until the curtain goes back up. Three page sources: **Designer** (fields + live device preview, the default), a **styled template** with WYSIWYG-edited content, or a **fully custom HTML document** served byte-for-byte. Selectable `503` (short maintenance) or `200` (extended/coming-soon) response, countdown with launch action, core-update and database-failure coverage. No analytics, no upsells, no paywall.

Published by **iHelp247 — by ULXI** · GPL-2.0-or-later · Support: [ihelp247.com](https://ihelp247.com)

## What it does

- **Enabled** (Settings → WP Intermission): visitors receive the maintenance page with no-cache headers and your choice of HTTP 503 (search engines understand it's temporary) or 200 (`noindex` is set in the bundled template either way).
- Logged-in users who can edit content (`edit_posts` by default) **see the live site normally**, with a red **MAINTENANCE ON** badge in the admin bar so it's impossible to forget.
- `wp-admin`, `wp-login.php`, AJAX, and cron are never blocked.
- A **Preview** link on the settings page shows the maintenance page even while you're logged in (`/?ihelp247_wp_intermission_preview=1`).
- **WYSIWYG editing**: the page content is edited with WordPress's own editor — Visual tab for writing, Code tab for pasting raw HTML, Media Library button for images. Content is injected at `{{CONTENT}}` in the template.
- **Countdown timer**: put `{ihelp-wp-countdown}` anywhere in the content (or a custom template) and set a target date/time on the settings page — it renders a live days/hours/minutes/seconds counter styled to match the page. Empty target = token renders as nothing.
- **Core-update coverage**: while WordPress updates itself, plugins cannot run — core serves `wp-content/maintenance.php` instead, if present. Tick the checkbox and the plugin generates that drop-in as a static snapshot of the same page, regenerates it on every settings save, refuses to touch a drop-in it didn't create (unless you opt into **Force overwrite**, documented as unreliable — the file is only replaced on save, never monitored), and removes its own on deactivation/uninstall.
- **Corner credit**: the served page carries a small "intermission by iHelp247" link, removable with one checkbox on the settings page — free either way.

## Install

Download the latest release zip and install via **Plugins → Add New → Upload Plugin**, or clone into `wp-content/plugins/wp-intermission/`. Activate, then open **Settings → WP Intermission** — Designer mode greets you with a working page and a live device preview; tick Enabled and Save.

## Branding it for a client site (survives plugin updates)

Do **not** edit the plugin. Create a site override instead:

```
wp-content/wp-intermission/
├── template.html   ← your page (copy templates/template.html as a starting point)
├── bg.png          ← your images, any files template.html references
└── logo.png
```

If `wp-content/wp-intermission/template.html` exists, it is served instead of the bundled template. The settings page shows which template is active.

Placeholders available in any template:

| Placeholder | Replaced with |
|---|---|
| `{{ASSETS_URL}}` | `wp-content/uploads/wp-intermission/` by default (auto-created, update-proof, same relative path on every site) — or the `wp-content/wp-intermission/` override folder when a `template.html` exists there |
| `{{SITE_NAME}}` | The WordPress site title |
| `{{YEAR}}` | Current year |

## Configuration

Every tunable is a constant at the top of `wp-intermission.php`, in one labeled block: bypass capability, Retry-After seconds, option names, override folder, and the Support-row links (the Square checkout URL and the ihelp247.com/support link live there). Developers can also use the `ihelp247_wp_intermission_bypass`, `ihelp247_wp_intermission_html`, `ihelp247_wp_intermission_template_path`, `ihelp247_wp_intermission_assets_url`, and `ihelp247_wp_intermission_docs_url` filters.

## Supporting the project

The settings page ends with a low-key Support row: if someone has tried the plugin and it's earning its keep, they can leave a review or keep the energy drinks and coffee flowing — one Square checkout, any amount, one-time or monthly (chosen at checkout), straight to feeding the developers' break room. A Support link points at [ihelp247.com/support](https://ihelp247.com/support). All links open in a new tab so nobody loses their work. Next to it sits the checkbox that removes the corner credit from the served page — deliberately together and deliberately free: find, try, see value, let us know to keep going. The `assets/` folder ships the iHelp247 wordmark as dark and light SVGs.

## Updates & distribution

Distributed via GitHub Releases (this repo). **Updates are built in**: the plugin answers WordPress's native `update_plugins_github.com` hook (wired to the `Update URI:` header), so every install checks this repo's latest Release (12-hour cache) and updates through the standard Plugins screen — no third-party updater needed. Each Release must have the versioned plugin zip attached as an asset (GitHub's auto source zipball is deliberately ignored — its folder name would break the plugin slug). The `Update URI:` header also blocks wordpress.org from ever offering an unrelated same-slug plugin as an "update."

**Two builds ship per release.** The GitHub build (`wp-intermission-<version>.zip`, the Release asset) keeps the self-updater. The wordpress.org submission build (`wp-intermission-<version>-wporg.zip`) is identical except the GitHub-update block and the `Update URI:` header are removed, because the directory takes over update delivery and disallows third-party update sources. Never submit the GitHub build to the directory, and never attach the wporg build to a GitHub Release.

## Release & governance checklist

1. Bump the version in three places: plugin header, `IH247_WPIM_VERSION`, `Stable tag` in readme.txt. Add changelog entries to both readmes.
2. `php -l` both PHP files; run the burn-in (modes round-trip, countdown + end action, drop-in generate/remove, preview).
3. Build `wp-intermission-<version>.zip` (exclude `.gitignore`, `SECURITY.md` optional), commit, tag `v<version>`, create the GitHub Release **with the zip attached as an asset** — that asset is what every site updates from. Build `wp-intermission-<version>-wporg.zip` alongside it (updater block and `Update URI:` stripped) for the directory.
4. Security watch: enable GitHub private vulnerability reporting on the repo (see SECURITY.md), and monitor the WordPress ecosystem feeds (Patchstack / WPScan weekly reports) for issues in comparable plugins — same attack surface, early warning.
5. After each major WordPress/PHP release: test, then bump `Tested up to`.

## Media policy

The plugin ships **no site media** (only its own logo SVGs in `assets/`). Upload images through the WordPress Media Library ("Add Media" in the content editor, or Media → Add New) — they are stored in `wp-content/uploads/`, which WordPress never touches during plugin, theme, or core updates, so Media Library assets are update-proof by construction. Reference their URLs in your content or full-page HTML. The bundled template renders a clean dark gradient when no background image is configured, and a missing logo hides itself. (For filesystem-managed branding, the `wp-content/wp-intermission/` override folder remains available to developers.)

## Plesk WP Toolkit note

Plesk's WP Toolkit has its own maintenance-mode toggle. While it is on, WP Toolkit drops a `.maintenance` file in the WP root (with an always-fresh `$upgrading` timestamp, so it never expires) and installs its own `wp-content/maintenance.php` — which this plugin correctly detects as foreign and, by default, refuses to touch. **Use one owner per site:** leave WP Toolkit's maintenance toggle off and let this plugin manage maintenance. WP Toolkit removes both of its files when its toggle is turned off. (The Force overwrite option exists for stubborn cases, but it only acts when settings are saved — it does not monitor the file.)

## Privacy & compliance

The maintenance page as shipped **collects nothing**: no cookies, no forms, no analytics, no tracking, and — with fonts self-hosted — no external font or CDN calls. The corner "intermission by iHelp247" credit is a plain link (no beacon, no request until clicked) and is removable with one checkbox. The plugin itself phones nothing home. Compliance-by-not-collecting is the default posture. Designer mode includes a footer **disclaimer field** for site-specific GDPR/CCPA or other legal wording. If you later add anything that does collect (a notify-me form, analytics), that addition brings its own obligations — revisit then.

## Screenshots

GitHub: add screenshots to `.github/screenshots/` and reference them here. For the WordPress.org directory, screenshots follow the `screenshot-1.png, screenshot-2.png, …` convention in the plugin's `assets` SVN folder, matching the numbered list in `readme.txt`.

## Documentation & support

A plain-language **user guide with a self-diagnosis section** ships in the plugin at `docs/index.html` (works offline) and is linked from the settings page. To host it publicly, enable GitHub Pages on this repo (Settings → Pages → deploy from `main`, `/docs` folder) — it becomes the live support URL at `https://ihelp247.com/wp-intermission/` (or GitHub Pages until the site is live). Override the linked URL with the `ihelp247_wp_intermission_docs_url` filter.

## One repo, three audiences

- **README.md** (this file) — GitHub: developers, contributors, release/governance process.
- **readme.txt** — the WordPress parser: directory-format description, FAQ, screenshots list, changelog. Written to the [wordpress.org plugin guidelines](https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/).
- **docs/index.html** — end users: the plain-language guide + self-diagnosis, shipped in the plugin and hostable via GitHub Pages or any support site (settings-page link is filterable via `ihelp247_wp_intermission_docs_url`).

## Changelog

### 1.5.3 — 2026-07-26
- **Support row wired live.** One Square checkout button (any amount, one-time or monthly — chosen at checkout) replaces the two placeholder links, a **Support** link points at ihelp247.com/support, and the row's language now matches the checkout page (*keep the energy drinks and coffee flowing*). No functional changes to the served page or settings behavior.

### 1.5.2 — 2026-07-25
- **Documentation and language pass** across the plugin header, both readmes, and the user guide, aligning everything with the published project narrative (*easy by default, powerful when you need it, blocking nobody*). Introduced the **WordPress.org submission build**: an otherwise-identical zip with the GitHub self-updater and `Update URI:` header removed, as the directory requires (this repo's build keeps them). No functional changes to the served page, settings, or behavior.

### 1.5.1 — 2026-07-25
- **Initial public release.** Designer with true-scale device preview (monitor / laptop / phone chrome), styled-template and full-HTML page sources, 503/200 response control, countdown with at-zero actions (display / hide / take the site live), core-update and database-failure drop-in coverage with foreign-file protection plus an opt-in **Force overwrite** (documented as unreliable: replaced on save, never monitored), per-element fonts (system stacks / Google Fonts / self-hosted woff2), GitHub-powered updates through the standard Plugins screen, a no-collection privacy posture, a removable corner credit, and a Support row with review and coffee links. Earlier version numbers were internal development builds.
