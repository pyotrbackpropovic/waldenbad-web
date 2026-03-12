# Assignments

## Priority Levels

- **P0** — Drop everything. Broken deployment, data loss, security issue.
- **P1** — Core functionality. Do these first.
- **P2** — Important but not blocking other work. Do after P1s.
- **P3** — Nice to have. Do when the queue is otherwise empty.

---

## Queued

### [P1] Provision Coolify services and set up local development environment
Added: 2026-03-12
Context: Phase 2 start. Need a Coolify project for waldenbad-web with a Next.js app service and a PostgreSQL database. Local dev environment (Node.js via nvm, Payload CMS) must also be running before any build work starts.
Acceptance:
- Coolify project "waldenbad-web" exists with a Next.js app service and PostgreSQL service
- `npm run dev` works locally and Payload CMS admin is accessible at localhost:3000/admin
- Environment variables documented in docs/architecture.md
- DATABASE_URL and PAYLOAD_SECRET stored in Coolify env vars

### [P1] Scaffold Next.js + Payload CMS project with i18n foundation
Added: 2026-03-12
Context: Create the actual Next.js 15 (App Router) project with Payload CMS integrated, next-intl configured for 5 locales (en, de, sv, da, nl), and the design system baseline (Tailwind CSS + shadcn/ui). This is the technical foundation all subsequent phases build on.
Acceptance:
- `npm run dev` starts successfully; Payload admin accessible
- next-intl routing works: /en/, /de/, /sv/, /da/, /nl/ all respond
- Tailwind and shadcn/ui installed and a sample Button component renders
- Basic Payload collections defined: Article, Listing, Location (all with i18n locale fields)
- Initial git history clean, pushed to main

### [P1] Design system and component library
Added: 2026-03-12
Context: Define and implement the visual identity before building pages. The site should feel like a high-quality editorial product — think Kinfolk magazine or Canopy & Stars: clean, nature-inspired, professional. Not wellness-kitsch. Use operator-supplied photos as the primary visual asset.
Acceptance:
- Colour palette, typography, and spacing scale defined and documented
- Core components built: Header, Footer, Button, Card (article card, listing card), Hero, RichText renderer
- Storybook or a /design-system demo page showing all components
- Playwright screenshot reviewed by agent confirms visual quality

### [P1] Homepage
Added: 2026-03-12
Context: The homepage introduces the concept, establishes the brand, and routes visitors to editorial content and accommodation listings. English content only at this stage (i18n in Phase 4).
Acceptance:
- Hero section with forest imagery, headline, and subheadline
- "What is forest bathing?" intro section with link to full article
- "Where to stay" section featuring both properties as cards with photos and link to listing pages
- "Good places in Sweden" teaser section with link to the directory
- Footer with language switcher (non-functional placeholder until Phase 4)
- Responsive (mobile + desktop), accessible, Core Web Vitals green

### [P1] Core editorial content — English
Added: 2026-03-12
Context: The editorial content is what gives the site SEO authority and credibility. Need at minimum: (1) What is forest bathing? (2) Forest bathing in Sweden. (3) Forest bathing in Blekinge. All content should be down-to-earth, evidence-based, no mysticism. Cite actual research findings honestly.
Content to write:
- "What is forest bathing?" — origins (Shinrin-yoku 1982), science (cortisol, blood pressure, mood — what's proven, what's not), how to do it practically
- "Forest bathing in Sweden" — friluftsliv and allemansrätten framing, why Sweden is ideal, practical guidance
- "Forest bathing in Blekinge" — the region's forest character, what makes it suitable
Acceptance:
- All three articles written, edited, published in Payload CMS
- Articles live at /en/[slug] on the site
- Each article 800–1500 words, well-structured with headings
- Internal linking between articles and to listing pages

### [P1] Accommodation listing pages — Kringelgården and Drängstugan
Added: 2026-03-12
Context: Property pages for both houses. These are the commercial anchor pages. Should be beautiful, trust-building, and clearly guide visitors to book on Airbnb.
Content sources: Airbnb listing descriptions (already researched), operator-supplied photos.
Acceptance:
- Kringelgården page: full description, capacity (8 guests, 3 beds, 1 bath), amenities, lake/forest highlights, photo gallery, "Book on Airbnb" CTA linking to airbnb.com/h/kringelgarden
- Drängstugan page: same treatment, capacity (6 guests, 2 beds, 1 bath), pets welcome note, 5.0 rating, link to airbnb.com/h/drangstuga
- Combined booking option mentioned on both pages with link to airbnb.com/h/kringelgarden-all
- Operator needs to provide photos — agent will request via blocker if not available before this assignment starts

### [P1] "Good places for forest bathing in Sweden" directory — initial
Added: 2026-03-12
Context: The directory is a key editorial asset that gives the site authority beyond just the operator's properties. Initial version should list 5–10 places (Blekinge featured prominently plus well-known locations nationally). Not a booking engine — pure editorial with links to external resources where relevant.
Acceptance:
- Directory page at /en/good-places lists at least 6 locations
- Each entry: location name, region, 2–3 sentence description, what makes it good for forest bathing
- Blekinge / the operator's farm area featured as the anchor entry with most detail
- Other entries include nationally known locations (e.g. Tyresta, Söderåsen, Ekopark Omberg)
- Filterable by region (basic, not complex)

