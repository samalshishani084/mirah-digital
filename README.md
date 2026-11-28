# MIRAH Digital — organized static site

## Structure
- `index.html` — main MIRAH website and portfolio entry point.
- `samples/automotive/m5-unleashed/index.html` — luxury personal-car concept.
- `samples/automotive/precision-auto-care/index.html` — repair and maintenance concept.

## Deployment
The project remains a simple static HTML site. Vercel serves the root `index.html` and nested sample pages directly. No build step or framework is required.


## MIRAH positioning and prototype boundaries
- MIRAH is positioned as an independent digital studio serving businesses across the United States.
- The website is a marketing prototype; portfolio entries are explicitly labeled fictional demonstration concepts.
- The contact form prepares a project brief in the visitor's browser. It does not submit enquiries to a server or create a lead in a CRM.
- The website does not currently provide a live AI service, booking system, payment flow, or authenticated client dashboard.
- Do not publish privacy, security, performance, client, or service-delivery claims until they have been verified and approved.
- Production deployment requires a separate explicit approval. Work on the feature branch does not authorize a production release.

## Internal delivery standard
- The mandatory project workflow, approval gates, asset integrity rules, visual quality criteria, QA evidence requirements, and definition of done are documented in [MIRAH Delivery Standard](docs/MIRAH_DELIVERY_STANDARD.md).

## Notes
- Sample businesses are fictional demonstrations.
- Forms only prepare/copy request text locally; they do not transmit or store customer information.
- Replace remote demo photography with licensed or client-owned images before commercial deployment.
- M5 Unleashed is an independent concept and is not affiliated with BMW.

## Foundation v1 — main-site rebuild (2026-11-27)
- Rebuilt `index.html` as a clean foundation: one stylesheet, one script, 575 lines / 48 KB. Removed 7+ layered CSS overrides, conflicting reveal/blur rules, and all dead AI-hero / device-mockup / particles / cursor-glow code for elements that did not exist in the HTML.
- Content is visible without JavaScript; the reveal effect can never hide or blur a section. Ticker, spacing, and mobile navigation fixed at the source level. No black floating controls exist in the site source — the small black floating button on the Preview is Vercel's preview Toolbar (preview-only, absent on Production).
- Brand, copy, services, tabs, portfolio links, process, and the local-only contact brief are preserved. M5 and Precision Auto Care samples were fixed in a later pass (see QA report): M5 images are now verified Wikimedia Commons photographs with per-photo credits; Precision has a mobile menu and the same honest brief-form fix as the main site.

## Phase 03 — M5 implementation and static QA (2026-11-27)
- Rebuilt the M5 sample as an independent 2014 BMW M5 F10 concept page.
- Added keyboard skip navigation, visible keyboard focus, a named main landmark, responsive mobile section navigation, a caption for the technical table, and social-sharing metadata.
- Static source checks passed: document structure, language and viewport metadata, page title and description, skip link and main landmark, mobile navigation, all section anchor targets, no broken in-page anchor targets, image alt text on all five gallery images, reduced-motion support, technical-table caption, BMW independence disclaimer, and illustrative-image disclaimer.
- Vercel Preview build completed successfully for commit `1dfd1f5be62fc58b9e433b826f619781694a7a0d`.
- CI status: Vercel success. No separate automated test suite is configured for this static HTML project.
- Manual visual testing across real mobile/desktop browsers, screen-reader testing, Core Web Vitals measurement, and live remote-image availability checks have not been performed in this environment; do not represent them as passed.
- Gallery and hero photography: UPDATED 2026-11-27 — all 9 images are now verified Wikimedia Commons photographs of BMW M5 F10 models, each used once, with licences verified via the Commons API and per-photo credits in the page footer (CC0, CC BY 2.0, CC BY-SA 3.0 / 4.0). The earlier mixed stock sources (bmwcoop / cstatic / ibsrv / encontracarros) were removed.
- The sample remains a concept, not an official BMW property. No Production deployment was made.

## Phase 04 — Racing Machine Service concept (2026-11-27)
- Added `samples/automotive/racing-machine-service/index.html` as an unofficial, independent concept redesign.
- Positioning focuses on engine machining and rebuilding; public directory evidence supports the engine-rebuilding category, while individual service capabilities are explicitly marked for owner confirmation.
- Includes responsive navigation, service-capability cards, a suggested customer journey, click-to-call, map link, and a local-only enquiry text generator (no network submission or storage).
- Third-party industry photographs are labeled illustrative and not representative of Racing Machine Service premises, staff, or work. Replace with licensed, owner-approved assets before commercial use.
- No client relationship, endorsement, approval, or production deployment is implied.
