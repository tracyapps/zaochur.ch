# Safety & Threat Model

> **Status:** Draft v0.1 — for community review
> **Companion to:** [Non-Negotiables](02-non-negotiables.md) — this document makes "safety" concrete.
> **Note:** This document is written to live in the open: it describes our protections in principle. Operational details (infrastructure specifics, credentials, incident runbooks, caretaker contact chains) live in a separate private repository, because a lock's blueprint is not its key.

Safety that lives in vibes produces either paralysis or false confidence. Safety that lives in a document can be reviewed, improved, and kept. So: what are we protecting, from whom, and what are we honestly able to do about it?

## What we protect

1. **People's identities and locations** — who is queer, trans, undocumented, disabled, organizing, or simply present; where they are; whom they worship with.
2. **What people say** — prayer requests, political speech, grief, joy, confession-adjacent honesty. The texture of a life together.
3. **The community's existence and continuity** — the Commons itself, and its ability to regather if attacked or lost.
4. **Trust** — the felt safety that makes people willing to be real. Once spent, it does not refund easily.

## Who might cause harm, and how

| Adversary | What they'd do | Our honest position |
|---|---|---|
| **Trolls / harassment raids** | Break in via invite links, spam, doxx members, screenshot sensitive posts | **Primary design target.** Defeatable with invite discipline, flag-to-hide, human review, pseudonymity, and minimal retention. |
| **Platforms & data economy** | Profile, scan, monetize, hand over what our community says | **Solved by ownership:** self-run, ad-free, untracked. The reason this project exists. |
| **Legal / government pressure** | Subpoena or seize data; compel disclosure | **Mitigated, not eliminated:** EU jurisdiction, minimal retention, no legal names, no phone numbers. We cannot leak what we never hold. |
| **Insider misuse** | A caretaker or hacked admin account reads what they shouldn't | **Mitigated by design:** least-privilege roles, no admin access to private notes/DMs (a ZAO Bank rule, kept), audit trails, two-person rules for sensitive actions. |
| **Targeted individual attackers** | Attempt one member's account to reach their messages | **Mitigated:** strong auth options (passkeys/TOTP), session controls, anomaly alerts, and visibility controls that limit blast radius. |
| **Nation-state adversary** | Direct sophisticated targeting of an individual member | **Out of scope for the platform to defeat** — and we will say so honestly. Protection there comes from personal OPSEC and pastoral practice (pseudonym culture, careful photo/location norms), which the Commons will teach and make easy, not from our crypto bravado. |

## Design responses (before any code)

- **Collect the minimum.** Retention schedule below is law, not aspiration. Old messages, old presence, old logs: pruned on schedule, automatically.
- **Pseudonyms everywhere.** Chosen names are the only names the system knows.
- **Invite discipline.** New members arrive through invite links that are scoped, revocable, and rate-limited — plus the oldest security system there is: a person who vouches and a human at the front door.
- **Flag-to-hide, humans decide.** (SAFETY-1, inherited from ZAO Bank.) Automated systems reduce exposure; only rested humans decide outcomes; nothing is auto-deleted; the reporter sees what happens next.
- **Compartmentalized visibility.** Rooms, affinity groups, prayer requests, and events each carry their own visibility walls. Being in the Sanctuary says nothing about being in an affinity group.
- **No silent third parties.** No analytics SDKs, no "login with Big Tech," no embedded trackers. The Commons speaks to its members and no one else.
- **Regather-ability.** Full encrypted backups, tested restores, and a published rally point ("if the Commons is unreachable, look for word at ___") so an attack or outage becomes an inconvenience, not an amputation.

## Retention schedule (working draft — to be discerned in Phase 0)

| Data | Kept | Why |
|---|---|---|
| Messages | Until a room's stewards prune; DMs deleted on request | Community memory is a gift; surveillance is not |
| Prayer requests | Until the author removes or resolves them | These are sacred, not archival |
| Presence / "who was online" | Not stored historically at all | Presence is for now |
| Access logs (IP, device) | 30 days, encrypted, caretaker-only | Abuse response only |
| Commons Bank exchanges | Permanent (immutable receipts) | The ledger *is* the point — balances derive from receipts |
| Private notes & DMs | Only as long as participants keep them | Never aggregated, never admin-visible |
| Backups | Rolling encrypted, second jurisdiction | Regather-ability |

**The rule under the table:** every new feature proposal must answer "what does this add to the retention schedule?" — and *not storing something* is always the first option considered.

## If the worst day comes

We will maintain (privately) and rehearse (gently): a compromised-server response, a doxxing response (centering the harmed person's wishes), a legal-demand response, and a "lost caretaker" succession plan. Members will know, in plain language, what happens to their data and the community in each case. **A community that knows its regather plan cannot be scattered by an outage.**

## What this document owes the community

Annual review, in the open, with incidents (anonymized) and near-misses shared. If something in this model proves false, we say so plainly and fix it in the Decision Log.
