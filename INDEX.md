# LIQUID LOCATIONS — INDEX

A production-services / location-scouting business for Spain, aimed at London production companies. In practice: one single-file marketing website plus three business docs. Live at `https://callingjhphoto-cmd.github.io/liquid-locations/`.

## CURRENT STATE
- **DORMANT. Last meaningful edit 5 Aug 2026.** `index.html` (184 KB, 2,546 lines) was edited that day and is **still uncommitted** (`M index.html`, `?? website_review.md`). Everything else in the folder is 23 Mar.
- **Last commit 16 Apr 2026** — `0dce4eb`, *"strip fabricated crew personas + unverified trusted-by entries (Tier-0 fabrication audit)"*. In sync with the remote. Verified in `memory/PROJECT_CURRENCY_AUDIT_2026-08-21.md`.
- **7 Apr 2026 verdict: "Not quite ready to send"** — site live, HTTP 200, 2 blocking + 5 minor issues. Source: `projects/liquid-locations-review.md` (note: sits in `projects/` **root**, not this folder).
- **The business shape (23 Mar 2026):** S.L. structure, three-tier pricing — €450/day scouting, 15–20% crew markup, 20% full service. **48 London outreach drafts sit unsent** in callingjhphoto@gmail.com. Source: `memory/projects/liquid-locations.md`.
- **One catalogued location so far** — Inner Flow, Barcelona (`memory/projects_flat/project_liquid_locations_shoots.md`, 9 Aug).

## WHERE THINGS LIVE
| Path | What's in it |
|---|---|
| `projects/liquid-locations/liquid-locations-review.md` | Site/business review (7 Apr). **Moved 21 Aug 2026 from loose `projects/` root.** |
| `projects/liquid-locations/index.html` | **The entire site** — GSAP animation, 20-location database, quote builder, tax-incentive table |
| `projects/liquid-locations/business_plan.md`, `pricing.md`, `pitch_email.md` | Agent-written business docs (23 Mar) |
| `projects/liquid-locations-review.md` | The newer, more thorough review (7 Apr) — **in `projects/` root** |
| `projects/liquid-locations/website_review.md` | The earlier review (5 Apr), untracked |
| `memory/projects/liquid-locations.md` | The business record — S.L. plan, pricing tiers, the 48 unsent drafts |
| `data/research_raw/gemini_production_service_business_plan.txt` · `gemini_london_spain_production_report.txt` | The source research |

**Repo:** `callingjhphoto-cmd/liquid-locations` · branch `main` · **deploy target:** GitHub Pages

## READ FIRST
1. `memory/projects/liquid-locations.md` — what the business is and what is already drafted.
2. `projects/liquid-locations-review.md` (7 Apr) — the outstanding fix list.
3. `projects/liquid-locations/index.html` — the site itself; everything user-facing is in this one file.

## OPEN
- [ ] **48 London outreach drafts created but never sent.**
- [ ] Review fixes 3–7: decorative EN/ES toggle, **availability calendar hardcoded to April 2026** (now four months stale), gradient hero placeholders, Gmail contact address, GA4/Formspree unconfigured. Items 1–2 (fabricated testimonials, dead client portal) appear addressed by `0dce4eb`, but the 5 Aug `index.html` diff is UNVERIFIED.
- [ ] Register the S.L. — still unchecked.
- [ ] Commit the 5 Aug `index.html`. It exists **only on this Mac**, and the parent repo's GitHub backup has been dead since 10 Aug (644 commits unpushed).

## HARD RULES
- ⛔ **Fabrication is the standing risk on this project.** Commit `0dce4eb` exists purely to strip fabricated crew personas, and the 7 Apr review flags **five invented testimonials naming real companies** (Palma Pictures, Questex). **Never re-add unverified social proof, client logos or crew bios.**
- **Spain's film tax rebate does NOT cover stills** — do not let the tax-incentive table imply otherwise for a stills job.
- **Do-not-contact applies here too:** Steve Evans / Palma Pictures and Falca are on the list.
- **Payment terms 30 days minimum**, never 14/15.

## STALE — superseded, do not answer from these
- ⛔ **The availability calendar inside `index.html` is hardcoded to April 2026.** It reads as live availability and is four months out of date. Fix before sending anyone the link.
- ⛔ `~/.claude-secretary-sync/projects/liquid-locations` — an **empty shell, 0 files**. Not a backup, not a source.
- `projects/liquid-locations/website_review.md` (5 Apr) — superseded by `projects/liquid-locations-review.md` (7 Apr), which is newer and more thorough. Two overlapping review docs is the trap here.
- `business_plan.md`, `pricing.md`, `pitch_email.md` (23 Mar) — never revised since; treat the pricing as a proposal, not a proven rate. The only proven Liquid-side prices are in `projects/liquid/INDEX.md`.
