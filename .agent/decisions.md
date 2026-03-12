# Decision Records

## DR-001: CMS Selection — Payload CMS
**Date:** 2026-03-12
**Context:** The site needs a CMS that both the agent and operator can use to manage content, supports 5 languages, and is self-hosted (no SaaS costs).
**Options considered:**
- **Payload CMS:** Self-hosted, TypeScript-native, excellent Next.js integration, first-class i18n support for content fields, admin UI the operator can use without touching code. Open source. Requires PostgreSQL.
- **Sanity:** Hosted SaaS (cost), excellent i18n, good DX. Monthly fee adds up. Less control over data.
- **Contentful:** SaaS, expensive at scale, good i18n. Overkill for this project size.
- **Directus:** Good alternative to Payload, less tightly coupled to Next.js.
- **Markdown/MDX files:** No operator-editable CMS, no i18n content management. Rules out non-technical operator edits.
**Decision:** Payload CMS. Best combination of operator usability, i18n support, Next.js integration, and zero ongoing SaaS cost. Aligns with project CLAUDE.md default stack.
**Consequences:** Requires PostgreSQL database (provisioned via Coolify). Agent manages schema migrations. Operator accesses /admin UI for content edits.

## DR-002: i18n Architecture — next-intl + Payload CMS
**Date:** 2026-03-12
**Context:** 5 languages (EN, DE, SV, DA, NL) required. Need both routing (URL structure) and content translation (CMS fields).
**Options considered:**
- **next-intl for routing + Payload i18n for content:** next-intl handles locale routing (/de/, /sv/ etc.), Payload stores localised content fields. Industry-standard combination for Next.js + Payload.
- **next-i18next:** Older library, less ergonomic with App Router.
- **Single-language site with language switcher injecting translations:** Simpler but poor for SEO (no separate URLs per language, no hreflang).
**Decision:** next-intl + Payload CMS i18n fields. Gives clean per-language URLs (good for SEO), operator can manage translations in Payload admin, agent can handle initial translations via Claude API.
**Consequences:** Locale routing prefix on all URLs. Must maintain translation files for UI strings alongside Payload content.

## DR-003: Accommodation Monetisation — Airbnb Link-Outs (initial)
**Date:** 2026-03-12
**Context:** The properties currently use Airbnb for bookings. Decide whether to implement direct booking on waldenbad.se or link out to Airbnb.
**Options considered:**
- **Airbnb link-outs:** Simple, no payment processing, no availability management needed. Airbnb handles all booking complexity. Operator pays Airbnb commission but this is already the case.
- **Direct booking (e.g. Smoobu, Lodgify, or custom):** Eliminates Airbnb commission on direct bookings. Requires availability management, payment processing, calendar sync. Significant complexity.
**Decision:** Airbnb link-outs for launch. Direct booking to be re-evaluated in Phase 7 once traffic data justifies the complexity investment.
**Consequences:** Waldenbad.se functions as a discovery/editorial layer above the existing Airbnb listings. Conversion tracking limited to click-through to Airbnb.
