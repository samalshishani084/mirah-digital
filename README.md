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

## Phase 03 — M5 implementation and static QA (2026-11-27)
- Rebuilt the M5 sample as an independent 2014 BMW M5 F10 concept page.
- Added keyboard skip navigation, visible keyboard focus, a named main landmark, responsive mobile section navigation, a caption for the technical table, and social-sharing metadata.
- Static source checks passed: document structure, language and viewport metadata, page title and description, skip link and main landmark, mobile navigation, all section anchor targets, no broken in-page anchor targets, image alt text on all five gallery images, reduced-motion support, technical-table caption, BMW independence disclaimer, and illustrative-image disclaimer.
- Vercel Preview build completed successfully for commit `1dfd1f5be62fc58b9e433b826f619781694a7a0d`.
- CI status: Vercel success. No separate automated test suite is configured for this static HTML project.
- Manual visual testing across real mobile/desktop browsers, screen-reader testing, Core Web Vitals measurement, and live remote-image availability checks have not been performed in this environment; do not represent them as passed.
- Gallery and hero photography remain illustrative stock images and are not verified photographs of a 2014 BMW M5 F10. Replace with model-verified, appropriately licensed images before presenting the sample as an accurate vehicle gallery or commercial vehicle listing.
- The sample remains a concept, not an official BMW property. No Production deployment was made.
