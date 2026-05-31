# by Maya — project context for Claude Code

A single-page website for Maya's custom commission art, hosted on GitHub Pages from this repo. Single `index.html`, no build step — edits go straight to live after `git push`.

Site stack:
- Single static `index.html` with inline `<style>` and `<script>`
- 5 painting images in the repo root
- Form submissions go to **Basin** (`https://usebasin.com/f/aeeb3cf675f3`) which emails Maya
- Hosted via GitHub Pages on the `main` branch

## ⚠️ IMPORTANT — Currently-removed sections

When asked to review the site, suggest improvements, or audit for missing things, **always flag the items below as deliberate removals to be revisited**. Don't silently treat their absence as "the site is complete".

### Testimonials section

**Status:** Removed from `index.html`.

**Why:** The section was built with placeholder quotes/names in `[brackets]` while waiting for real customer testimonials. Maya wanted to share the site with friends before having real testimonials, and the placeholders would have read poorly if anyone re-shared the site publicly.

**Where the design is preserved:** Git tag `testimonials-design-saved` (commit `0fd36fa`). To see what it looked like: `git show testimonials-design-saved -- index.html`. To restore: cherry-pick the relevant chunks back from that tag, then have Maya replace the placeholder text with real quotes before pushing.

**Where it used to live in the page:** Between the "How it works" section and the order form. A `<!-- Testimonials section temporarily removed -->` comment marks the slot.

**When to re-add:** As soon as Maya has 1+ real testimonials from past buyers. Even one real quote is better than three fake ones — when restoring, fewer cards is fine (the CSS uses `repeat(3,1fr)`, but it can be adapted to a 1-column or 2-column layout for fewer entries).

**What needs to come back:**
- CSS block (was in the section between trust-band and FAQ rules)
- Mobile media-query rules (`.testimonials-section`, `.testimonials-inner`, `.testimonials-grid`)
- HTML `<section class="testimonials-section">` block (was right before the order form)

## Project conventions

- Commit messages use a temp file (`.commit-msg-tmp`) because PowerShell mangles multi-line `-m` strings with embedded quotes. Pattern: `Write` the message, `git commit -F .commit-msg-tmp`, then `Remove-Item .commit-msg-tmp -Force`.
- Git identity in this repo is set locally to `gregory.troha@gmail.com` / `Gregory Troha` (not the global work identity).
- Tags are used as restore points before risky / temporary changes (`pre-jasmine-demo`, `testimonials-design-saved` already exist).

## Useful tags

| Tag | What it marks |
|---|---|
| `pre-jasmine-demo` | Pristine design before a one-off jasmine-scatter demo (reverted) |
| `testimonials-design-saved` | Last commit containing the placeholder testimonials section |
