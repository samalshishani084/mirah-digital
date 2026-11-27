# MIRAH Digital — Strategy & Design System (Phases 1–2)

Date: 2026-11-27 · Status: Foundation v1 approved as the base; this document is the operating brief for everything built on it.
Stack (locked by the Master Blueprint): static HTML, CSS, JavaScript — no framework, no build step. Vercel serves the files as-is; GitHub pushes auto-deploy Previews.

## Phase 1 — Strategy & Analysis

### Who we serve
US small-to-medium businesses, startups, and entrepreneurs who need a website that earns trust, turns visits into enquiries, and is ready for the AI era. They are not buying code — they are buying a clearer business presence.

### User journey (business owner)
1. **Arrive** — a Google search, referral, or social link lands on Home. In 5 seconds they must know: what MIRAH does, who it is for, and what to do next.
2. **Believe** — the hero, the design-system showcase ("the foundation"), and honest concept work prove craft without invented clients or results.
3. **Explore** — Services answers "what do you do for me?"; Industries answers "do you understand my world?"; Portfolio shows what the work looks like.
4. **Decide** — the 4-step process (Discover / Plan / Create / Improve) removes uncertainty about how working together feels.
5. **Act** — the project-brief form turns their need into words in under a minute, locally in their browser, with an honest "not sent" status. No pressure, no fake chat, no invented availability.

### Sitemap
- `/` Home — hero, foundation showcase, capabilities tabs, six services, industries, process, portfolio (2 concept samples), project-brief contact, footer.
- `/#services` Services (section; dedicated page only when the service detail grows beyond one screen).
- `/#portfolio` Portfolio — M5 Unleashed (automotive showcase concept) and Precision Auto Care (service-center concept), both labelled as concepts.
- `/#process` About / how we work — the 4-step process and the studio's honest positioning (independent studio, not a large agency).
- `/#contact` Contact — project-brief form (local-only prototype until a real intake is wired up).
- Future only (never advertised as live): AI Receptionist, client dashboard, workflow automation products.

### Honesty rules (non-negotiable)
- Never fabricate customers, testimonials, reviews, metrics, prices, or availability.
- Concept work is labelled as concept work. Photography is credited with its real photographer and licence.
- Forms never claim submission. Copy is claimed only when the Clipboard API really succeeded; the text is always shown so it can be copied manually.
- No fake chatbot. No floating widget that pretends a human or an AI is waiting. A floating button may only do something real (e.g. scroll to Contact) and say so.

## Phase 2 — UI Design & Design System

### Tokens (exact)
| Token | Value |
|---|---|
| Ink (text) | `#10162D` |
| Background | `#F7F8FC` |
| Blue | `#258EEA` |
| Violet | `#7046ED` |
| Magenta | `#DF39A7` |
| Orange | `#FF8A32` |
| Mint | `#49B99A` |
| Gradient | `linear-gradient(112deg, #258EEA 0%, #7046ED 43%, #DF39A7 76%, #FF8A32 100%)` |
| Headings | Manrope (Google Fonts) |
| Body | DM Sans (Google Fonts) |
| Content width | ~1160px |
| Card radius | 21–24px |
| Section rhythm | 64px desktop / 48px mobile; hero 64/56px desktop, 40/44px mobile |

### Components and states
- **Buttons** — Primary: gradient background, white text, pill radius, soft violet shadow; hover lifts 2px with a deeper shadow; focus gets a visible 3px ring; disabled is greyed and non-clickable. Secondary: white background, ink text, 1px border. No button ever shows a loading spinner for an action that does nothing.
- **Form fields** — White background, 11px radius, 1px `#E3E6F0` border; focus border `#9B86F4` + 3px soft ring; required fields use native validation ("Please fill out this field."); error state is the native message plus a visible status line, never a silent failure.
- **Cards** — White / soft tint, 21–24px radius, soft shadow, numbered gradient accents (01 violet, 02 orange, 03 pink, 04 teal on the process cards).
- **Navbar** — Sticky, translucent with blur; mobile hamburger with `aria-expanded`, closes on Escape and on link click. Navigation collapses to the hamburger at ≤900px on every page (standardized 2026-11-27 — the 620/650px breakpoints let tablet-width headers overflow).
- **Ticker** — One duplicated track, `overflow:hidden`, pauses under `prefers-reduced-motion`.
- **Tabs / industry selector** — Button-based, keyboard-focusable, panels swap content; no tab may promise a capability that does not exist.
- **Footer** — Brand, service list, honest studio line, copyright.
- **Reveal animation** — Content is visible without JavaScript; JS only adds a one-time entrance. Nothing may hide content if JS fails.

### Wireframes (text)
**Home** — Top line (3px gradient) → sticky nav (logo, Services, Industries, Portfolio, Process, Contact CTA) → Hero (kicker, H1 "Make your next digital move count.", supporting copy, two CTAs, CSS concept visual) → Ticker strip → "The foundation" design-system showcase → Capabilities tabs (4) → Services grid (6 cards) → Industries selector (4 panels) → Process (4 numbered cards) → Portfolio (2 concept cards) → Contact (copy + brief form) → Footer.
**Contact (section)** — Left: heading "What should your website do better?", short copy, studio line. Right: brief form — name (required), business (required), need (select), details (textarea), submit "Create my project brief", status line, brief output box + "Copy brief" button, prototype note. On submit the brief is always shown; copy is attempted and reported honestly.

### Accessibility
Skip link, semantic landmarks (`header`/`main`/`footer`, labelled `nav`), `aria-expanded`/`aria-label` on toggles, `role="status"` + `aria-live="polite"` on form status, visible focus rings, `prefers-reduced-motion` respected, alt text that describes what the image actually shows.

### SEO
One H1 per page, descriptive title + meta description, Open Graph tags, semantic HTML, descriptive link text, fast static files (no framework JS to download).

### Performance
Static files only; system fonts via Google Fonts with `preconnect`; images lazy-loaded except the hero; no render-blocking scripts; content visible without JS.

## Stack decision — read before building further

The Master Blueprint locks the stack to static HTML/CSS/JS. A later instruction asked for Next.js (App Router) + React + TypeScript + Tailwind + Framer Motion. That is a real architecture change, not a cosmetic one: it adds a build step, `package.json`, framework settings in Vercel, and a full rewrite of Foundation v1 (which is approved, deployed, and QA-passed). It does not change what the visitor sees — the same design, copy, and honesty rules apply in either stack.

Recommendation: stay static until a feature actually needs a framework (server data, auth, CMS, or a real AI backend). If the decision is to migrate, it needs an explicit go-ahead, and the migration must preserve every QA-passed behaviour (visible-without-JS content, honest brief form, credited images, mobile menu).

## What is NOT built (deliberately)
- No chatbot / AI receptionist widget (future direction only).
- No fake testimonials, logos, metrics, or case-study results.
- No backend, analytics, or tracking until explicitly approved.
- No Production deployment without explicit approval.