### [P1] Deploy to Coolify staging and smoke test
Added: 2026-03-12
Context: First deployment to verify the full stack works on production infrastructure before Phase 4 begins.
Acceptance:
- App deployed to Coolify and accessible at a staging URL (e.g. waldenbad.staging.yourdomain.com or the Coolify-assigned URL)
- Playwright smoke test passes: homepage loads, article loads, listing page loads, Airbnb links present
- Payload CMS admin accessible at /admin on staging
- No build errors in Coolify logs

### [P2] Multilingual content — all 5 languages
Added: 2026-03-12
Context: Phase 4. Translate all editorial content and UI strings into DE, SV, DA, NL. Agent drafts translations using Claude API. Operator reviews DE and SV before publishing.
Languages: English (source), German, Swedish, Danish, Dutch
Content to translate: all articles, property descriptions, homepage copy, UI strings, meta tags
Acceptance:
- All pages accessible in all 5 languages with clean URLs (/de/, /sv/, /da/, /nl/)
- Language switcher functional
- hreflang tags in HTML head
- Operator has reviewed and approved German and Swedish translations

### [P2] SEO optimisation
Added: 2026-03-12
Context: Phase 5. On-page SEO targeting the identified low-competition keywords per language. Structured data for accommodation listings. Technical SEO hygiene.
Key target keywords: "forest bathing Sweden" (EN), "Waldbaden Schweden" (DE), "skogsbad Sverige" (SV), "forest bathing accommodation Sweden" (EN), "Waldbaden Urlaub Schweden" (DE)
Acceptance:
- Meta title and description optimised per page per language
- schema.org LodgingBusiness markup on listing pages
- schema.org Article markup on editorial pages
- XML sitemap at /sitemap.xml covering all locales
- robots.txt correct
- Core Web Vitals: LCP < 2.5s, CLS < 0.1, FID < 100ms on key pages

### [P2] Production launch
Added: 2026-03-12
Context: Phase 5. Final pre-launch verification and go-live. Operator performs DNS cutover.
Acceptance:
- Full Playwright regression test of staging passes in all 5 languages
- Agent sends ntfy notification with staging URL for operator review
- Operator approves
- Coolify production environment configured for waldenbad.se
- Post DNS cutover: Playwright verifies site is live at waldenbad.se
- Google Search Console property created and sitemap submitted

### [P2] Post-launch blog article: "Why Blekinge's forest is different"
Added: 2026-03-12
Context: Phase 6. First post-launch content piece. Positions Blekinge specifically as a forest bathing destination. Good for SEO, shareable in German forest bathing communities.
Acceptance:
- 1000–1500 word article in English and German published on the site
- Article focuses on Blekinge's distinctive mixed deciduous/coastal forest vs northern boreal pine forests
- References the specific character of the family-managed forest at Kringelgården/Drängstugan
- Internally links to both property pages and the Good Places directory

### [P2] Analytics and monitoring setup
Added: 2026-03-12
Context: Phase 6. Need to understand traffic before making Phase 7 decisions.
Acceptance:
- Privacy-respecting analytics installed (Plausible or similar — no Google Analytics cookies)
- Dashboard shows: page views per page, traffic by language, click-throughs to Airbnb
- Google Search Console connected, sitemap submitted, initial index coverage checked 2 weeks post-launch

### [P3] Visit Blekinge and Visit Sweden outreach preparation
Added: 2026-03-12
Context: Phase 6. Prepare outreach materials for regional and national tourism authorities. Agent drafts; operator approves before sending.
Acceptance:
- Draft email to Visit Blekinge prepared: introduction to waldenbad.se, request for inclusion in their content and co-marketing programs
- Draft email to Visit Sweden Germany market program prepared
- Agent flags to operator via ntfy for review before any emails are sent

### [P3] German travel blogger outreach list
Added: 2026-03-12
Context: Phase 6. Identify 5–10 German-language Scandinavia/nature travel bloggers to approach for potential coverage.
Acceptance:
- List of 5–10 bloggers with: name/blog URL, Instagram/follower count, recent Sweden or forest content, contact details
- Agent drafts a template pitch email for operator review
- No outreach happens without operator approval

### [P3] Expand "Good places" directory — 10 additional locations
Added: 2026-03-12
Context: Phase 7. Grow the directory to increase topical authority and give the site more SEO surface area.
Acceptance:
- 10 additional Swedish forest bathing locations researched and published
- Mix of regions: Dalarna, Lapland, Värmland, High Coast, Gotland
- Each entry consistent with existing format

### [P3] Evaluate direct booking
Added: 2026-03-12
Context: Phase 7. Once traffic and Airbnb click-through data is available (at least 3 months post-launch), assess whether direct booking implementation would have meaningful ROI.
Acceptance:
- Agent produces a simple analysis: estimated bookings per month from direct traffic, Airbnb commission cost, implementation cost estimate
- Operator makes go/no-go decision
- If go: separate assignment created for direct booking implementation

---

## In Progress

<!-- No active assignment. Agent picks next from Queued. -->

---

## Done

### [P0] Research and masterplan
Added: 2026-03-12
Started: 2026-03-12
Completed: 2026-03-12
Outcome: Research complete. Masterplan written with 7 phases, full assignment queue populated, 3 decision records written. Site positioned as authoritative editorial hub for forest bathing travel in Sweden targeting DE/NL/SV/DA/EN markets.
