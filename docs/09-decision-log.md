# Decision Log

> **What this is:** Every significant decision, its why (tied to the [Non-Negotiables](02-non-negotiables.md)), and when to revisit it. Power operating in daylight.
> **Format:** one entry per decision, newest last. An entry can be *Proposed*, *Confirmed*, or *Revisited*.

| ID | Status | Decision | Why (non-negotiables cited) | Revisit when |
|----|--------|----------|------------------------------|--------------|
| D001 | Proposed | **Build a custom Commons rather than adopt an existing platform** (Matrix, Mastodon, etc.) — with borrowed engines underneath | INCLUSION-2, ACCESS-3: existing tools force our most vulnerable members to adapt to *them*; the calm-by-default experience we owe this community cannot be retrofitted onto tools built for other bodies. Borrowing (video, auth plumbing) keeps us from rebuilding the world | Phase 0 gate — if the community prefers adopting-then-customizing, this entry reverses honestly |
| D002 | Proposed | **Progressive Web App; no native app-store builds** | INCLUSION-1, ETHICS-5: no gatekeepers at the door; any device with a browser | An accessibility need emerges that only a native app can meet |
| D003 | Proposed | **React/Next.js frontend** (SvelteKit acceptable alternative) | ETHICS-3/4: largest ecosystem = most inheritable by a stranger; best accessibility & AI-assist tooling | Phase 0 Build-group confirmation |
| D004 | Proposed | **Supabase (Postgres) backend in EU region, with a written self-host exit plan** | ETHICS-3 (boring, open-source bones) — *in tension with* PRIVACY-4 (US company); resolved by EU region + export discipline + exit plan reviewed at each phase gate | Each phase gate; immediately if Supabase ownership/policy shifts |
| D005 | Proposed | **Embed LiveKit (or Jitsi) for voice/video; never build our own** | ETHICS-3, ACCESS-1: real-time media is specialist work; self-hostable engines keep streams under our covenant | Phase 3 design |
| D006 | Proposed | **EU hosting (Hetzner) with encrypted backups in a second jurisdiction** | PRIVACY-4, SAFETY-3: jurisdiction as safety decision | Phase 0 confirmation with Care group |
| D007 | Proposed | **Public open-source repository** (license leaning AGPL-3.0 to prevent corporate capture — to be discerned; repo home: `app/` → GitHub) | ETHICS-3: living in the open; "living in the open" is also how we ask for buy-in | Phase 0 |
| D008 | Proposed | **No engagement/attention metrics of any kind; only service metrics** (can people find events, are digests useful) | PRIVACY-5, ETHICS-1: we measure whether the space serves, never who is most watched | Never (this one is a covenant) |
| D009 | Proposed | **Jam sessions → layer-recording ("virtual round"), not real-time audio** | Honesty (ETHICS-6 sibling): latency physics makes real-time jamming impossible; pretending otherwise harms trust. Specialist tools (Jamulus) pointed to, outside our promises | Someone invents anti-latency; until then, never |
| D010 | Proposed | **Games may keep daily scores, attached to the game-day — never to a person's community standing; collective streaks celebrate and never scold** | ETHICS-1/2 in tension with the joy of the games channel; resolved by the "crown the day, not the person" pattern | If games ever produce shame or exclusion in the seasonal review |
| D011 | Proposed | **Discord bridge during migration; Discord stays open until the last willing person crosses** | INCLUSION-4: nobody chooses between friends and tools; no cliff | Gate 2 passes |
| D012 | Proposed | **ZAO Bank ports into the Commons as the Commons Bank, logic-first (WordPress plugin shell stays behind)** | Continuity of discerned design: its safety pattern and abundance economics *are* the platform's constitution in miniature | Gate 1 |
| D013 | Proposed | **Presence is ephemeral: "who's here" is shown now, never stored** | SAFETY-3, PRIVACY-2: we cannot leak what we never kept | Never (retention law) |
| D014 | Proposed | **Naming of the platform itself is a Phase 0 community decision** ("Zao Commons" is the working name; the Discord server already bears it) | The name belongs to the community, like the building | Phase 0 |

---

### How entries change

Anyone may propose a change to a decision; the relevant working group (or the whole community, for covenant-level entries) discerns it; the entry gets a new status line and a dated note explaining what changed and why. We repent in the open, same as we build in the open.

**Change log**
- 2026-10-18 · Log created with D001–D014 (Proposed) — awaiting Phase 0 community discernment.
