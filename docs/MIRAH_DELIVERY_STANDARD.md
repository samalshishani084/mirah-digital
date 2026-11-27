# MIRAH Delivery Standard

Status: Internal operating standard — v1.0
Applies to: MIRAH website projects, portfolio demonstrations, and client work.
Purpose: Make design quality, implementation accuracy, and delivery evidence repeatable.

## 1. Non-negotiable principles

1. No development begins before the creative direction and required screen designs are approved.
2. Every project has its own visual identity. Shared components and engineering conventions are reusable; sector-specific art direction is not copied blindly.
3. Never use unrelated, misleading, unverified, or unlicensed imagery as if it depicts the client's product, premises, staff, or work.
4. Never invent client names, testimonials, ratings, results, certifications, prices, inventory, warranties, or performance claims.
5. A successful build or deployment is not proof of visual quality or functional correctness.
6. Production deployment, paid services, scope changes with cost, and external commitments require explicit client authorization.
7. Report status truthfully: DONE, PARTIAL, NOT DONE, or NOT TESTED. Do not mark an untested item as passed.

## 2. Project workflow and approval gates

### Gate 0 — Qualification and discovery
Deliverables:
- Project brief: business, audience, goals, primary conversion, services/products, geography, competitors, constraints.
- Stakeholder and approval owner.
- Required integrations, data handling, accessibility, legal/compliance constraints.
Exit condition: client confirms the brief and priorities.

### Gate 1 — Research and creative direction
Deliverables:
- Competitor/reference review with links and observations.
- Audience and user-journey summary.
- Creative direction: visual concept, tone, typography direction, color direction, imagery approach, motion principles.
- Content and asset inventory, including ownership/licensing status.
Exit condition: client approves the direction before high-fidelity design.

### Gate 2 — UX structure and visual design
Deliverables:
- Sitemap and page list.
- Key user flows and low-fidelity wireframes.
- Responsive high-fidelity designs for agreed breakpoints (at minimum mobile and desktop).
- Component/state inventory: navigation, buttons, forms, cards, menus, loading, empty, success, error.
- Design decision log and open questions.
Exit condition: written approval of the agreed screens and responsive behavior. Any later change is recorded as a change request.

### Gate 3 — Scope and implementation plan
Deliverables:
- Scope of Work: included pages/features, exclusions, dependencies, milestones, acceptance criteria.
- Asset manifest: source, exact subject/model/version, license/permission, attribution, crop/use notes.
- Technical plan and privacy/data-flow notes for every form or integration.
Exit condition: scope and implementation plan approved.

### Gate 4 — Development
Rules:
- Implement against the approved design, not an improvised replacement.
- Reuse accessible components and design tokens where appropriate.
- Keep the project structure maintainable; do not create duplicate projects or unnecessary dependencies.
- Forms must have an explicitly documented behavior. A visual prototype must never imply that data was submitted or stored.
- Use real client-owned/licensed assets or clearly labeled placeholders. Placeholders must not be presented as real evidence.
Exit condition: agreed functionality implemented in Preview.

### Gate 5 — Quality assurance
Run and record:
- Visual comparison against approved design at agreed viewport sizes.
- Responsive checks: small mobile, large mobile, tablet, desktop.
- Functional checks: navigation, anchors, buttons, forms, validation, success/error states, external links.
- Asset checks: all images load; subject/model is correct; no accidental duplicates; crop and resolution are appropriate; rights/attribution are documented.
- Accessibility checks: keyboard-only navigation, focus visibility, semantic landmarks/headings, labels, alt text, contrast, reduced motion.
- Performance checks: image weight and formats, layout shift, loading behavior, Core Web Vitals where measurement is available.
- SEO checks: unique title/description, heading structure, canonical/indexing settings as applicable, social metadata.
- Browser/device checks on actual target environments when available.
Evidence rule: record tool/device, date, viewport, result, and defects. If a test environment is unavailable, mark NOT TESTED and disclose it.
Exit condition: no critical/high-severity defects; accepted medium/low defects documented; client acceptance criteria met.

