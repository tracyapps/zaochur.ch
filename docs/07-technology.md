# Technology

> **Status:** Draft v0.1 — for community review, with final confirmation in Phase 0
> **Guiding rule (ETHICS-3):** *boring, honest, open.* Every choice optimizes for: any competent developer could inherit this; any member can leave with their data; no big-tech gatekeeper sits at the door.

This document is written for the whole community, not just builders. Each choice has a "what this means in plain language" note. Final confirmation of all choices happens in Phase 0 with the Care and Build working groups; each choice also has an entry in the [Decision Log](09-decision-log.md).

---

## The shape of the thing

- **A Progressive Web App (PWA)** — a website that installs like an app from a link
- **Borrowed engines for voice/video** — we embed proven open-source, we don't build
- **An open-source backend** we can host where our values point
- **Open code**, in a public repository, documented like we expect to be replaced (kindly)

## The choices

### App: a PWA (Progressive Web App)
- **Plain language:** The Commons is a web page that installs on your phone or laptop from a link — no App Store, no Play Store, no account with Apple or Google, no "your device is too old." Works on anything with a browser; installs in one tap; keeps a home-screen icon and offline doorstep.
- **Why:** the door stays wide (INCLUSION-1); we refuse gatekeepers whose values conflict with ours (ETHICS-5); one codebase means one thing to maintain for a volunteer team (ETHICS-4).

### Frontend framework: React (Next.js)
- **Plain language:** The most widely used way to build web interfaces. "Boring" in the best sense — huge documentation, deep accessibility tooling, and any developer we ever invite to help will already know it.
- **Why:** bus-factor insurance (ETHICS-3/4) — the ecosystem is so large that help is always findable, and AI-assisted tooling knows it deeply. SvelteKit remains an acceptable alternative if the Build group leans that way; the deciding question is "which can a stranger inherit most easily?"

### Backend & database: Supabase (Postgres)
- **Plain language:** An open-source platform giving us accounts/sign-in, the database, real-time updates (who's in a room; new messages), and file storage (art, recordings) — the plumbing every app needs, so we spend our energy on the rooms instead.
- **Why:** open source with a self-host escape hatch (nothing is locked in); accessibility of maintenance for a small team; the Commons Bank's ledger becomes ordinary database tables — exactly what Postgres is for.
- **The honest tension, stated plainly:** Supabase's *cloud* is a US company (PRIVACY-4 concern). Our proposal: run in Supabase's **EU region** while tiny, with member data export discipline from day one and a **written exit plan to self-host on our own EU server** — reviewed at each phase gate. This trade-off is recorded in the Decision Log and revisited honestly.

### Voice & video: LiveKit (with Jitsi as alternative)
- **Plain language:** The engines that carry sound and picture. Open-source, self-hostable, used by serious products — we embed them room by room (Sanctuary services, Living Room hangs, Quiet Room body doubling).
- **Why:** real-time media is specialist work; borrowing it is the boring choice (ETHICS-3). Self-hostable means the streams pass through *our* covenant, not a stranger's.

### Hosting: EU-based servers (proposed: Hetzner)
- **Plain language:** The computers the Commons lives on sit in the European Union, under GDPR — privacy law with teeth — rather than in US jurisdiction. Backups are encrypted and kept in a *second* jurisdiction.
- **Why:** PRIVACY-4 — jurisdiction is a safety decision for this community, decided by the same reasoning that moved our pastors. Final call belongs to Phase 0 with the Care group.

### Email (digests): a values-screened provider
- **Plain language:** The gentle daily/weekly letter is email, because email belongs to no platform. Provider chosen against our vendor covenant (ETHICS-5), minimal recipient data, unsubscribe that actually unsubscribes.

### Migration bridge: Matrix↔Discord bridge (or equivalent)
- **Plain language:** During migration, a doorway carries messages between the old Commons and the new one, so friends on each side still hear each other. It comes down when the last willing person has crossed (INCLUSION-4).

### The games: native web games, ported by their author
- **Plain language:** *doku and draw-tionary already exist as web apps; they're ours, and they come home — running inside the Rec Room with the same spoiler-safe share cards and daily-ritual rhythm described in [What We're Building](05-what-we-are-building.md). The daily community puzzle is a small, well-understood build.

## What we deliberately avoid

- App stores as gatekeepers; "login with Google/Apple/Meta"
- Analytics SDKs, ad tech, engagement tracking — nothing that phones home about people (PRIVACY-1/5)
- Exotic or clever infrastructure that only one person understands (the bus-factor test)
- Building what we can borrow: video engines, calendars plumbing, auth primitives

## Ownership, code, and succession

- **The code lives in the open** (public GitHub repository, `app/` in our workspace is its home). License and repo details: Decision Log.
- **Documentation is a deliverable,** not a chore: a "new developer's first week" guide, runbooks, and a written succession plan for every role (ETHICS-4). If the Commons' builder wins the lottery or needs to rest for a season, the community should experience a shrug, not a crisis.
- **Data belongs to the community:** full export anytime; the exit plan from any vendor is written before we enter.

## The one-sentence version

> A plain, kind web app on open-source bones, living in a jurisdiction that protects us, borrowing the hard parts, owned by the community it shelters.
