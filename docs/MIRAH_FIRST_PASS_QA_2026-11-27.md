# MIRAH Website — First-pass QA Review

## Foundation v1 — main-site rebuild (2026-11-27, Sam approved re-study)

What was done: `index.html` was rebuilt as a clean foundation (575 lines, 48 KB, one `<style>` block, one `<script>` block). No layered CSS overrides remain on the main page.

Diagnosis confirmed from source:
- Old file had 7+ layered CSS blocks with `!important` overrides, conflicting `.reveal` definitions (opacity 0 + blur 4px, later overridden to opacity 1), conflicting hero heights (740px, then 0), and ~300 lines of dead AI-hero / device-mockup / particles / cursor-glow CSS and JS for elements that do not exist in the HTML (`ai-stage`, `ai-console`, `aiChatForm`, `mirahCursorGlow`). All removed.
- No black floating controls exist in the site source. The only fixed element is the 3px gradient progress line (`.topline`); the header is sticky, not floating. CORRECTION (live check 2026-11-27 06:20): the small black floating button on the Preview is Vercel's preview Toolbar — a preview-only tool, not site content and absent on Production. The earlier "Android system / accessibility UI" explanation was wrong.
- Ticker: old track duplicated content but sat inside conflicting overflow rules. Foundation ticker uses one duplicated track, `overflow:hidden`, `width:max-content`, and stops under reduced motion.
- Excess vertical space: old hero padding 86px + 100px, plus stacked section padding (90px) and strip padding. Foundation uses one rhythm: hero 64px/56px desktop, 40px/44px mobile; sections 64px desktop, 48px mobile.

Foundation v1 guarantees:
- Content is visible without JavaScript: `.reveal` has no hidden state in CSS; JS only adds a one-time entrance animation via `.in-view`. If JS or the observer fails, content stays visible.
- No duplicate IDs (checked 2026-11-27, all IDs unique). One script block; no references to missing elements.
- Mobile menu: toggle + Escape to close + close on link click + `aria-expanded`. Active nav link via IntersectionObserver.
- Contact form unchanged in behaviour: local brief only, clipboard with manual fallback, explicit "has not been sent" status.
- Brand, copy, six services, four experience tabs, four industry tabs, two portfolio cards, process, and footer preserved. Hero visual is now a truthful CSS-only concept preview, not a fake device or fake AI chat.

## Live Preview QA — Vercel Preview dpl_J4Wc8CcLAwHgu4uTFBTayyBzQQLz (2026-11-27 06:20–06:23, device browser, phone screen)

- Deployment: GitHub commit ad8c16a auto-deployed by Vercel; state READY. URL https://mirah-digital-mplt760vo-samalshishani084.vercel.app (SSO Deployment Protection on — viewer must be signed in to Vercel).
- Visual: PASS at phone width. Hero "Make your next digital move count.", six services, ticker, process, contact form, footer — all render, no blank/hidden sections, no broken or overlapping content.
- Mobile menu: PASS. Hamburger opens (Services, Industries, Portfolio, Our process, Contact); tapping Services closes the menu and jumps to #services.
- Experience tabs: PASS. Four tabs — 01 Design that earns trust, 02 Journeys that convert, 03 Smarter business systems, 04 Built to keep improving — all switch panels. (Note: no tab is labelled "Growth"; that was a wrong label in the test instruction, not a site defect.)
- Industry selector: PASS. Automotive / Home services / Contractors / Professional services; selecting Home services shows its panel with the honest "illustrative directions, not completed client work" disclaimer.
- Brief form: DEFECT FOUND + FIXED (same day). Empty submit correctly triggered native validation ("Please fill out this field."). But a filled submit showed "Your project brief was copied to your clipboard" while the brief box stayed empty and nothing was in the clipboard. Root cause, two compounding bugs: (1) `.field{display:grid}` overrode the `hidden` attribute, so the fallback box was always visible and empty; (2) `navigator.clipboard.writeText` resolves without throwing in in-app WebViews even when the write silently fails, so the code claimed a copy that never happened. Fix: global `[hidden]{display:none!important}`; the brief is now ALWAYS rendered visibly in the box on submit; the status only claims a copy when the Clipboard API call really succeeded; a visible "Copy brief" button retries the copy and reports the real result. Re-test pending on the next Preview deployment.
- Minor: tight letter spacing on gradient words in some headings (e.g. "to a" in the process heading) — readable. Fix: `.gradient` letter-spacing set to -.015em in the same commit.

