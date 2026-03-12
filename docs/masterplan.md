# Project Masterplan: waldenbad.se

## Vision

Waldenbad.se is the authoritative editorial destination for forest bathing travel in Sweden. It combines science-backed, down-to-earth content about the forest bathing concept with curated accommodation listings — starting with two exceptional properties in the forests of Blekinge, and expanding over time.

The site serves a clear gap: no site currently positions itself as the editorial home for this topic in Scandinavia. The keywords "forest bathing Sweden," "Waldbaden Schweden," and "skogsbad Sverige" are all low-competition and unowned. Waldenbad.se can claim this territory organically.

**Brand logic:** "Waldenbad" fuses Walden (Thoreau's nature-immersion classic, recognisable across all target languages) with *bad* (bath in Swedish and German — as in Shinrin-yoku, forest bath). The brand works in all five languages simultaneously.

**Tone:** Evidence-based and down-to-earth. Cite real research, be honest about what's proven versus preliminary. No mysticism, no new-age framing. The Swedish concepts of *friluftsliv* (outdoor life) and *allemansrätten* (right to roam) provide a natural, grounded cultural frame.

**Target audiences (priority order):**
1. German-speaking tourists (Germany, Austria, Switzerland) — largest market, strongest Waldbaden cultural fit
2. Dutch tourists — second largest Sweden market, similar profile to Germans
3. Swedish domestic — essential baseline
4. Danish — proximity-driven, short breaks
5. English-speaking — international catchall

**Languages:** English, German (Deutsch), Swedish (Svenska), Danish (Dansk), Dutch (Nederlands)

---

## Properties

### Kringelgården
Historic farmhouse (c.1790, renovated), Stamsmåla, Blekinge. Sleeps up to 8 (3 bedrooms, 7 beds). Lake Bredasjön 200m away, rowing boat included. Library with lake view, fireplace, wood-fired stove. Airbnb: airbnb.com/h/kringelgarden

### Drängstugan
Secluded forest cottage, Stamsmåla, Blekinge. Sleeps up to 6 (2 bedrooms, 4 beds). Same forest and lake setting. Fireplace, pets allowed. Rating: 5.0/5.0 (4 reviews). Airbnb: airbnb.com/h/drangstuga

Both houses can be booked together (up to 14 guests): airbnb.com/h/kringelgarden-all

The forest around both properties has been managed by the operator's family for over 100 years with a focus on recreation rather than timber production — giving it exceptional character for forest bathing.

---

## Structural model

**Inspiration:** Canopy & Stars (canopyandstars.co.uk) — editorial voice, curated listings, nature immersion as core value, trust built through editorial integrity rather than aggregation.

**Site structure:**
1. **Editorial hub** — What is forest bathing? The science. How to do it. Seasonal guides. Forest bathing in Sweden.
2. **"Good places" directory** — Curated forest bathing locations in Sweden (editorial, not booking engine), with Blekinge as the anchor region.
3. **Accommodation listings** — Initially Kringelgården and Drängstugan. Expandable to other operators.
4. **About** — The story behind the site and the properties.

**Monetisation (initial):** Accommodation bookings via Airbnb link-outs. No OTA dependency required — direct booking possibility to be evaluated later.

---

## Tech stack

- **Framework:** Next.js 15 (App Router) with TypeScript
- **CMS:** Payload CMS — self-hosted, both operator and agent can edit content; excellent i18n support
- **Styling:** Tailwind CSS + shadcn/ui — clean, modern, professional
- **i18n:** next-intl for routing and translations; Payload CMS for multilingual content fields
- **Database:** PostgreSQL via Coolify (required by Payload CMS)
- **Deployment:** Coolify on the operator's VPS; domain waldenbad.se

**Rationale:** Payload CMS is the right choice because: (a) the operator needs to edit content without touching code, (b) multilingual content management is a first-class feature, (c) it's self-hosted so there are no SaaS costs, (d) it integrates cleanly with Next.js. See decisions.md for the full decision record.

---

## Phases

### Phase 1: Research & Planning ✅ COMPLETE
**Goal:** Understand the concept, competitive landscape, and target markets. Produce the masterplan.
**Agent works autonomously throughout.**
**Deliverables:** This masterplan. Assignment queue. Project scaffold on GitHub.

---

### Phase 2: Design & Architecture
**Goal:** Establish the visual direction and technical foundation before any content is built.

**Key deliverables:**
- Coolify service provisioned (Next.js app + PostgreSQL)
- Payload CMS installed and running locally
- Design system defined: typography, colour palette, spacing, component library
- Wireframes for key pages: homepage, article page, listing page, directory page
- i18n routing structure decided and implemented

**Operator touchpoint:** Agent presents design direction (colour palette, typography, example component screenshots via Playwright). Operator approves or redirects before Phase 3 begins.

**Operator input needed:**
- Provide forest/property photos (upload to a shared location — agent will advise where)
- Confirm any visual preferences or hard constraints

---

### Phase 3: Content & Core Build
**Goal:** Build the full site with placeholder content, all pages functional in English.

**Key deliverables:**
- Homepage: hero with forest imagery, concept intro, link to editorial and listings
- "What is forest bathing?" — core science/concept article
- "Forest bathing in Sweden" — editorial with Swedish framing (friluftsliv, allemansrätten)
- "Good places for forest bathing in Sweden" — initial listing with Blekinge featured
- Kringelgården property page
- Drängstugan property page
- About page
- All pages responsive, accessible, production-quality

**Agent works autonomously throughout.**

---

### Phase 4: Multilingual Content
**Goal:** Full site in all 5 languages.

**Key deliverables:**
- All editorial content translated: EN → DE, SV, DA, NL
- Translation approach: agent drafts all translations using Claude API; operator reviews German and Swedish (native knowledge), Danish and Dutch (operator to confirm review capacity or accept agent translation)
- Payload CMS configured for 5-language content management
- Language switcher in UI
- hreflang tags for SEO

**Operator touchpoint:** Operator reviews translated content, particularly German and Swedish. Agent flags any passages where cultural nuance may be lost in translation.

---

### Phase 5: SEO & Launch Preparation
**Goal:** Site is production-ready and discoverable.

**Key deliverables:**
- On-page SEO for all target keywords per language
- Meta tags, structured data (schema.org for accommodation listings, articles)
- Sitemap and robots.txt
- Performance optimisation (Core Web Vitals)
- Staging deployment verified with Playwright
- Operator DNS cutover instructions prepared

**Operator touchpoint:** Operator reviews staged site before go-live. Agent sends ntfy notification when staging is ready for review.

**Operator action required:** DNS cutover (point waldenbad.se to Coolify server).

---

### Phase 6: Post-Launch & Marketing
**Goal:** Site is live and beginning to attract organic traffic.

**Key deliverables:**
- Google Search Console and analytics set up
- Initial outreach content: Visit Blekinge contact, 2-3 German travel blogger pitches
- First blog article written and published (e.g. "Why Blekinge's forest is perfect for forest bathing")
- Social media presence established (Instagram at minimum)
- Airbnb listings updated with waldenbad.se link

**Agent works autonomously on content and outreach preparation. Operator approves any external communications before they go out.**

---

### Phase 7: Growth (ongoing)
**Goal:** Expand the directory, grow traffic, evaluate direct booking.

**Key deliverables:**
- Additional forest bathing locations added to the directory (agent researches and proposes; operator approves)
- Additional blog content (seasonal guides, forest species, activity ideas)
- Evaluate adding more accommodation listings from other operators
- Evaluate direct booking (vs. Airbnb link-out) based on traffic and conversion data

**Agent proposes assignments; operator prioritises.**

---

## Operator involvement summary

| Phase | Operator action required |
|-------|--------------------------|
| Phase 2 (Design) | Approve visual direction; provide forest/property photos |
| Phase 4 (i18n) | Review German and Swedish translations |
| Phase 5 (Launch prep) | Review staged site; perform DNS cutover |
| Phase 6 (Marketing) | Approve outreach communications before sending |
| Phase 7 (Growth) | Prioritise expansion assignments |

Between these touchpoints, the agent works autonomously and communicates via the blocker/ntfy system only when genuinely blocked.

---

## Current Status

Phase 1 complete. Phase 2 begins with the first assignment in the queue.

---

## Key decisions

See `.agent/decisions.md` for full records on:
- DR-001: CMS selection (Payload CMS vs. alternatives)
- DR-002: i18n approach (next-intl + Payload)
- DR-003: Accommodation monetisation (Airbnb link-outs vs. direct booking)
