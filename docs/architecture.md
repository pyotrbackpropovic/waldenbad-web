# Architecture

## Stack

- **Language/Runtime:** Node.js (LTS)
- **Framework:** TBD — see masterplan for decision
- **CMS:** TBD — see masterplan for decision
- **Database:** TBD — PostgreSQL via Coolify if CMS requires it
- **i18n:** 5 languages: English, German, Swedish, Danish, Dutch

## Deployment

- **Platform:** Coolify
- **Domain:** waldenbad.se
- **Coolify service name:** TBD (set during deployment assignment)
- **Production URL:** https://waldenbad.se
- **Branch deployed:** `main`

## Environment Variables

| Variable | Purpose | Where set |
|----------|---------|-----------|
| TBD | | |

Use `.env.example` in the project root as the canonical list of required variables.

## External Services

| Service | Purpose | Auth method |
|---------|---------|-------------|
| Airbnb (read-only) | Source for house listings content | No auth — public pages |

## Key Architectural Decisions

See `.agent/decisions.md` for the full decision log.