Status: main site — PARTIAL (source + static checks DONE; live mobile visual + interaction QA DONE at one phone width; desktop widths 768/1366/1440 still to run).
- M5 sample: FIXED 2026-11-27 (re-test pending on Preview). All 9 images now come from Wikimedia Commons, each used exactly once, with licences verified via the Commons API on 2026-11-27: Sedan front/rear CC0 (Tokumeigakarinoaoshima), Blue fr/rr CC BY-SA 3.0 (Matti Blume / MB-one), 2014 Auto CC BY-SA 4.0 (Calreyn88), 30 Jahre front/rear CC0 (Tokumeigakarinoaoshima), 2014 CC BY 2.0 (Kieran White), 2013 CC BY-SA 4.0 (DestinationFearFan). Removed: bmwcoop / cstatic / ibsrv / encontracarros images and the false "all photographs licensed CC0" claim; gallery intro and legal line now carry per-photo credits. Alt texts corrected (rear is rear, no "on a circuit" claims). Main-photo URL updated to the authoritative `b/bd` path (the old `8/8a` path was stale). Spare verified image (unused): Black BMW M5 (F10) rr Ottawa, CC BY-SA 3.0 (MB-one).
- Precision Auto Care: FIXED 2026-11-27 (re-test pending on Preview). Mobile hamburger menu added (toggle + `aria-expanded` + Escape close + close on link click), same pattern as the main site. Form given the same honesty fix as the main site: the prepared request is always shown in a visible box with a "Copy request" button; copy is claimed only on real Clipboard API success.
- Production: unchanged; no Production deployment authorized. Work is on `feature/mirah-immersive-studio-v1` only.

## Professional rework pass — 2026-11-27 (stack: static, confirmed by Sam 06:38)

- Re-test 06:36–06:39 on Preview dpl_361DtxTaSjhA6Hd2szLFrJa1S4hq: **M5 PASS** — all 9 images load, 3 thumbnails are three different photos, photo credits shown in full. **Precision form PASS** — request shown in a visible box with Copy button, status honest. **Precision mobile menu DEFECT** — no hamburger at the test viewport; the header showed desktop links and overflowed, cutting off GET AN ESTIMATE. Root cause: Precision collapsed its nav only at ≤620px while the test viewport was wider; the main site already collapses at 900px. Same latent defect existed on the main site (651–900px: 5 links + CTA overflow) and on M5 (links simply vanished ≤620px, no menu at all).
- Fixes applied (same commit): navigation collapses to a hamburger at **≤900px on all three pages**; hamburger + mobile nav added to M5; Precision header CTA hides ≤620px (the mobile menu carries the Enquire link); skip link added to Precision (main site and M5 already had one); Precision service icons marked `aria-hidden`; `touch-action:manipulation` on buttons on all pages; footer year falls back to 2026 without JS; `aria-controls` on all 8 main-site tab buttons plus Arrow/Home/End keyboard navigation for both tab groups.
- Open: the Precision submit button did not respond to two synthetic mouse clicks in the probe (first "refused as covered", second unknown); the form submitted fine via Enter, so the handler works — re-test with a real finger tap before calling it a defect. Known gaps: no `og:image` (no owned brand image exists — do not fabricate one from stock); desktop widths 768/1366/1440 still untested (SSO wall blocks the cloud browser).

