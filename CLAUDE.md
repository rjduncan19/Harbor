# Harbor — briefing for Claude Code

Harbor (code name) is a mission-driven product that lets a non-technical "adult child" keep an aging parent's own iPhone or Windows PC safe: locked down against scams and accidental breakage, without turning the device into a "senior device" and without ever spying on the parent.

**Project stage:** design complete enough to start building; no production code yet. Read `docs/` before proposing architecture.

## Non-negotiable product principles

These are hard rules. If a task would violate one, stop and flag it instead of implementing it.

1. **Protect, don't watch (anti-surveillance capability boundary).** Harbor does not have, and will never ship, the ability to read message contents, capture the screen, log keystrokes, log browsing history for review, or track continuous location. Do not build it, even behind a flag — code that doesn't exist can't be enabled, misused, breached, or subpoenaed. This applies equally on Windows, where the platform would allow far more than iOS does.
2. **Locate is on-demand and emergency-only**, never ambient tracking.
3. **Collect the minimum data.** Uncollected data can't leak. Default to not storing anything that isn't needed to protect the device.
4. **Forgiving by design.** Every destructive action in the adult-child experience needs a safety net (confirm, undo, or grace period). The default dashboard state communicates "everything's fine."
5. **Hide the enterprise machinery.** Neither persona ever sees MDM terminology, raw policy matrices, or platform admin consoles.
6. **Support boundary.** Harbor supports the device's configured state (lockouts, over-tight restrictions, threats that slipped through), not general digital literacy. Teaching requests route to community resources.

## Personas

- **Parent** — the device owner. Sees almost nothing of Harbor; keeps their real, aspirational device. Carries both pride and fear (of scams, of losing independence, of being a burden).
- **Adult child** — a well-intentioned, more-technical-than-the-parent caregiver (not necessarily a relative, not necessarily tech-savvy). Pays, and uses a simple, reassuring dashboard.

## Architecture direction

- **MDM engine:** embed an open-source core (Fleet or MicroMDM — not yet chosen) behind a clean internal boundary so it is replaceable. Do not build an engine from scratch; do not build on a commercial MDM API.
- **Real effort goes into:** the enrollment experience and the adult-child dashboard.
- **iOS:** every device is supervised (requires erase + setup; restore from the parent's iCloud backup during Setup Assistant so nothing is lost). Supervision unlocks the deep restriction set.
- **Windows:** more fragmented (assigned access, AppLocker/WDAC, policy). Likely start with a tightly configured standard user + app allow-listing; non-bypassable SmartScreen via policy.
- **Security value comes first from the platforms' own free protective dials turned all the way up**, not paid threat-intel feeds.
- **Platforms in scope:** iOS and Windows. Android is out of scope for now.

## Docs

- `docs/product-principles.md` — principles, positioning, personas
- `docs/architecture.md` — platform lockdown and engine decisions
- `docs/dashboard.md` — adult-child dashboard and app-approval design
- `docs/business.md` — pricing, mission model, validator/endorsement ladder
- `docs/risks.md` — trust-product failure modes to design against
- `docs/open-questions.md` — undecided items

Keep these docs current: when a design decision changes, update the relevant doc in the same change.
