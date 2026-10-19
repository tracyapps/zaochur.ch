# Hosting Research — Jurisdiction, Pricing & Stacks

> **Status:** Research snapshot — October 18, 2026 (prices verified against official pages where possible; they change — re-verify before committing)
> **Feeds:** decisions D004 (database), D005 (voice/video), D006 (hosting) in the [Decision Log](09-decision-log.md)
> **Interactive version:** [hosting-comparison.html](hosting-comparison.html) — browse, filter, side-by-side compare, and build stacks like an ecommerce configurator

---

## The one thing that matters most: jurisdiction tiers

"Where are the servers?" is the wrong first question. The right one is **"who can be compelled to hand over what, by whom?"**

The US **CLOUD Act** lets US courts compel *US-incorporated companies* to produce data they control **regardless of where it's stored**. "EU region" on a US platform is real (GDPR applies to EU processing) but partial — the parent can still be served. A German, French, or Singaporean company is outside that *direct* reach; requests must go through slower international channels.

So every option in this research carries a tier:

| Tier | Meaning | Posture |
|---|---|---|
| **A** | EU company, EU servers (Hetzner, OVHcloud, Scaleway, Brevo) | Strongest |
| **B** | Non-US company, EU regions (Supabase — Singapore entity) | Outside direct US reach |
| **C** | US company, EU regions available (Vercel, DO, Neon, LiveKit, most PaaS) | Real but partial |

Per our [Threat Model](03-safety-and-threat-model.md), jurisdiction is defense-in-depth — the stronger protection is that **we never store what we can't afford to leak**. Both together are the plan.

## What the research changed in our assumptions

Three findings corrected or nuanced our planning docs (all now reflected in the Decision Log):

1. **Supabase is not a US company.** Its Terms of Service define the entity as **Supabase Pte. Ltd., Singapore** — outside direct CLOUD Act reach (not an EU company either; GDPR transfers run on SCCs). This *improves* D004's posture beyond what we assumed.
2. **Hetzner raised prices significantly in June 2026** (up to ~3× on some CPX lines; the CX22 went €3.29 → ~€4.49/mo). Still the best price/performance in Tier A — but "dirt cheap Hetzner" lore is slightly stale.
3. **Neon was acquired by Databricks (May 2025)** and its roadmap now serves AI-agent infrastructure. Combined with scale-to-zero pricing (wrong shape for an always-on community), Neon is a weaker fit than Supabase for us despite being a fine database.

Two traps worth remembering: **Supabase's free tier pauses projects after ~1 week of inactivity** (an always-on Commons needs Pro), and **Vercel's Hobby plan is personal/non-commercial only** (an organization runs on Pro, $20/user/mo).

## The field, condensed

Full details, filters, and per-provider pros/cons live in the [interactive tool](hosting-comparison.html). Summary:

### App hosting
| Option | Tier | Entry | @ Zao scale | One-line read |
|---|---|---|---|---|
| Vercel | C | Pro $20/user/mo | $20–35 | Best DX, your wheelhouse; US entity |
| Netlify | C | Pro $19/member/mo | $0–19 | Fine; no edge over Vercel for us |
| Cloudflare Pages/Workers | C | Free → $5/mo | $0–5 | Cheapest credible; CF-specific runtime |
| Railway | C | $5–20/mo + usage | $5–25 | Simple, Docker-friendly; meter creep |
| Render | C | ~$7/mo | $7–25 | Calm middle option; free tier sleeps |
| Fly.io | C | PAYG ~$5.70 VM | $6–20 | Cheap always-on; closer to the metal |
| **Hetzner** | **A** | CX22 ≈ €4.49/mo | $5–25 | The sovereignty pick; you're the sysadmin |
| DigitalOcean | C | $4–24/mo | $6–30 | Your familiarity; US parent |
| OVHcloud | A | VPS-1 ≈ €4.49–6.49 | $5–25 | Tier A alternative; mixed support rep |
| Scaleway | A | from ≈ €4.99 (Stardust €3.28 w/ IPv4) | $4–25 | EU-only regions; Stardust too small for prod |
| Linode (Akamai) | C | from $5/mo | $5–25 | No standout for us |