### Gate 6 — Client acceptance and launch
Deliverables:
- Preview URL and release notes.
- QA report with passed/failed/not-tested distinctions.
- Known limitations and outstanding risks.
- Client written acceptance.
- Backup/rollback plan and launch checklist.
Production release requires explicit approval. Preview readiness alone never authorizes Production.

### Gate 7 — Handover and care
Deliverables:
- Access/ownership handover as agreed.
- Content and asset source register.
- Maintenance scope, response expectations, and exclusions.
- Delivery checklist and maintenance record.
- Confirmation of backups, analytics, forms, and integrations only where actually configured and tested.

## 3. Visual quality standard

Every project must demonstrate:
- A clear visual hierarchy and a deliberate art direction.
- Consistent typography, spacing, grid, color, radius, borders, and image treatment.
- Images that are relevant, high quality, compositionally consistent, and legally usable.
- Clear primary action and an understandable user journey.
- Responsive layouts designed intentionally, not merely squeezed down.
- Motion that supports hierarchy and feedback, with reduced-motion support.
- Readable contrast, restrained effects, and no decorative clutter that competes with the task.

Industry direction examples (not rigid templates):
- Automotive: cinematic photography, strong vehicle identity, performance/editorial storytelling, credible specs, clear enquiry path.
- Professional services: trust, clarity, credentials only when verified, clear service scope and contact.
- E-commerce: product accuracy, strong product imagery, transparent pricing/shipping/returns, low-friction purchase flow.
- Technology/SaaS: product clarity, interface evidence, workflow explanation, trustworthy feature claims, clear conversion path.

## 4. Asset and content integrity

Maintain an asset manifest for every externally sourced or client-supplied asset:
- Filename or URL
- Creator/source
- Exact subject/model/version shown
- License or written permission and attribution requirements
- Intended placements
- Verification date and reviewer

If image identity or license cannot be verified, do not present it as authentic or commercially cleared. Use an explicit placeholder or omit it pending approval.

All numerical claims and product specifications must have a reliable source and an appropriate qualifier. Demonstration concepts must be labeled as concepts.

## 5. Definition of done

A project is NOT complete merely because:
- Code was written.
- A Preview deployment is READY.
- A page looks plausible in source code.
- A checklist was drafted.

A project can be marked complete only when:
- Approved design and scope are implemented.
- All required acceptance criteria are tested.
- Critical and high defects are resolved.
- Remaining limitations are documented and accepted.
- QA evidence is recorded.
- Client approval is received.
- Launch authorization is separately received where Production is involved.

## 6. Required project records

Use the existing project workspace and keep records proportionate:
- Project Brief
- Scope of Work
- Design Direction / Design Decisions
- Asset Manifest
- Development Notes
- QA Report
- Client Approval
- Delivery Checklist
- Maintenance Record

Do not create duplicate repositories or parallel project structures for routine documentation.

## 7. Status language

- DONE: completed and evidence is available.
- PARTIAL: some work is complete; remaining items are named.
- NOT DONE: work has not been completed.
- NOT TESTED: no reliable test was performed.
- BLOCKED: work cannot continue until a named dependency or approval is received.

Every status update should state: what changed, evidence/link, what remains, blockers, and whether Production was affected.

## 8. Applying the standard to the current M5 sample

The current M5 page is a portfolio demonstration, not a real vehicle listing. It must not be labeled client-ready until:
- One verified art direction is approved.
- Every visible vehicle image is confirmed to show the intended F10 M5 model/body and coherent angles.
- Image rights and attribution are recorded.
- Desktop and mobile visual review is performed.
- Gallery, navigation, links, and enquiry behavior are tested.
- A truthful QA report is added.

Current known status at adoption: implementation is in progress; visual and device QA are not complete; Production has not been authorized.
