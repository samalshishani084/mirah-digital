# MIRAH Website — First-pass QA Review

## Foundation v1 — main-site rebuild (2026-11-27, Sam approved re-study)

What was done: `index.html` was rebuilt as a clean foundation (575 lines, 48 KB, one `<style>` block, one `<script>` block). No layered CSS overrides remain on the main page.

Diagnosis confirmed from source:
- Old file had 7+ layered CSS blocks with `!important` overrides, conflicting `.reveal` definitions (opacity 0 + blur 4px, later overridden to opacity 1), conflicting hero heights (740px, then 0), and ~300 lines of dead AI-hero / device-mockup / particles / cursor-glow CSS and JS for elements that do not exist in the HTML (`ai-stage`, `ai-console`, `aiChatForm`, `mirahCursorGlow`). All removed.
- No black floating controls exist in the site source. The only fixed element is the 3px gradient progress line (`.topline`); the header is sticky, not floating. The black controls in the Android screenshot are Android system / accessibility UI, not website elements — NOT DONE as a site fix because there is nothing in the source to remove.
- Ticker: old track duplicated content but sat inside conflicting overflow rules. Foundation ticker uses one duplicated track, `overflow:hidden`, `width:max-content`, and stops under reduced motion.
- Excess vertical space: old hero padding 86px + 100px, plus stacked section padding (90px) and strip padding. Foundation uses one rhythm: hero 64px/56px desktop, 40px/44px mobile; sections 64px desktop, 48px mobile.

Foundation v1 guarantees:
- Content is visible without JavaScript: `.reveal` has no hidden state in CSS; JS only adds a one-time entrance animation via `.in-view`. If JS or the observer fails, content stays visible.
- No duplicate IDs (checked 2026-11-27, all IDs unique). One script block; no references to missing elements.
- Mobile menu: toggle + Escape to close + close on link click + `aria-expanded`. Active nav link via IntersectionObserver.
- Contact form unchanged in behaviour: local brief only, clipboard with manual fallback, explicit "has not been sent" status.
- Brand, copy, six services, four experience tabs, four industry tabs, two portfolio cards, process, and footer preserved. Hero visual is now a truthful CSS-only concept preview, not a fake device or fake AI chat.

Status: main site — PARTIAL (source + static checks DONE; live browser/device visual QA still to run on the Preview deployment).
- M5 sample: NOT READY — unchanged in this pass. Confirmed duplicates: front image used twice (main photo + thumb 1), rear image used twice (thumb 2 + thumb 3, with mismatched alt text), gallery mixes Wikimedia / bmwcoop / cstatic / ibsrv / encontracarros sources. Needs a verified, rights-cleared F10 set before portfolio approval.
- Precision Auto Care: PARTIAL — unchanged in this pass. Single clean stylesheet and reduced-motion support are present; mobile nav links are hidden at ≤620px with no hamburger/menu alternative — needs a mobile menu before approval.
- Production: unchanged; no Production deployment authorized. Work is on `feature/mirah-immersive-studio-v1` only.

Next: run live Preview QA at 360 / 390 / 430 / 768 / 1366 / 1440, test nav, tabs, form, ticker, and record real screenshots before marking visual QA DONE.


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