### Database
| Option | Tier | Entry | @ Zao scale | One-line read |
|---|---|---|---|---|
| **Supabase Cloud (EU region)** | **B** | Pro $25/mo | $25–40 | The spine (auth+pg+realtime+storage); OSS exit path |
| Neon | C | usage ≈ $0.106/compute-hr | $10–45 | Databricks-owned; scale-to-zero wrong shape for 24/7 |
| Self-hosted on VPS | A | €0 incremental | $0–8 | The D004 exit destination; ops-heavy |

### Voice/video
| Option | Tier | Entry | @ Zao scale | One-line read |
|---|---|---|---|---|
| LiveKit Cloud | C | Build $0 (50 GB bw, 5k min) | $0–30 | D005 pick; free tier may cover Phase 3 |
| Self-host LiveKit/Jitsi | A | €5–15/mo server | $5–15 | Endgame; TURN networking is the fiddly part |

### Email (the digest)
| Option | Tier | Entry | One-line read |
|---|---|---|---|
| **Brevo** | **A** | free ~300/day | French company — the values-aligned default |
| Postmark | C | $15/mo 10k | Best deliverability if we ever need the fix |
| Resend | C | free 3k/mo | Lovely DX; 100/day cap pinches on bursts |

## Four stacks worth imagining

The tool presets, spelled out (estimates at Zao scale):

1. **⚡ Fast & familiar — $45–80/mo.** Vercel Pro + Supabase Pro (EU) + LiveKit Cloud + Resend. Lowest ops; you already work this way; US entities carry app + video (mitigate with retention discipline).
2. **⚖️ The middle path (our documented lean) — $30–45/mo.** Hetzner CX (app + self-hosted LiveKit) + Supabase Pro (EU) + Brevo. Tier A hosts the app and calls; Tier B the data; the only US touch is… none, until you look at registrar/DNS.
3. **🏰 EU-sovereign — $15–30/mo.** Hetzner ×2 + self-hosted Supabase OSS/Postgres + self-hosted LiveKit + Brevo. Strongest posture, cheapest cash cost, **highest ops cost** — an honest trade of volunteer hours for sovereignty.
4. **🌱 Leanest sane — $25–40/mo.** Cloudflare free + Supabase Pro + LiveKit Cloud free + Brevo free. About the floor for an always-on Commons without sleeping apps.

## Honest open questions for Phase 0

- **What is ops-time worth?** The cash gap between stacks is ~$15–30/mo — a few volunteer hours. The Care + Build groups should decide the exchange rate between money and rest (ETHICS-4).
- **Registrar & DNS jurisdiction** — unexamined so far; the domain and DNS see metadata. Add to Phase 0 (candidate: an EU registrar).
- **Backups' second jurisdiction** (Threat Model rule): if primary is Hetzner/DE, does OVH/FR or Scaleway/FR fit? Cheap and Tier A.
- **Supabase Team tier ($599/mo)** is the cliff if we ever need SSO/SCIM — note it, hope to outgrow the need slowly.
- **Currency drift:** several costs are €-denominated; budgets in USD should carry ~10% slack.

## Sources

Official pricing pages (linked per provider in the tool) plus: [Hetzner price adjustment notice](https://docs.hetzner.com/general/infrastructure-and-availability/price-adjustment), [Supabase Terms of Service (entity)](https://supabase.com/terms), [Supabase data residency FAQ](https://supabase.com/legal/privacy-resources/data-residency-and-transfers-faq), [Cross-Border Data Forum CLOUD Act FAQ](https://www.crossborderdataforum.org/cloudactfaqs), [Databricks–Neon acquisition coverage](https://itdaily.net/news/business/databricks-acquires-neon), [Northflank hosting comparisons](https://northflank.com/blog/railway-vs-flyio), [OVHcloud 2026 pricing update](https://blog.ovhcloud.com/en/posts/pricing-evolution-of-public-cloud-bare-metal-and-vps-at-ovhcloud), [Scaleway pricing](https://www.scaleway.com/en/pricing), [DigitalOcean droplet pricing](https://www.digitalocean.com/pricing/droplets), [Cloudflare developer platform pricing](https://www.cloudflare.com/plans/developer-platform), [LiveKit pricing](https://livekit.com/pricing).