- **ROOT CAUSE FOUND 06:49 (Precision menu):** a literal `\n` (backslash + `n`, two characters) sat in the Precision stylesheet between the reduced-motion block and the 900px block. In CSS, `\n` outside a string is an escape that produces the identifier `n`, so the parser swallowed the entire 900px media block as the body of a bogus rule — the 900px rules never applied, while the 620px block after it parsed normally. The same stray sequence predated the rework and had silently killed the original 620px block too. Fix: removed the two stray characters. Verified after the fix: no stray backslash-n remains in any stylesheet (the only ones left are legitimate JS `'\n'` string escapes), all @media blocks start at brace-depth 0, braces balanced 96/96. Lesson recorded: static QA now includes a stray-backslash check on every stylesheet.

- **Re-test PASSED 06:52** on Preview dpl_FCi7c48PMNTB5ceRrCsSAekqt4FU (https://mirah-digital-p4my7ctdp-samalshishani084.vercel.app): hamburger visible, desktop links hidden, menu opens with all 4 items, tapping Services closes it and jumps to #services showing all 6 services. **Mobile QA is now complete at phone width** — main site, M5, and Precision all PASS.

Next: desktop QA at 768 / 1366 / 1440 (blocked — SSO Deployment Protection keeps the cloud browser out; needs the protection off or a signed-in desktop browser).


Review date: 2026-11-27
Scope: Static source inspection of the main website and two automotive demonstration pages on `feature/mirah-immersive-studio-v1`.
Method: Source-level checks only. No real browser/device session was performed.

## Main website — `index.html`

Static checks:
- DOCTYPE, English document language, and viewport metadata: PASS.
- Page title and meta description: PRESENT.
- Image alt attributes: 2 images inspected; no missing alt attributes.
- Duplicate HTML IDs: none found.
- In-page anchor targets: no missing targets found.
- Contact/project brief form: present; source copy explains that it prepares a local brief and does not submit it to MIRAH.
- Reduced-motion CSS: present.
- No testimonials were found in the inspected source search.
- Industry concept panels include a visible note that they are illustrative directions, not completed client work or performance claims.
- Portfolio section states that the samples are demonstration concepts, not real customer businesses or official manufacturer partnerships.

Items requiring visual/functional verification:
- Five script blocks are present. Interactive navigation, industry selector, form behavior, and any concept assistant interaction need browser testing.
- Mobile and desktop layout, keyboard-only operation, screen-reader output, image loading, and performance metrics have not been tested in a real browser.
- Verify that all service descriptions and any AI-related concept UI are clearly understood as proposed capabilities, not existing live integrations.

## Automotive sample — M5 F10

Static checks:
- DOCTYPE, language, viewport, title, alt attributes, reduced-motion support, and in-page anchor targets: PASS.
- Nine image elements are present; all have alt text.
- No duplicate IDs or missing in-page anchor targets found.

Known blocking content issue:
- The gallery/source markup still contains repeated images and mixed legacy image sources. It is not a coherent, fully verified M5 F10 photo set.
- The visible M5 emblem is a typographic interpretation, not an official BMW M logo.
- Image identity and rights have not been visually re-verified in the published page.
- This page is NOT portfolio-ready and must remain a demonstration in Preview only.

## Automotive sample — Precision Auto Care

Static checks:
- DOCTYPE, language, viewport, title, alt attributes, and in-page anchor targets: PASS.
- A contact/booking form and one script block are present.
- Reduced-motion support was not found in the source and should be added.
- No real submission or booking service should be implied unless a backend integration is implemented and tested.

## Release decision

- Main website: static source review only; not yet approved for release based on this review.
- M5 sample: NOT READY — image consistency and visual direction are unresolved.
- Precision Auto Care: PARTIAL — reduced-motion support and browser-based form/interaction testing remain.
- Production: unchanged; no Production deployment authorized.

## Next actions (priority order)

1. Run browser-based desktop and mobile review of the main site, including navigation and form behavior.
2. Correct any visible layout/contrast/interaction defects found.
3. Add reduced-motion support to Precision Auto Care and verify its form clearly communicates its actual behavior.
4. Rebuild the M5 image set using a verified, rights-cleared set of distinct F10 M5 angles before any portfolio approval.
5. Record actual test device, viewport, date, and results before marking any manual test as passed.
