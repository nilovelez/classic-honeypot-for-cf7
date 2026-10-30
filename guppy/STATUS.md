# Status

GPL fork of Honeypot for Contact Form 7 2.1.1 (Nocean), renamed Classic Honeypot for CF7 and free of ads. Milestones 1 to 5 are finished and merged into `main`. Milestone 5 set up the development environment (Playground with a blueprint, a Studio site linked to the repo and reachable from the local network, MCP Adapter connected to Claude Code), which will serve as the basis for a public skill. Local folder and GitHub repo renamed to the slug `classic-honeypot-for-cf7`.

**Published** on WordPress.org: https://wordpress.org/plugins/classic-honeypot-for-cf7/ (version 1.0.2, tested with WordPress 7.1.4 and Contact Form 7 6.2.4.1). Also released on GitHub. The SVN working copy is at `D:\repos-svn\classic-honeypot-for-cf7`; Nilo makes the SVN commits with TortoiseSVN, or asks Claude to commit (the command-line `svn` uses the cached credentials).

**Status:** inactive. No work in progress; reopen for maintenance when WordPress or Contact Form 7 releases need checking, or a support request comes in.

**Next step:** maintenance and support. For each new version: bump the version, `composer lint`, Plugin Check on the extracted zip, merge into `main`, GitHub release with the zip, then copy the `git archive` zip into SVN `trunk/`, `svn copy` it to `tags/<version>/` and give Nilo the commit message.

## Log

- 2026-10-30: Maintenance task closed. Status set to inactive. Everything committed and pushed; lessons logged in `wp-agentic-workflow/docs/lessons-learned.md`. The Studio site is stopped, updated to WordPress 7.1.4 and Contact Form 7 6.2.4.1.

- 2026-10-30: 1.0.2 published on WordPress.org (SVN r3774907, committed by Claude at Nilo's request). The plugin API shows 1.0.2 and the download is identical to the `git archive` zip. GitHub release `1.0.2` with the zip (the repo's first release; tags without "v", like SVN).

- 2026-10-30: 1.0.2 prepared: tested with WordPress 7.1.4 and Contact Form 7 6.2.4.1 (Playground: human submission sent; honeypot, too fast, future start and missing start time flagged as spam; settings menu, settings page and tag generator OK; clean debug.log). CF7 6.2.2 to 6.2.4.1 diff reviewed: only file uploads, UTF-8 scrubbing, REST permission callbacks and the dashboard; nothing the plugin uses. WordPress 7.1.4 is a security release. Plugin Check on the extracted zip: clean (run on the repo folder it flags `.claude`, `.github`, `CLAUDE.md` and the untracked `code-reference/`, all outside the zip). The Studio site did not start that day: `studio site start` asked for UAC permission to edit the hosts file (whose entries were already correct) and nobody was there to accept it, so the functional test ran in Playground. Cause not confirmed yet: Nilo will check whether it happens on every start.

- 2026-10-18: 1.0.1 published on WordPress.org (SVN r3753510): code in `trunk/` and `tags/1.0.1/`, images in `assets/` with `svn:mime-type=image/png`. The WordPress.org download is identical to the `git archive` zip. WordPress.org now delays plugin updates by six hours. WPCS set up in the repo with Composer (`composer lint`) from the workflow templates.

- 2026-10-18: Approved by WordPress.org. The automated pre-review (AI-assisted) had flagged three things: Guideline 11 (the two admin notices are justified error notices, kept), the name and the "CF7" trademark (the manual reviewers approved it as is, kept), and unescaped inline CSS in `includes/choneypot4cf7.php`. For the last one, 1.0.1 sanitizes the wrapper ID with `sanitize_html_class()` and strips tags from the filtered CSS. Tested in Playground: a `</style><script>` returned by the `wpcf7_honeypot_container_css` filter reached the page before the fix and is removed after it.

- 2026-10-16: migrated to the new Guppy format (STATUS.json).

- 2026-10-14: Another reviewer closed the submission without seeing the appeal notes (second rejection). When asked, the appeal reviewer asked us to upload it again and let him know in the thread so he can continue the review himself. Resubmitted.

- 2026-10-13: Appeal accepted for consideration: WordPress.org asked us to upload the zip again from the submission form and said a reviewer will get in touch. Resubmitted. Waiting for the manual review.

- 2026-10-12: WordPress.org rejects it as a duplicate of Honeypot for Contact Form 7. Appealed by replying to their email with `classic-honeypot-for-cf7-1.0.0.zip`: it is a direct copy of 2.1.1 (May 2021, the last Nocean release), the original was bought in July 2024, and since 2.1.1 it is an independent parallel development with no code from later changes. We also explained why the `[honeypot]` tag and the `wpcf7_honeypot_*` filters are kept. Waiting for a reply.

- 2026-10-11: Submitted to WordPress.org (1.0.0 zip from `312c621`). Initial slug `classic-honeypot-for-cf7`. Automated scan: Pass. The note to reviewers explains the fork and why the `[honeypot]` tag and the `wpcf7_honeypot_*` filters are kept.

- 2026-10-11: New icon (assets and settings screen at 64x64), screenshots retaken with it, and 772x250 and 1544x500 banners generated from `assets-src/` (HTML + script, excluded from the zip). `assets/` complete. Plugin ready to submit.

- 2026-10-11: Preparing the release (branch `feature/release-assets`): deleted `languages/` (and the Domain Path header), created `assets/` for the WordPress.org SVN (excluded from the zip) with the two readme screenshots and icon and banner placeholders. Final icon and banner design still pending.

- 2026-10-11: Branch `docs/readme` published on GitHub for Nilo's review: readme.txt rewritten in a neutral tone (independent fork developed in parallel since 2.1.1, no criticism of the original) and a new README.md (excluded from the zip). Plugin Check: 0 errors, 0 warnings (the `wpcf7_honeypot_*` filters are kept for compatibility with a justified `phpcs:ignore`; the WordPress.org review may ask to change them). Review of the original's fixes up to 3.7.2: everything applicable is already included.

- 2026-10-11: Branch `fix/settings-menu`: the settings page shows up again in the Contact menu as "Honeypot settings", at the end (CF7 6.2 changed the menu slug to `wpcf7-dashboard` and had left it hidden). Pending Nilo's review.

- 2026-10-11: Decided not to add abilities (Abilities API) to the plugin. Remaining: Nilo's review, minor changes (icon) and publishing on WordPress.org.

- 2026-10-11: Milestone 5 closed: MCP tested from a new Claude Code session; `feature/dev-environment` merged into `main`.

- 2026-10-11: Milestone 5, step 3: Studio site `classic-honeypot.local` with the plugin linked to the repo (junction), CF7 and a test page; reachable from the local network by adding the machine's IP to the hosts file. MCP Adapter 0.7.0 connected to Claude Code over STDIO (`studio wp mcp-adapter serve`, local scope, no application password). Playground also reachable on the local network with `--site-url`.

- 2026-10-11: GitHub repo renamed to `nilovelez/classic-honeypot-for-cf7`; remote and Plugin URI updated.
- 2026-10-11: Local folder renamed to `classic-honeypot-for-cf7` (the slug); Claude Code memory migrated and verified.
- 2026-10-11: Milestone 5, step 2: development blueprint.json; plugin tested in Playground (honeypot, time check and settings import, all correct).
- 2026-10-11: guppy/STATUS.md created.
