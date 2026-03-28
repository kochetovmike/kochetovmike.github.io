# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# kochetovmike.github.io

Personal static one-pager for Mikhail Kochetov. Hub linking social/professional profiles, projects, credentials, and side projects.

## Stack

- Plain HTML + CSS (no framework, no build step)
- Hosted on GitHub Pages from `main` branch
- No JS dependencies unless explicitly added per feature

## Structure

- `index.html` — the entire site: markup, embedded `<style>` block, and inline `<script>` at the bottom
- `src/` — images and favicon
- `CNAME` — custom domain config (if applicable)

## Content Sections (in order)

1. Header — name, handle, social links (GitHub, LinkedIn, Instagram, X)
2. About Me — short personal/professional bio
3. Projects — Aethelon, AIM, One Page Apps (browsertools, dsvisuals)
4. Miscellaneous → Credentials — expandable table of certifications (Microsoft, Google, Palantir, Appian, Bloomberg)
5. Footer — copyright

## Editing Rules

- This is a single-page site. All content lives in `index.html`. Do not split into multiple pages unless explicitly asked.
- Preserve all outbound links exactly — social profiles, project URLs, credential verification URLs are critical and must not break.
- The credentials table uses a show/hide toggle (JS at the bottom of `index.html`). Keep this interaction pattern intact when editing.
- When adding a new project or credential row, match the existing markup pattern exactly.
- Keep the page lightweight — no heavy JS libraries, no build tooling. Vanilla HTML/CSS only.

## Credentials Table

Columns: Name | Provider | Difficulty | Valid From | Valid To | URL

Each `<td>` must have a `data-label="<Column Name>"` attribute — required for the mobile card layout (≤640px, CSS converts the table to stacked cards using `::before { content: attr(data-label) }`).

For rows with no verification URL, use `<td data-label="URL" class="no-link">-</td>`. The `no-link` class hides the cell on mobile.

## Style Guidelines

- Clean, minimal aesthetic. No flashy animations or gradients unless requested.
- Mobile-responsive. Test any layout change mentally for narrow viewports (≤640px breakpoint).
- Consistent link styling across all sections.
- Semantic HTML (`<section>`, `<table>`, `<header>`, `<footer>`).
- Two card types: `.block` (blue left border, outer) and `.block_inner` (purple left border, nested).

## Verification

- After any edit, confirm the markup is valid.
- Check that all external links are correct (don't fabricate URLs).
- Confirm every new `<td>` has the correct `data-label` attribute.

## Things Claude Gets Wrong Here

- Tends to over-engineer this into a React/Next.js app. Don't. It's intentionally a plain HTML file.
- Sometimes rewrites the entire file when only one section needs a change. Use targeted edits.
- May invent placeholder links or fake credential URLs. Never guess a URL — ask if unsure.
- There is no separate `styles.css` file — all CSS is in the `<style>` block inside `index.html`.
