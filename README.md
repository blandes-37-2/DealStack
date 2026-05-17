# DealStack

A purpose-built CRM for commercial real estate investment sales teams. Built from scratch around how brokers actually work — not how generic sales software thinks they should.

## Why DealStack Exists

Off-the-shelf CRMs treat buildings as accounts and deals as opportunities. That abstraction breaks down fast in CRE investment sales. DealStack was designed to fix that:

- **Buildings are first-class objects** with transaction history, leases, ownership, and broker coverage
- **Relationships are cadence-driven** — the Outreach Board surfaces who's overdue, who's due soon, and who's been recently contacted
- **Pipeline is weighted** — active deals at 100%, pursuits at probability-adjusted value, rolled up by quarter and year
- **Email logs itself** — DealBot captures communications via CC, runs them through OpenAI, and links them to the right buildings, contacts, and deals automatically

## What's Inside

| Module | Description |
|---|---|
| **Buildings** | 495 Class A / Trophy office buildings across 8 Florida markets with full transaction and lease history |
| **Contacts & Companies** | 701 companies, 184 contacts, with cadence tracking and deal history |
| **Outreach Board** | Kanban view of your contact outreach — overdue, due soon, recently contacted |
| **Deals** | Active investment sales pipeline with multi-building support and team assignments |
| **Pursuits** | Pre-deal tracking with probability weighting and one-click conversion to deals |
| **Weighted Pipeline** | Revenue forecast combining deals + probability-weighted pursuits across Q1–Q4 |
| **Activities** | 46 logged interactions (calls, meetings, emails, site visits) linked across contacts, buildings, and deals |
| **DealBot** | AI-powered email capture via SendGrid + OpenAI — CC the bot, it handles the rest |
| **Tasks** | Internal to-do tracking, distinct from client-facing activities |
| **Goals** | Pipeline targets, closed deals, and meeting counts tracked per broker |
| **Bulk Upload** | CSV/Excel import with fuzzy duplicate detection and merge conflict resolution |

## Tech Stack

| Layer | Stack |
|---|---|
| Frontend | React 18, TypeScript, Vite, shadcn/ui, Tailwind CSS, TanStack Query |
| Backend | Node.js, Express.js, TypeScript |
| Database | PostgreSQL (Neon serverless), Drizzle ORM |
| Auth | Passport.js, bcrypt, PostgreSQL-backed sessions |
| AI / Email | OpenAI API (gpt-4o-mini), SendGrid Inbound Parse |

## Scale

- 495 buildings tracked across Miami, Fort Lauderdale, Tampa, Orlando, Jacksonville, West Palm Beach, Boca Raton, and Naples
- 212 historical sales transactions
- 325 leases
- 701 companies, 184 contacts
- 6-role permission system (Admin → Viewer)
- Built for teams of 5–20 brokers

## Highlight: DealBot

The most distinctive feature. Brokers CC `dealbot@dealstack-crm.com` on any email or calendar invite. SendGrid forwards it to a webhook, OpenAI extracts entities from the body, and the system fuzzy-matches them against buildings, companies, contacts, and deals — then creates a structured activity record automatically. Handles Microsoft Teams, Google Calendar, and Outlook meeting formats. Deduplicates threads via Message-ID tracking.

## License

MIT © Ben Landes